---
tags:
  - code
  - code_snippet
  - python/aws_python_sdk
  - aws/sagemaker
keywords: 
topics: 
language: python
date of note: 2024-12-27
---

## Code Snippet Summary

>[!important]
>The MIMS Packaging Script
>- Extracts a `model.tar.gz` file from the input model path
>- Copies two model-related files:
>     - `model.pth` (the main model file)
>     - `model_artifacts.pth` (associated model artifacts)
>     - `model.onnx` (ONNX file)
>- Copies scripts to the code directory using the `copy_scripts` function
>- Creates a new compressed tar file (`model.tar.gz`) in the output path containing:
>     - The model file
>     - The model artifacts file
>     - The code directory and its contents

- [[AtoZ BSM MODS script]]
- [[Export to ONNX and Inference]]

## Code

```python
import shutil
import tarfile
from pathlib import Path

import os
from typing import List, Dict, Optional # If you use Dict or Optional elsewhere for type hinting
```

```python
import logging
# Configure logging
logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(levelname)s - %(message)s')
logger = logging.getLogger(__name__)
```

### Constants

```python
# Constants
MODEL_PATH = Path("/opt/ml/processing/input/model")
SCRIPT_PATH = Path("/opt/ml/processing/input/script")
OUTPUT_PATH = Path("/opt/ml/processing/output")
WORKING_DIRECTORY = Path("/tmp/mims_packaging_directory") # Using /tmp for broader compatibility
CODE_DIRECTORY = WORKING_DIRECTORY / "code"
MODEL_FILE = "model.pth"  # Expected PyTorch model file
MODEL_ARTIFACT_FILE = "model_artifacts.pth" # Additional artifacts (e.g., tokenizer, config)
ONNX_MODEL_FILE = "model.onnx" # Standard name for ONNX model file
```

### Helper Functions

```python
def ensure_directory(directory: Path):
    """Ensure a directory exists, creating it if necessary."""
    directory.mkdir(parents=True, exist_ok=True)
    logger.info(f"Ensured directory exists: {directory}")
```


```python
def check_file_exists(path: Path, description: str) -> bool:
    """Check if a file exists and log its details."""
    exists = path.exists() and path.is_file() # Ensure it's a file
    size_mb = 0
    if exists:
        try:
            size_mb = path.stat().st_size / 1024 / 1024
        except FileNotFoundError: # Race condition if file is deleted between exists() and stat()
            exists = False
            
    logger.info(
        f"{description}: "
        f"Path='{path}', "
        f"Exists={exists}, "
        f"Size={size_mb:.2f}MB"
    )
    return exists
```


```python
def list_directory_contents(path: Path, description: str):
    """List and log the contents of a directory."""
    logger.info(f"\nContents of {description} ('{path}'):")
    if path.exists() and path.is_dir():
        if not any(path.iterdir()): # Check if directory is empty
            logger.info("  (Directory is empty)")
            return
        for item in path.rglob("*"):
            if item.is_file():
                size_mb = 0
                try:
                    size_mb = item.stat().st_size / 1024 / 1024
                except FileNotFoundError:
                    pass # File might have been deleted, log as 0MB or skip
                logger.info(f"  {item.relative_to(path)} ({size_mb:.2f}MB)")
            elif item.is_dir() and not any(item.iterdir()): # Log empty subdirectories
                 logger.info(f"  {item.relative_to(path)}/ (empty directory)")
    elif path.exists() and not path.is_dir():
        logger.warning(f"Path is not a directory: {path}")
    else:
        logger.warning(f"Directory does not exist: {path}")
```

### Copy Functions

```python
def copy_file_robust(src: Path, dst: Path):
    """Copy a file and log the operation, ensuring destination directory exists."""
    if not check_file_exists(src, "Source file for copy"):
        logger.warning(f"Source file {src} does not exist or is not a file. Skipping copy.")
        return False
    try:
        ensure_directory(dst.parent) # Ensure destination directory exists
        shutil.copy2(src, dst) # copy2 preserves more metadata
        if check_file_exists(dst, "Destination file after copy"):
            logger.info(f"Copied '{src}' to '{dst}'")
            return True
        else:
            logger.error(f"Failed to verify copy of '{src}' to '{dst}'")
            return False
    except Exception as e:
        logger.error(f"Error copying file from '{src}' to '{dst}': {e}", exc_info=True)
        return False
```

