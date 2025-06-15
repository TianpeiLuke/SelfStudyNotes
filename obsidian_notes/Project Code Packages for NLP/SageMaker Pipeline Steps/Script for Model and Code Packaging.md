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
WORKING_DIRECTORY = Path("/tmp/mims_packaging_directory")
CODE_DIRECTORY = WORKING_DIRECTORY / "code"
```

### Helper Functions

```python
def ensure_directory(directory: Path):
    """Ensure a directory exists, creating it if necessary."""
    try:
        directory.mkdir(parents=True, exist_ok=True)
        logger.info(f"Directory ensured: {directory}")
        logger.debug(f"Directory permissions: {oct(directory.stat().st_mode)[-3:]}")
        return True
    except Exception as e:
        logger.error(f"Failed to create directory {directory}: {str(e)}", exc_info=True)
        return False
```


```python
def check_file_exists(path: Path, description: str) -> bool:
    """Check if a file exists and log its details."""
    exists = path.exists() and path.is_file()
    try:
        if exists:
            stats = path.stat()
            size_mb = stats.st_size / 1024 / 1024
            logger.info(f"{description}:")
            logger.info(f"  Path: {path}")
            logger.info(f"  Size: {size_mb:.2f}MB")
            logger.info(f"  Permissions: {oct(stats.st_mode)[-3:]}")
            logger.info(f"  Last modified: {stats.st_mtime}")
        else:
            logger.warning(f"{description} not found at {path}")
        return exists
    except Exception as e:
        logger.error(f"Error checking file {path}: {str(e)}", exc_info=True)
        return False
```


```python
def list_directory_contents(path: Path, description: str):
    """List and log the contents of a directory."""
    logger.info(f"\n{'='*20} Contents of {description} {'='*20}")
    logger.info(f"Path: {path}")
    
    if not path.exists():
        logger.warning(f"Directory does not exist: {path}")
        return
    
    if not path.is_dir():
        logger.warning(f"Path exists but is not a directory: {path}")
        return
    
    try:
        total_size = 0
        file_count = 0
        dir_count = 0
        
        logger.info("\nDetailed contents:")
        for item in path.rglob("*"):
            indent = "  " * len(item.relative_to(path).parts)
            try:
                if item.is_file():
                    size_mb = item.stat().st_size / 1024 / 1024
                    total_size += size_mb
                    file_count += 1
                    logger.info(f"{indent}📄 {item.name} ({size_mb:.2f}MB)")
                elif item.is_dir():
                    dir_count += 1
                    logger.info(f"{indent}📁 {item.name}/")
            except Exception as e:
                logger.error(f"Error accessing {item}: {str(e)}")
        
        logger.info(f"\nSummary for {description}:")
        logger.info(f"  Total files: {file_count}")
        logger.info(f"  Total directories: {dir_count}")
        logger.info(f"  Total size: {total_size:.2f}MB")
        
    except Exception as e:
        logger.error(f"Error listing directory contents for {path}: {str(e)}", exc_info=True)
```

### Copy Functions

```python
def copy_file_robust(src: Path, dst: Path):
    """Copy a file and log the operation, ensuring destination directory exists."""
    logger.info(f"\nAttempting to copy file:")
    logger.info(f"  From: {src}")
    logger.info(f"  To: {dst}")
    
    if not check_file_exists(src, "Source file for copy"):
        logger.warning("Source file does not exist or is not a file. Skipping copy.")
        return False
    
    try:
        ensure_directory(dst.parent)
        shutil.copy2(src, dst)
        if check_file_exists(dst, "Destination file after copy"):
            logger.info("File copied successfully")
            return True
        else:
            logger.error("Failed to verify copied file")
            return False
    except Exception as e:
        logger.error(f"Error copying file: {str(e)}", exc_info=True)
        return False
```

```python
def copy_scripts(src_dir: Path, dst_dir: Path):
    """Recursively copy scripts from source to destination."""
    logger.info(f"\n{'='*20} Copying Scripts {'='*20}")
    logger.info(f"From: {src_dir}")
    logger.info(f"To: {dst_dir}")
    
    list_directory_contents(src_dir, "Source scripts directory")

    if not src_dir.exists() or not src_dir.is_dir():
        logger.warning("Source scripts directory does not exist or is not a directory. Skipping script copy.")
        return

    ensure_directory(dst_dir)
    
    files_copied = 0
    total_size_mb = 0
    
    for item in src_dir.rglob('*'):
        if item.is_file():
            relative_path = item.relative_to(src_dir)
            destination_file = dst_dir / relative_path
            if copy_file_robust(item, destination_file):
                files_copied += 1
                total_size_mb += destination_file.stat().st_size / 1024 / 1024
    
    logger.info(f"\nScript copying summary:")
    logger.info(f"  Files copied: {files_copied}")
    logger.info(f"  Total size: {total_size_mb:.2f}MB")
    
    list_directory_contents(dst_dir, "Destination scripts directory")
