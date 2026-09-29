# Modern Python Project Guide & Structure

## 📁 Recommended Project Layout

Here is a clean, scalable directory structure for a modern Python application:

```text
my_app_project/
├── .gitignore
├── pyproject.toml          # Build system and dependency configuration
├── README.md
├── src/                    # ALL application code lives here
│   └── my_app/
│       ├── __init__.py
│       ├── main.py         # The entry point
│       ├── config.py       # Environment variables and settings
│       ├── auth/           # Feature-based module
│       │   ├── __init__.py
│       │   ├── routes.py
│       │   └── service.py
│       └── payments/       # Feature-based module
│           ├── __init__.py
│           └── service.py
└── tests/                  # Mirrors the src/ directory structure
    ├── test_auth/
    └── test_payments/
```

---

## 🚀 How to Set Up a Modern Python Project

### 1. Initialize the Directory Structure
Create a root directory for your project and a subdirectory for your actual application code. A clean, standard layout looks like this:

```text
my_project/
├── my_app/
│   ├── __init__.py
│   └── main.py
├── tests/
├── .gitignore
└── pyproject.toml
```

---

### 2. Create a Virtual Environment
Using a virtual environment prevents dependency conflicts with your system. Never install project dependencies directly to your global Python environment.

Create an isolated virtual environment inside your project folder:
```bash
python -m venv .venv
```

Activate it:
- **Windows (PowerShell):**
  ```powershell
  .venv\Scripts\Activate.ps1
  ```
- **Windows (Command Prompt):**
  ```cmd
  .venv\Scripts\activate.bat
  ```
- **macOS / Linux:**
  ```bash
  source .venv/bin/activate
  ```

---

### 3. Configure the Build System
Create a `pyproject.toml` file in your root directory. This is the modern standard file (defined by PEP 517/518/621) that replaces older `setup.py` scripts. It tells Python which backend tools to use to package and build your project.

Example `pyproject.toml`:
```toml
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"

[project]
name = "my_app"
version = "0.1.0"
description = "A modern Python project"
readme = "README.md"
requires-python = ">=3.10"
dependencies = []
```

---

### 4. Write and Package
Once your code is written, you use a frontend build tool (like `build` or `poetry`) to bundle your project into a `.whl` (Wheel) or `.tar.gz` (Source Distribution) file, which can then be published to PyPI or deployed.

Example using the `build` tool:
```bash
python -m pip install --upgrade build
python -m build
```