```python
def copy_scripts(src_dir: Path, dst_dir: Path):
    """Recursively copy scripts from source to destination."""
    logger.info(f"\nCopying scripts from '{src_dir}' to '{dst_dir}'")
    list_directory_contents(src_dir, "Source scripts directory")

    if not src_dir.exists() or not src_dir.is_dir():
        logger.warning(f"Source scripts directory '{src_dir}' does not exist. Skipping script copy.")
        return

    ensure_directory(dst_dir) # Ensure the root 'code' directory exists

    copied_any = False
    for item in src_dir.rglob('*'): # rglob handles recursive
        if item.is_file():
            relative_path = item.relative_to(src_dir)
            destination_file = dst_dir / relative_path
            ensure_directory(destination_file.parent) # Ensure sub-directory structure is created
            if copy_file_robust(item, destination_file):
                copied_any = True
    
    if copied_any:
        list_directory_contents(dst_dir, "Destination scripts directory ('code')")
    else:
        logger.info(f"No files found to copy from '{src_dir}' or copy failed for all files.")
```

### Extract Tar File

```python
def extract_tarfile(tar_path: Path, extract_path: Path):
    """Extract a tar file to the specified path."""
    logger.info(f"\nExtracting tar file:")
    if not check_file_exists(tar_path, "Tar file to extract"):
        logger.error(f"Cannot extract. Tar file does not exist: {tar_path}")
        return

    ensure_directory(extract_path)
    with tarfile.open(tar_path, "r:*") as tar: # "r:*" auto-detects compression (gz, bz2, etc.)
        logger.info(f"Extracting '{tar_path}' to '{extract_path}'...")
        logger.info("Tar file contents:")
        for member in tar.getmembers():
            member_size_mb = member.size / 1024 / 1024
            logger.info(f"  {member.name} ({member_size_mb:.2f}MB)")
        tar.extractall(path=extract_path)

    list_directory_contents(extract_path, f"Extracted contents in '{extract_path}'")

```

### Create Tar File

```python
def create_tarfile(output_tar_path: Path, base_dir_to_tar_from: Path, items_to_include: List[Path]):
    """
    Create a tar file with the given items, preserving their paths relative to a base directory.
    Items should be paths relative to base_dir_to_tar_from, or absolute paths that are children of it.
    """
    logger.info(f"\nCreating tar file at '{output_tar_path}' from base '{base_dir_to_tar_from}'")
    ensure_directory(output_tar_path.parent)

    with tarfile.open(output_tar_path, "w:gz") as tar:
        for item_path_in_working_dir in items_to_include:
            if not item_path_in_working_dir.exists():
                logger.warning(f"Item '{item_path_in_working_dir}' does not exist. Skipping from tar.")
                continue

            # arcname is the name it will have inside the tar file.
            # We want paths relative to the WORKING_DIRECTORY to be at the root of the tar.
            # For files directly in WORKING_DIRECTORY, arcname = item.name
            # For directories (like CODE_DIRECTORY), arcname = directory.name (e.g., "code")
            try:
                arcname = item_path_in_working_dir.relative_to(base_dir_to_tar_from).as_posix()
            except ValueError: # If item_path_in_working_dir is not relative to base_dir_to_tar_from (should not happen with current logic)
                arcname = item_path_in_working_dir.name # Fallback to just the item name
                logger.warning(f"Item '{item_path_in_working_dir}' not relative to base '{base_dir_to_tar_from}'. Using arcname: '{arcname}'")
            
            logger.info(f"Adding to tar: '{item_path_in_working_dir}' as '{arcname}'")
            tar.add(item_path_in_working_dir, arcname=arcname)

    check_file_exists(output_tar_path, "Created tar file")
```

### Main

- Step 1: Extract input `model.tar.gz` (if it exists) 
- Step 2: Prepare items for the output `model.tar.gz`
	- Helper to conditionally copy files from `MODEL_PATH` to `WORKING_DIRECTORY`
	- Conditionally copy `model.pth`, `model_artifacts.pth`, and `model.onnx`
- Step 3: Copy inference scripts to `WORKING_DIRECTORY/code`
- Step 4: Create the output `model.tar.gz`
	- All paths in `items_for_output_tar` are now absolute paths to files/dirs within `WORKING_DIRECTORY`
	- We want them to be at the root of the tarball, or 'code/' for the scripts.
- Step 5: Final verification
	- Optionally, list contents of the created tar for verification
	- Optional: Clean up working directory


