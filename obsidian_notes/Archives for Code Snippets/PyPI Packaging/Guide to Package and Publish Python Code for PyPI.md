---
tags:
  - code
  - code_snippet
  - python/pip
  - python/twine
  - python/build
keywords:
topics:
language: python
date of note: 2025-08-22
---

## Code Snippet Summary

>[!important]
>Given a code repo (e.g. in Github), wrap it into a package and submit to PyPI

## Introduction: The "Why" of Python Packaging

Packaging is an essential skill that elevates a Python project from a personal script to a shareable, reusable, and professional piece of software.1 For developers, data scientists, and researchers, the ability to package code empowers collaboration, ensures reproducibility, and allows contributions to be distributed to a global community through the Python Package Index (PyPI).2 A well-packaged project is inherently more credible; it signals a commitment to quality and makes the code significantly easier for others to install, use, and integrate into their own work.4

The Python packaging landscape has evolved significantly, moving towards a more standardized and declarative approach. This guide provides a definitive, step-by-step walkthrough of the modern packaging workflow. This process centers on a single configuration file, `pyproject.toml`, which serves as the project's blueprint. From this file, standardized tools are used to create distribution archives and upload them securely to PyPI. The primary tools in this modern workflow are:

- **`pyproject.toml`**: The central, standardized configuration file that declaratively defines all project metadata and build requirements.
    
- **`build`**: A command-line tool that reads `pyproject.toml` and orchestrates the creation of distributable package files.
    
- **`twine`**: A utility for securely uploading the built package files to PyPI.
    

This modern, standards-based approach represents a fundamental improvement over older methods that relied on an executable `setup.py` script. Historically, determining a project's metadata or build dependencies required executing this script, which could introduce arbitrary side effects and security vulnerabilities. It was difficult for tools like `pip` to resolve a project's dependencies without running potentially complex and untrusted code. To address these shortcomings, the Python community introduced a series of Python Enhancement Proposals (PEPs), notably PEP 517, 518, and 621, which established `pyproject.toml` as a static, declarative standard.5 This shift allows tools to read project information without code execution, enabling critical features like build isolation and more reliable dependency resolution. This change has fostered a healthier ecosystem where different build tools can interoperate based on a common, secure standard.4 Understanding this evolution from an imperative to a declarative model is key to appreciating the stability and power of the current packaging process.

This report will guide the user through five major phases, using the `cursus` project from GitHub as a practical example. The journey will cover:

1. **Preparation**: Structuring the project code and creating essential files like a `LICENSE` and `README.md`.
    
2. **Configuration**: Defining the package's identity, dependencies, and metadata in the `pyproject.toml` file.
    
3. **Building**: Generating the standardized distribution archives (wheels and source distributions).
    
4. **Publishing**: Uploading the package to PyPI, using the TestPyPI sandbox for a safe first run.
    
5. **Verification**: Installing and testing the newly published package to confirm its success.
    

By the end of this guide, any developer will have the knowledge and confidence to transform their Python code into a publicly available package, ready for the community to `pip install`.

## Phase 1: Preparing Your Project for Packaging

Before creating any packaging-specific configuration, the project's structure must be organized in a standard, robust manner. A clean and logical layout is the foundation of a high-quality package.

### 1.1. Adopting a Standard Project Structure (The src/ Layout)

A highly recommended best practice for structuring a Python package is the `src/` layout.7 In this pattern, all of the Python source code that is meant to be part of the installable package is placed inside a

`src` directory. This provides a clear separation between the importable package code and other project files like tests, documentation, and configuration.

For the example `cursus` project, the initial structure might look like this:

```
cursus/
├── cursus/
│   ├── __init__.py
│   ├── anova.py
│   ├── data.py
│   └──...
├── tests/
├── README.md
└── requirements.txt
```

To adopt the `src/` layout, a `src` directory is created in the project root, and the main package directory (`cursus`) is moved inside it. The refactored structure becomes:

```
cursus-project/
├── src/
│   └── cursus/
│       ├── __init__.py
│       ├── anova.py
│       ├── data.py
│       └──... (other.py files)
├── tests/
│   └──...
├── README.md
├── LICENSE
└──.gitignore
```

The rationale for this structure is compelling and addresses common development pitfalls 7:

- **Prevents Accidental Imports**: Without a `src/` layout, if the current working directory is the project root, it is possible for Python to accidentally import the local `cursus` directory instead of the version that has been installed into the environment. This can lead to confusing bugs where tests pass locally but fail in other environments because they are running against different code. The `src/` layout forces the package to be properly installed (even in editable mode with `pip install -e.`) before it can be imported for testing, ensuring that the code being tested is the same code that users will have.
    
- **Clear Separation of Concerns**: This layout creates an unambiguous distinction between the code that will be distributed (`src/`) and the auxiliary files used for development and project management (documentation, tests, configuration files in the root). This organization makes the project easier to navigate and maintain.
    

### 1.2. Establishing Essential Project Files

Alongside the source code, several other files are essential for a professional and legally sound package. These should reside in the project's root directory.

#### LICENSE

Every open-source project published on PyPI must have a license.7 Without an explicit license, the code is under exclusive copyright by default, meaning no one else can legally use, modify, or distribute it. A

`LICENSE` file clearly defines the permissions and restrictions for users of the software.

There are many open-source licenses, but they generally fall into two categories:

- **Permissive Licenses**: (e.g., MIT, Apache 2.0, BSD) These place minimal restrictions on how the software can be used, modified, and redistributed. The MIT License is a popular choice for its simplicity and broad compatibility.
    
- **Copyleft Licenses**: (e.g., GNU General Public License - GPL) These require that derivative works also be licensed under the same copyleft terms, ensuring that the software remains open-source.
    

For most projects, the MIT License is an excellent starting point. A file named `LICENSE` should be created in the project root, containing the full text of the chosen license.

#### README.md

The `README.md` file is the public face of the project. Its content will be automatically used as the main description on the package's PyPI page.5 A comprehensive and well-written README is crucial for helping users understand what the package does and how to use it.

A high-quality `README.md` should include:

- A clear and concise summary of the project's purpose.
    
- Installation instructions (e.g., `pip install your-package-name`).
    
- A "Quickstart" or basic usage example to get users started immediately.
    
- A link to the full documentation, if available.
    
- Information on how to contribute to the project.
    
- A mention of the project's license.
    

#### .gitignore

The `.gitignore` file specifies files and directories that the Git version control system should ignore. This is essential for keeping the repository clean and preventing build artifacts, temporary files, and environment-specific directories from being committed. A standard Python `.gitignore` should be created in the project root, including entries for common Python and packaging-related artifacts:

```
# Byte-compiled / optimized / C files
__pycache__/
*.py[cod]
*$py.class

# Virtual environment
.venv/
venv/
ENV/

# Build artifacts
dist/
build/
*.egg-info/
```

With the project structure and essential files in place, the project is now ready for the core configuration step.

## Phase 2: Configuring Your Package with pyproject.toml

