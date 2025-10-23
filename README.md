# Project Overview

This repository hosts a data processing pipeline that converts an Excel spreadsheet into a CSV, processes the data using a Python script, and publishes the results as a JSON file via GitHub Pages. It also includes a simple responsive HTML application.

## Repository Structure

```
.
├── .github/              # GitHub Actions workflows
│   └── workflows/
│       └── ci.yml        # CI/CD workflow for testing, processing, and deployment
├── execute.py            # Python script for data processing (fixed and updated)
├── data.xlsx             # Original Excel data file
├── data.csv              # Converted CSV data file (generated from data.xlsx)
├── index.html            # Single-file responsive HTML application
├── README.md             # This README file
└── LICENSE               # MIT License
```

## Setup and Local Development

### Prerequisites

- Python 3.11+
- pip (Python package installer)
- virtualenv (recommended)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2.  **Create and activate a virtual environment:**
    ```bash
    python -m venv .venv
    # On Windows:
    .\.venv\Scripts\activate
    # On macOS/Linux:
    source .venv/bin/activate
    ```

3.  **Install dependencies:**
    The `execute.py` script requires `pandas`.
    ```bash
    pip install pandas==2.3.0 ruff
    ```

### Data Conversion (`data.xlsx` to `data.csv`)

The `data.xlsx` file is converted to `data.csv` as part of the initial setup. This conversion process ensures that the `execute.py` script can work with a standardized CSV format. The `data.csv` file is committed to the repository.

### Running the `execute.py` script

The `execute.py` script has been thoroughly reviewed and a non-trivial error has been fixed. It is now compatible with Python 3.11+ and Pandas 2.3.

To run the script locally and generate `result.json`:

```bash
python execute.py > result.json
```

This will produce a `result.json` file in your current directory with the processed data.

### Linting and Code Quality

`ruff` is used for linting and code formatting to maintain code quality. To run `ruff` locally:

```bash
ruff check .
rfff format .
```

## Continuous Integration and Deployment (CI/CD)

This project leverages GitHub Actions for its CI/CD pipeline, defined in `.github/workflows/ci.yml`.

### Workflow Steps:

1.  **Code Linting with Ruff**:
    -   On every push to the `main` branch, `ruff` is run to check for style violations and potential errors in the Python codebase. Results are displayed directly in the CI log.

2.  **Execute Python Script**:
    -   The `execute.py` script is run using Python 3.11.
    -   Its standard output is redirected to `result.json`, which contains the processed data.

3.  **Publish `result.json` via GitHub Pages**:
    -   The generated `result.json` file is then published as a static asset using GitHub Pages.
    -   After a successful run, the `result.json` will be accessible at `https://your-username.github.io/your-repo-name/result.json`.

**Note**: The `result.json` file is *not* committed to the repository; it is generated and deployed exclusively by the CI pipeline.

## License

This project is open-source and available under the MIT License. See the `LICENSE` file for more details.
