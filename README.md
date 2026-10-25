#M26MAC011-ML02

A machine-learning coursework project organized into configuration, data, model, experiment, evaluation, visualization, testing, and report directories. The repository includes a Python package (`task99`), experiment-run storage under `runs/actual_roll`, and a report directory.
The supplied tree lists directories only; it does not expose the source filenames, exact experiment commands, dataset identity, or report compiler settings. The run and validation commands below are therefore templates—confirm the relevant script names and arguments in `scripts/` before running them.
Table of Contents
Project Structure
Setup
Run Experiments
Validate Results
Reproducibility
Report Compilation
Main Components
Project Structure
```text
M26MAC011-ML02/
├── configs/
├── data/
├── figures/
├── logs/
├── models/
├── results/
├── runs/
│   └── actual_roll/
│       ├── configs/
│       ├── data/
│       ├── figures/
│       ├── logs/
│       ├── models/
│       ├── report/
│       │   └── figures/
│       └── results/
├── scripts/
├── task99/
├── tests/
├── .idea/
├── .pytest_cache/
└── .venv/
```
`.venv/`, `.pytest_cache/`, and `.idea/` are environment or IDE-related directories and generally should not be included in a source-control submission.
Setup
The existing project environment is a Windows virtual environment located at `.venv`. Activate it from the project root using PowerShell:
```powershell
.\.venv\Scripts\Activate.ps1

python --version
python -m pip --version
```
If PowerShell prevents activation, you can invoke the environment's Python directly:
```powershell
.\.venv\Scripts\python.exe --version
```
Install dependencies from the project's dependency file if one is present (for example, `requirements.txt` or `requirements-lock.txt`):
```powershell
python -m pip install -r requirements-lock.txt
```
The directory listing does not show which dependency manifest is present. Check the repository root and use the matching file. If no manifest exists, inspect the project imports and assignment requirements before installing packages manually.
Run Experiments
The experiment scripts are located in `scripts/`. Review the available entry points and their command-line options:
```powershell
Get-ChildItem .\scripts -File
```
If the project provides a unified runner, use its help output to confirm the supported arguments:
```powershell
python .\scripts\run_all.py --help
```
A typical run may write artifacts to `runs/actual_roll`, but the exact command depends on the runner's interface. For example, only if the script supports these options:
```powershell
python .\scripts\run_all.py `
  --root runs/actual_roll `
  --roll-number M26MAC011
```
Replace the example script name and arguments with those actually implemented in the repository. Avoid overwriting a completed run when testing a different configuration; use a separate output directory if the runner supports it.
Validate Results
Run the project's tests from the repository root:
```powershell
python -m pytest -q
```
The test directory is present in the project tree. If imports fail with `ModuleNotFoundError: No module named 'task99'`, confirm that the virtual environment is active and that commands are being executed from the project root.
If the repository includes a result-validation or reproducibility script, inspect its usage first:
```powershell
Get-ChildItem .\scripts -File
```
Then run the appropriate script with the arguments shown by its `--help` output. No validator filename or CLI options can be confirmed from the directory-only tree.
Reproducibility
The repository separates shared project artifacts from a run-specific directory:
`configs/` — project configuration files.
`runs/actual_roll/configs/` — configuration artifacts associated with the recorded run.
`data/` and `runs/actual_roll/data/` — dataset and run-specific data artifacts.
`models/` and `runs/actual_roll/models/` — model artifacts.
`results/` and `runs/actual_roll/results/` — experiment outputs and evaluation results.
`logs/` and `runs/actual_roll/logs/` — run and diagnostic logs.
`figures/` and `runs/actual_roll/figures/` — generated visualizations.
For repeatable results, record the configuration, random seed, package versions, and exact command used. Keep each materially different configuration in a separate run directory when possible.
Before submission, verify that the configuration and report metadata contain the correct student name, roll number (`M26MAC011`), repository URL, and final commit hash, if those fields are required by the assignment.
Report Compilation
The repository contains a top-level `report/` directory and a run-specific report directory:
```text
report/
└── figures/

runs/actual_roll/
└── report/
    └── figures/
```
The directory listing does not reveal the report source format or compiler. Inspect the report directory for files such as `.tex`, `.md`, or `.pdf`, then use the build instructions appropriate to the source.
For a LaTeX report, check whether a compiler such as Tectonic or `latexmk` is installed and follow the report's source-specific build instructions. Do not assume a particular compiler command until the report files and dependencies have been confirmed.
Main Components
`task99/` — project Python package.
`scripts/` — experiment and utility scripts.
`tests/` — automated tests.
`configs/` — project configuration.
`data/` — data assets.
`models/` — saved model artifacts.
`results/` — experiment outputs and evaluation results.
`figures/` — generated figures.
`report/` — report files and figures.
`logs/` — logs and run records.
`runs/actual_roll/` — run-specific copies of the configuration, data, figures, logs, models, report, and results.