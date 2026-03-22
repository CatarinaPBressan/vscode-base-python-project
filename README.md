# VSCode Base Python Project Template

This is a template repository for Python projects with sensible defaults for VSCode development. It includes configuration for testing, linting, formatting, and debugging.

## Features

- **Project Structure**: Organized package structure with tests
- **Dependencies**: Managed with Poetry (pyproject.toml)
- **Testing**: Pytest configured with VSCode integration
- **Linting**: Flake8 for code quality
- **Formatting**: Black and isort for consistent code style
- **Debugging**: VSCode launch configurations for debugging

## Getting Started

### 1. Clone or Download the Template

```bash
git clone https://github.com/yourusername/vscode-base-python-project.git your-new-project
cd your-new-project
```

### 2. Install Poetry

If you haven't already, install Poetry: [Installation Instructions](https://python-poetry.org/docs/#installation)

### 3. Set Up the Python Environment

Poetry will automatically create and manage a virtual environment for you.

```bash
poetry install
```

This installs the project dependencies and development dependencies, and creates a virtual environment if one doesn't exist.

### 4. Update Project Configuration

#### Update pyproject.toml

Edit `pyproject.toml` to customize your project:

- Change the `name` field to your project name
- Update `version`, `description`, and `authors`
- Modify dependencies as needed

Example:

```toml
[project]
name = "my-awesome-project"
version = "0.1.0"
description = "My awesome Python project"
```

#### Rename the Package Directory

The default package directory is named `package`. Rename it to match your project name:

```bash
mv package your_project_name
```

Update any imports in your code accordingly.

#### Update VSCode Settings

Edit `.vscode/settings.json` to update the pytest path:

```json
{
  "python.testing.pytestArgs": ["your_project_name/tests/"]
}
```

#### Update Launch Configuration

Edit `.vscode/launch.json` to add a project-specific debug configuration. Replace the existing configuration with:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Run Main Module",
      "type": "debugpy",
      "request": "launch",
      "module": "your_project_name.your_main_module",
      "console": "integratedTerminal"
    },
    {
      "name": "Python: Current File",
      "type": "debugpy",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal"
    }
  ]
}
```

Replace `your_project_name.your_main_module` with the appropriate module path (e.g., `your_project_name.main`).

### 5. Run Tests

```bash
pytest
```

Or use VSCode's test runner (Ctrl+Shift+P > "Python: Run All Tests").

### 6. Start Developing

- Open the project in VSCode
- Code will be automatically formatted on save
- Use the debug configurations to run/debug your code
- Run tests from the Testing panel

## Project Structure

```
your-project/
├── pyproject.toml          # Project configuration and dependencies
├── README.md              # This file
├── your_project_name/     # Main package directory
│   ├── __init__.py
│   ├── main.py           # Example main module
│   └── tests/            # Test directory
│       ├── __init__.py
│       └── test_main.py
└── .vscode/               # VSCode configuration
    ├── settings.json     # Editor and testing settings
    ├── launch.json       # Debug configurations
    └── extensions.json   # Recommended extensions
```

## Recommended VSCode Extensions

The `.vscode/extensions.json` file includes recommended extensions. Install them for the best development experience:

- Python
- Pylance
- Black Formatter
- Flake8
- isort

## Customization

Feel free to modify the configurations in `.vscode/` and `pyproject.toml` to suit your project's needs. Add or remove dependencies, adjust linting rules, and customize the debug configurations as required.