```

### Extract Tar File

```python
def extract_tarfile(tar_path: Path, extract_path: Path):
    """Extract a tar file to the specified path."""
    logger.info(f"\n{'='*20} Extracting Tar File {'='*20}")
    
    if not check_file_exists(tar_path, "Tar file to extract"):
        logger.error("Cannot extract. Tar file does not exist.")
        return
    
    ensure_directory(extract_path)
    
    try:
        with tarfile.open(tar_path, "r:*") as tar:
            logger.info(f"\nTar file contents before extraction:")
            total_size = 0
            for member in tar.getmembers():
                size_mb = member.size / 1024 / 1024
                total_size += size_mb
                logger.info(f"  {member.name} ({size_mb:.2f}MB)")
            logger.info(f"Total size in tar: {total_size:.2f}MB")
            
            logger.info(f"\nExtracting to: {extract_path}")
            tar.extractall(path=extract_path)
            
        logger.info("\nExtraction completed. Verifying extracted contents:")
        list_directory_contents(extract_path, "Extracted contents")
        
    except Exception as e:
        logger.error(f"Error during tar extraction: {str(e)}", exc_info=True)
```

### Create Tar File

```python
def create_tarfile(output_tar_path: Path, source_dir: Path):
    """Create a tar file from the contents of a directory."""
    logger.info(f"\n{'='*20} Creating Tar File {'='*20}")
    logger.info(f"Output tar: {output_tar_path}")
    logger.info(f"Source directory: {source_dir}")
    
    ensure_directory(output_tar_path.parent)
    
    try:
        total_size = 0
        files_added = 0
        
        with tarfile.open(output_tar_path, "w:gz") as tar:
            for item in source_dir.rglob("*"):
                if item.is_file():
                    arcname = item.relative_to(source_dir)
                    size_mb = item.stat().st_size / 1024 / 1024
                    total_size += size_mb
                    files_added += 1
                    logger.info(f"Adding to tar: {arcname} ({size_mb:.2f}MB)")
                    tar.add(item, arcname=arcname)
        
        logger.info(f"\nTar creation summary:")
        logger.info(f"  Files added: {files_added}")
        logger.info(f"  Total uncompressed size: {total_size:.2f}MB")
        
        if check_file_exists(output_tar_path, "Created tar file"):
            compressed_size = output_tar_path.stat().st_size / 1024 / 1024
            logger.info(f"  Compressed tar size: {compressed_size:.2f}MB")
            logger.info(f"  Compression ratio: {compressed_size/total_size:.2%}")
        
    except Exception as e:
        logger.error(f"Error creating tar file: {str(e)}", exc_info=True)
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
    logger.info(f"Python version: {sys.version}")
    logger.info(f"Working directory: {os.getcwd()}")
    logger.info(f"Available disk space: {shutil.disk_usage('/').free / (1024*1024*1024):.2f}GB")

    # Ensure working and output directories exist
    ensure_directory(WORKING_DIRECTORY)
    ensure_directory(OUTPUT_PATH)

    # Extract input model.tar.gz if it exists
    input_model_tar = MODEL_PATH / "model.tar.gz"
    logger.info("\nChecking for input model.tar.gz...")
    
    if check_file_exists(input_model_tar, "Input model.tar.gz"):
        extract_tarfile(input_model_tar, WORKING_DIRECTORY)
    else:
        logger.info("No model.tar.gz found. Copying all files from MODEL_PATH...")
        files_copied = 0
        total_size = 0
        for item in MODEL_PATH.rglob("*"):
            if item.is_file():
                dest_path = WORKING_DIRECTORY / item.relative_to(MODEL_PATH)
                if copy_file_robust(item, dest_path):
                    files_copied += 1
                    total_size += item.stat().st_size / 1024 / 1024
        logger.info(f"\nCopied {files_copied} files, total size: {total_size:.2f}MB")

    # Copy inference scripts to WORKING_DIRECTORY/code
    copy_scripts(SCRIPT_PATH, CODE_DIRECTORY)

    # Create the output model.tar.gz
    output_tar_file = OUTPUT_PATH / "model.tar.gz"
    create_tarfile(output_tar_file, WORKING_DIRECTORY)

    # Final verification and summary
    logger.info("\n=== Final State and Summary ===")
    list_directory_contents(WORKING_DIRECTORY, "Working directory final content")
    list_directory_contents(OUTPUT_PATH, "Output directory final content")

    logger.info("\n=== MIMS packaging completed successfully ===")
```

#### Main Entry

```python
if __name__ == "__main__":
    try:
        main()
    except Exception as e:
        logger.error(f"An unexpected error occurred during packaging: {str(e)}", exc_info=True)
        logger.error("Detailed traceback:", exc_info=True)
        raise
```



-----------
##  Recommended Notes

- [[Pipeline for MODS Deep Learning training]]

- [[AtoZ BSM MODS script]]
- [[Inference Handler AtoZ BSM]]
- [[MIMS Packaging for XGB Model]]

- [[Register SageMaker Model]]