```python
def main():
    logger.info("\n=== Starting MIMS packaging process ===")

    # Log initial directory states
    logger.info("\n--- Initial directory state ---")
    list_directory_contents(MODEL_PATH, "Model input directory (/opt/ml/processing/input/model)")
    list_directory_contents(SCRIPT_PATH, "Script input directory (/opt/ml/processing/input/script)")
    list_directory_contents(OUTPUT_PATH, "Output directory (/opt/ml/processing/output)")

    # Ensure working and output directories exist
    ensure_directory(WORKING_DIRECTORY)
    ensure_directory(CODE_DIRECTORY) # This is WORKING_DIRECTORY / "code"
    ensure_directory(OUTPUT_PATH)

    # --- Step 1: Extract input model.tar.gz (if it exists) ---
    input_model_tar = MODEL_PATH / "model.tar.gz"
    if check_file_exists(input_model_tar, "Input model.tar.gz from /opt/ml/processing/input/model"):
        extract_tarfile(input_model_tar, MODEL_PATH) # Extract contents into MODEL_PATH itself
                                                    # This means files like model.pth, model.onnx (if in tar)
                                                    # will now be at MODEL_PATH/model.pth, MODEL_PATH/model.onnx
    else:
        logger.warning(f"Input model.tar.gz not found at '{input_model_tar}'. Any required model files must be directly in '{MODEL_PATH}'.")

    # --- Step 2: Prepare items for the output model.tar.gz ---
    logger.info(f"\n--- Preparing items for output tar in working directory: {WORKING_DIRECTORY} ---")
    items_for_output_tar = []

    # Helper to conditionally copy files from MODEL_PATH to WORKING_DIRECTORY
    def try_copy_to_working_dir(filename: str, source_dir: Path, work_dir: Path, tar_list: List[Path]):
        source_file = source_dir / filename
        if check_file_exists(source_file, f"Checking for '{filename}' in '{source_dir}'"):
            dest_file = work_dir / filename
            if copy_file_robust(source_file, dest_file):
                tar_list.append(dest_file) # Add path within working directory
        else:
            logger.info(f"'{filename}' not found in '{source_dir}', will not be included.")

    # Conditionally copy model.pth, model_artifacts.pth, and model.onnx
    try_copy_to_working_dir(MODEL_FILE, MODEL_PATH, WORKING_DIRECTORY, items_for_output_tar)
    try_copy_to_working_dir(MODEL_ARTIFACT_FILE, MODEL_PATH, WORKING_DIRECTORY, items_for_output_tar)
    try_copy_to_working_dir(ONNX_MODEL_FILE, MODEL_PATH, WORKING_DIRECTORY, items_for_output_tar) # Check for ONNX file

    # --- Step 3: Copy inference scripts to WORKING_DIRECTORY/code ---
    copy_scripts(SCRIPT_PATH, CODE_DIRECTORY)
    # Add the 'code' directory (relative to WORKING_DIRECTORY) to the tar list if it's not empty
    if CODE_DIRECTORY.exists() and any(CODE_DIRECTORY.iterdir()):
        items_for_output_tar.append(CODE_DIRECTORY)
        logger.info(f"Directory '{CODE_DIRECTORY.name}' will be included in the output tar.")
    else:
        logger.warning(f"Code directory '{CODE_DIRECTORY}' is empty or does not exist, not adding to tar.")


    # --- Step 4: Create the output model.tar.gz ---
    output_tar_file = OUTPUT_PATH / "model.tar.gz"
    if items_for_output_tar:
        # All paths in items_for_output_tar are now absolute paths to files/dirs within WORKING_DIRECTORY
        # We want them to be at the root of the tarball, or 'code/' for the scripts.
        create_tarfile(output_tar_file, WORKING_DIRECTORY, items_for_output_tar)
    else:
        logger.warning("No items were prepared for packaging. Output model.tar.gz will not be created.")

    # --- Step 5: Final verification ---
    logger.info("\n--- Final state ---")
    list_directory_contents(WORKING_DIRECTORY, "Working directory content before cleanup (optional)")
    list_directory_contents(OUTPUT_PATH, "Output directory")
    if output_tar_file.exists():
        check_file_exists(output_tar_file, "Final output model.tar.gz")
        # Optionally, list contents of the created tar for verification
        # with tarfile.open(output_tar_file, "r:gz") as tar:
        # logger.info(f"Contents of created tar '{output_tar_file}':")
        # for member in tar.getmembers(): logger.info(f"  {member.name}")
    else:
        logger.warning(f"Final output tar file '{output_tar_file}' was not created (likely no items to tar).")


    # Optional: Clean up working directory
    # logger.info(f"Cleaning up working directory: {WORKING_DIRECTORY}")
    # shutil.rmtree(WORKING_DIRECTORY)

    logger.info("\n=== MIMS packaging completed ===")
```

```python
if __name__ == "__main__":
    try:
        main()
    except FileNotFoundError as e:
        logger.error(f"A required file was not found: {str(e)}", exc_info=True)
        raise
    except Exception as e:
        logger.error(f"An unexpected error occurred during packaging: {str(e)}", exc_info=True)
        raise
```



-----------
##  Recommended Notes

- [[Pipeline for MODS Deep Learning training]]

- [[AtoZ BSM MODS script]]
- [[Inference Handler AtoZ BSM]]
- [[MIMS Packaging for XGB Model]]

- [[Register SageMaker Model]]