The `pyproject.toml` file is the cornerstone of modern Python packaging. It is a unified, declarative configuration file that replaces older, more complex files like `setup.py` and `setup.cfg`. Based on the TOML (Tom's Obvious, Minimal Language) format, it provides a clear and standardized way to define project metadata and build requirements.5

### 2.1. The Central Role of pyproject.toml

Introduced by PEP 518 and later expanded by PEP 621, `pyproject.toml` serves as the single source of truth for packaging tools.5 Its declarative nature allows build frontends (like

`pip` and `build`) to understand a project's requirements without executing arbitrary code, which enhances security and reliability. The file is organized into sections, or "tables," with the most important for packaging being `[build-system]` and `[project]`. A new file named `pyproject.toml` should be created in the project's root directory.

### 2.2. Defining the Build System ([build-system])

The `[build-system]` table tells build tools which _build backend_ to use for creating the package's distribution files.5 A build backend is the library that performs the actual work of packaging the code. While several backends exist (like Hatchling and Flit), this guide will use

`setuptools`, the most established and widely compatible backend.

The standard configuration for `setuptools` is as follows:

```toml
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"
```

The keys in this table have specific meanings:

- `requires`: This is a list of packages that must be installed in an isolated environment for the build to succeed. It must always include the build backend itself.6 Specifying a minimum version, such as
    
    `setuptools>=61.0`, is a crucial best practice, as it ensures that a modern version of `setuptools` with full support for `pyproject.toml` is used.4
    
- `build-backend`: This specifies the exact Python object that the build frontend will invoke to perform the build process.5 For
    
    `setuptools`, this is always `"setuptools.build_meta"`.
    

### 2.3. Describing Your Project Metadata ([project])

The `[project]` table contains all the public metadata about the package that will be displayed on PyPI and used by installation tools. This section is governed by PEP 621 and provides a standardized set of keys for describing the project.5

For the `cursus` project, a complete `[project]` table would be constructed as follows. It is critical to choose a unique `name` for the package on PyPI. A common convention to ensure uniqueness is to append a username or organization name, as done here.10

|Key|Description|Example for `cursus`|Source Reference|
|---|---|---|---|
|`name`|**Required.** The distribution name on PyPI. Must be unique. Can only contain letters, numbers, and `._-`.|`name = "cursus-pkg-tianpeluke"`|5|
|`version`|**Required.** The current version of the package. Should follow Semantic Versioning (`MAJOR.MINOR.PATCH`).|`version = "0.1.0"`|5|
|`description`|A short, one-sentence summary of the package. This appears in search results on PyPI.|`description = "A Python package for causal inference in quasi-experimental settings."`|5|
|`readme`|The path to the file containing the long description, which will be displayed on the PyPI project page.|`readme = "README.md"`|5|
|`requires-python`|The Python versions your package is compatible with. This prevents `pip` from installing it on unsupported versions.|`requires-python = ">=3.8"`|5|
|`license`|Specifies the license. The `text` key can be used for standard licenses, or the `file` key can point to the `LICENSE` file.|`license = { text = "MIT License" }`|5|
|`authors`|A list of authors, including name and email. This is the preferred way to specify authorship.|`authors =`|5|
|`keywords`|A list of keywords to improve discoverability on PyPI.|`keywords = ["causal inference", "statistics", "econometrics", "quasi-experiment"]`|5|
|`classifiers`|A list of trove classifiers from a standard list on PyPI to categorize the project. This is very important for search and filtering.|`classifiers =`|7|
|`urls`|A table of relevant links, such as the project's homepage, documentation, or source code repository.|`[project.urls]<br>Homepage = "https://github.com/TianpeiLuke/cursus"<br>Repository = "https://github.com/TianpeiLuke/cursus"`|5|

### 2.4. Managing Dependencies (dependencies & optional-dependencies)

A package's dependencies are the other Python packages it needs to function. These are declared directly within `pyproject.toml`.

#### Runtime Dependencies

The `dependencies` key holds a list of packages that are required for the core functionality of the project. These are the packages that will be automatically installed by `pip` alongside the project. For the `cursus` package, the dependencies listed in its `requirements.txt` file should be transferred here.

```toml
[project]
#... other metadata
dependencies = [
    "pandas>=1.0",
    "numpy>=1.20",
    "scipy",
    "statsmodels"
]
```

When specifying dependencies for a library, it is important to follow best practices to avoid causing conflicts for end-users 7:

- **List only direct dependencies**: Only list packages that the code directly imports and uses. Transitive dependencies (dependencies of dependencies) will be handled automatically by `pip`.
    
- **Avoid strict version pinning**: Using `"=="` to pin an exact version (e.g., `pandas==1.3.5`) is discouraged in libraries, as it can easily create version conflicts in a user's environment if another package requires a different version of `pandas`.
    
- **Use lower bounds**: Use `>=` to specify the minimum version of a dependency required if the code relies on features introduced in that version.
    
- **Use upper bounds cautiously**: Use `<` to specify an upper bound if there is a known incompatibility with a future major version of a dependency. This should be used sparingly, as it can also lead to installation problems.
    

#### Optional Dependencies

The `[project.optional-dependencies]` table is used to define "extras"—sets of dependencies that are not required for the core functionality but enable additional features.9 This is an excellent way to keep the base installation lightweight. For example, dependencies for plotting, testing, or development can be made optional.


```toml
[project.optional-dependencies]
plotting = ["matplotlib>=3.0"]
dev = ["pytest", "black", "ruff"]
```

Users can then install these optional features as needed. For example, to install the `cursus` package along with its plotting capabilities, a user would run: `pip install cursus-pkg-tianpeluke[plotting]`. To install development dependencies, one would use `pip install.[dev]`.

### 2.5. Creating Command-Line Executables ([project.scripts])

The `[project.scripts]` table provides a powerful way to expose functions from the package as command-line scripts that are automatically added to the user's system `PATH` upon installation.6 This is ideal for creating command-line interface (CLI) tools.

If the `cursus` package had a main function for running an analysis, located for example in a `cursus/cli.py` file and named `main`, it could be configured as follows:


```toml
[project.scripts]
cursus-run = "cursus.cli:main"
```

After a user installs the package, they can simply type `cursus-run` in their terminal to execute the `main` function from the `cursus.cli` module. This provides a clean and professional entry point for users to interact with the package's functionality.

## Phase 3: Building the Distribution Archives

With the project configured, the next step is to build the distribution archives. These are the standardized file formats that are uploaded to PyPI and used by `pip` for installation.

### 3.1. Understanding Distribution Formats: Wheels and Source Distributions (sdist)

There are two primary types of distribution archives in the Python ecosystem, and it is best practice to generate and distribute both.4

- **Wheel (`.whl`)**: A wheel is a pre-built, binary distribution format. It is essentially a ZIP archive containing the package's files in a structure that is ready to be unpacked directly into a user's `site-packages` directory. Because they are pre-built, wheels install very quickly and do not require the end-user to have a build environment (like compilers for C extensions) set up on their machine. For these reasons, the wheel is the preferred distribution format for end-users.
    
- **Source Distribution (`.tar.gz` or sdist)**: A source distribution is a compressed archive (`.tar.gz`) containing the project's source code, the `pyproject.toml` file, and any other files needed to build the package. When a user installs from an sdist, `pip` must first build the package on the user's machine before it can be installed.
    

The modern packaging infrastructure has made building from source more reliable than in the past. When `pip` encounters an sdist, it uses the information in `pyproject.toml` to create a temporary, isolated build environment, installing the necessary build dependencies (like `setuptools`) before running the build.8 This build isolation prevents many common installation failures. However, this process is still slower and more complex than installing a wheel. Providing a wheel is a direct way to improve the installation experience for the vast majority of users by making it faster and less error-prone. Building and publishing both a wheel and an sdist ensures maximum compatibility and provides a robust fallback mechanism for platforms or situations where a wheel is not available.

### 3.2. Generating Archives with `build`

The Python Packaging Authority (PyPA) recommends using the `build` package as the standard, frontend tool for generating distribution archives.4 It is a simple, standalone tool that works with any PEP 517-compliant backend specified in

`pyproject.toml`.

First, the `build` package must be installed into the development environment:


```bash
python3 -m pip install build
```

Once installed, the build process is initiated by running the following command from the project's root directory:


```bash
python3 -m build
```

This command performs the following actions:

1. It reads the `pyproject.toml` file to identify the build backend (`setuptools.build_meta`).
    
2. It creates an isolated virtual environment and installs the required build dependencies (`setuptools>=61.0`).
    
3. It invokes the build backend within this isolated environment to generate both the sdist and the wheel.
    
4. The resulting archive files are placed in a newly created `dist/` directory in the project root.
    

After the command completes, the `dist/` directory will contain two files, for example:

- `cursus_pkg_tianpeluke-0.1.0-py3-none-any.whl` (the wheel)
    
- `cursus-pkg-tianpeluke-0.1.0.tar.gz` (the source distribution)
    

These files are now ready to be uploaded to PyPI.

## Phase 4: Publishing to the Python Package Index

With the distribution archives built, the final step is to publish them, making the package available to the public. This process should always be done first on a test server to ensure everything works as expected before publishing to the official index.

### 4.1. The Sandbox: Using TestPyPI for Practice

PyPI provides a separate, parallel instance called TestPyPI (test.pypi.org) that serves as a sandbox for packaging experiments.12 It is strongly recommended that every developer use TestPyPI for their first upload, and for testing any changes to their packaging process.14 This allows for a full end-to-end test of the build, upload, and installation process without the risk of polluting the official PyPI repository with test packages, broken releases, or placeholder names.

To use TestPyPI, a separate account must be created on its website: [https://test.pypi.org/account/register/](https://test.pypi.org/account/register/). The registration process is similar to the official PyPI site.

### 4.2. Secure Uploads with API Tokens

The modern and secure method for authenticating with PyPI and TestPyPI is through API tokens.12 Using a direct username and password for uploads is deprecated and less secure. API tokens are specific, revocable credentials that can be scoped to a particular project, limiting the potential damage if a token were ever compromised.

To generate an API token for TestPyPI:

1. Log in to the TestPyPI account.
    
2. Navigate to "Account settings" from the user dropdown menu.
    
3. Scroll down to the "API tokens" section and click "Add API token".
    
4. Give the token a name (e.g., "cursus-uploader").
    
5. For the first upload of a new package, the token's scope must be set to "Entire account (all projects)". Once the project has been created on TestPyPI, future tokens can be scoped specifically to that project.
    
6. Click "Add token".
    
7. **Crucially, copy the token value immediately and store it in a secure location (like a password manager). The token will only be displayed once and cannot be retrieved again.** The token will start with `pypi-`.
    

### 4.3. Uploading Your Package with `twine`

The PyPA-recommended tool for securely uploading packages is `twine`. It handles the interaction with PyPI over HTTPS and provides robust authentication mechanisms.13

First, install `twine` into the development environment:

```bash
python3 -m pip install twine
```

To upload the built packages from the `dist/` directory to TestPyPI, run the following command. The `--repository testpypi` flag directs `twine` to the TestPyPI server.

```bash
python3 -m twine upload --repository testpypi dist/*
```

`twine` will then prompt for a username and password for authentication:

- For **Username**, enter the special value `__token__`.12 This tells
    
    `twine` and TestPyPI that authentication is being performed with an API token.
    
- For **Password**, paste the full API token that was generated and saved in the previous step.
    

If the authentication is successful, `twine` will upload the wheel and sdist files. The package will now be live on TestPyPI.

Once the process has been successfully verified on TestPyPI, the same steps can be repeated for the official PyPI repository:

1. Register an account on the official PyPI site: [https://pypi.org/account/register/](https://pypi.org/account/register/).13
    
2. Log in and generate a new API token, following the same procedure as for TestPyPI.
    
3. Run the `twine upload` command again, this time _without_ the `--repository` flag, which defaults to the official PyPI index.
    

Bash

```bash
python3 -m twine upload dist/*
```

When prompted, use `__token__` as the username and the newly generated API token from the official PyPI site as the password. The package is now publicly available to the global Python community.

## Phase 5: Verification and Post-Publication Steps

The final phase is to verify that the package was published correctly and is installable and usable by others. This is the ultimate confirmation of a successful packaging process.

### 5.1. Installing Your Live Package

To accurately simulate a new user's experience, it is essential to perform the installation test in a clean, new virtual environment that does not contain the project's source code or any of its development dependencies.

First, create and activate a new virtual environment:

Bash

```
python3 -m venv test-env
source test-env/bin/activate
```

To install the package from **TestPyPI**, the `--index-url` flag must be used to tell `pip` to look at the test index instead of the official one 12:

Bash

```
python3 -m pip install --index-url https://test.pypi.org/simple/ cursus-pkg-tianpeluke
```

To install the package from the **official PyPI**, the standard `pip install` command is used 10:

Bash

```
python3 -m pip install cursus-pkg-tianpeluke
```

If `pip` successfully downloads and installs the package and its dependencies without errors, the publication was a success.

### 5.2. Testing the Installation

After installation, a quick functional test should be performed to ensure the package is working as expected.

Start a Python interpreter from the command line:

Bash

```bash
python3
```

Inside the interpreter, try to import the package and, if possible, run a simple function from it:

Python

```python
>>> import cursus
>>> # Try to access a function or class from the package
>>> # For example:
>>> # from cursus.data import load_data
>>> # df = load_data('some_dataset')
>>> print(cursus.__doc__)
```

If the import succeeds and basic functionality works, the package is correctly installed. If a command-line script was defined in `pyproject.toml`, exit the interpreter and test it directly in the terminal:

Bash

```
cursus-run --help
```

This confirms that the package's entry points have been correctly registered and are accessible from the system `PATH`.

## Conclusion: Your Role as a Python Publisher

Successfully navigating the journey from raw source code to a publicly available package on PyPI is a significant milestone for any developer. This process transforms a project into a durable, shareable, and professional contribution to the Python ecosystem. The key skills acquired—structuring a project with the `src/` layout, declaratively configuring it with `pyproject.toml`, building standardized distribution archives with `build`, and securely publishing them with `twine`—form the foundation of modern Python development and distribution practices.

With the first package published, developers can explore more advanced topics to further professionalize their workflow and manage the lifecycle of their software.

- **Versioning**: Adopting a disciplined versioning strategy is critical for package maintenance. Semantic Versioning (`MAJOR.MINOR.PATCH`) is the community standard. For each new release, the `version` string in `pyproject.toml` must be incremented before building and publishing. A `MAJOR` version change signals incompatible API changes, `MINOR` adds functionality in a backward-compatible manner, and `PATCH` indicates backward-compatible bug fixes.
    
- **Automated Publishing with CI/CD**: Manually building and uploading packages can be tedious and error-prone. Modern development workflows automate this process using Continuous Integration/Continuous Deployment (CI/CD) services like GitHub Actions. A common pattern is to configure a workflow that automatically builds and publishes the package to PyPI whenever a new release is created on GitHub.15 This can be made even more secure by using PyPI's "trusted publisher" feature, which uses OpenID Connect (OIDC) to grant short-lived, tightly-scoped publishing permissions to the CI/CD job, eliminating the need to store long-lived API tokens as repository secrets.12
    
- **Modern Workflow Tools**: While this guide has focused on the foundational, tool-agnostic components (`build`, `twine`), the Python ecosystem offers several all-in-one workflow management tools that can streamline the entire development lifecycle. Tools like **Hatch**, **Poetry**, and the rapidly emerging **uv** provide unified interfaces for managing virtual environments, resolving and locking dependencies, running tests, building packages, and publishing to PyPI.4 By handling these interconnected tasks, they can significantly reduce cognitive overhead and enforce best practices, making them excellent choices for future projects.
    

By mastering the fundamentals of packaging and embracing these advanced practices, developers can ensure their contributions are robust, maintainable, and easily accessible to the vibrant global community that makes Python a leader in science, technology, and software development.




-----------
##  Recommended Notes

- Example
	- Github Rep https://github.com/TianpeiLuke/cursus/tree/main
	- PyPI site
		- https://pypi.org/project/cursus/