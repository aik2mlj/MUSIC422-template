# MUSIC 422 Python Environment Setup (using uv)

This tutorial explains how to set up and use the course Python environment with **uv**.  
Please follow the steps carefully to ensure your environment matches the grader’s.

---

## 1. Install `uv` (official method)

Follow the official installation instructions from Astral:

- https://docs.astral.sh/uv/getting-started/installation/

For macOS / Linux:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

For Windows (PowerShell):

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

After installation, **restart your terminal**, then verify the installation with:

```bash
uv --version
```

---

## 2. Replicate the course Python environment

This repository is provided as a **GitHub template** to help you get started quickly with the correct environment and folder structure.

### Create your own copy from the template

1. Open the course template repository on GitHub.
2. Click **“Use this template”** → **“Create a new repository”**.
3. Choose a repository name (e.g., `MUSIC422`).
4. **Set the repository to Private** (required).
5. Click **“Create repository”**.

This creates your own independent copy of the template—changes you make will not affect the original.

- **Do NOT create a public repository**
- Public repos make your homework searchable and can lead to **plagiarism issues**

### Clone your repository

Copy the URL of your newly created repository, then run:

```bash
git clone <your-repo-url>
cd <your-repo-name>
```

## Create the environment

You are provided with the following files.

- `pyproject.toml`
- `uv.lock`
- `.python-version`

I also optionally provided a `.gitignore` file to help you avoid committing unnecessary files if you use Git.

Make sure all these files are in the **same directory**.

From that directory, simply run:

```bash
uv sync
```

This will:

- Install **Python 3.13.9** (if not already available)
- Create a virtual environment in `.venv/`
- Install NumPy, matplotlib, and Scipy with **exact locked versions**

---

## 3. (Optional) Activate the environment

You normally **do not need to activate** the virtual environment if you use `uv run`
(the recommended way to run scripts).

If you prefer to activate it manually:

### macOS / Linux

```bash
source .venv/bin/activate
```

### Windows (PowerShell)

```powershell
.venv\Scripts\Activate.ps1
```

---

## 4. Test that the environment works

Verify the Python version:

```bash
uv run python --version
```

Expected output:

```text
Python 3.13.9
```

Verify the installed libraries:

```bash
uv run python -c "import numpy, matplotlib; print(numpy.__version__, matplotlib.__version__)"
```

Expected output:

```text
2.3.5 3.10.6
```

If you see these versions, your environment is set up correctly.

---

## 5. Recommended homework folder structure

We recommend organizing your work like this:

```text
MUSIC422/
├── pyproject.toml
├── uv.lock
├── .python-version
├── hw1/
│   └── src/
│       └── main.py
├── hw2/
│   └── src/
│       └── solution.py
├── hw3/
│   └── src/
│       └── problem.py
```

Notes:

- Each homework has its **own folder** (`hw1`, `hw2`, …)
- Put all Python code inside a `src/` subfolder

---

## 6. Running Python scripts with `uv run`

This is the **recommended way** to run all Python code.

Example:

```bash
uv run python hw1/src/main.py
```

Using `uv run` ensures:

- The correct Python version is used
- The correct dependencies are loaded
- Your script runs exactly as expected by the grader

---

## 7. Using `uv` and Python in VS Code (Optional)

This section explains how to configure **VS Code** so it works smoothly with `uv` and the course environment.

### Install the Python extension

In VS Code:

1. Open **Extensions** (`Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Install **Python** (by Microsoft)

This extension provides syntax highlighting, linting, debugging, and Jupyter support.

### Open the project folder

In VS Code:

- Click **File → Open Folder**
- Select the **root folder** of your repository (the one containing `pyproject.toml`)

Do **not** open individual homework folders directly.

### Create the environment (if not already done)

Open the VS Code terminal (**Terminal → New Terminal**) and run:

```bash
uv sync
```

This creates the `.venv/` folder used by VS Code.

### Select the correct Python interpreter

1. Open the Command Palette
   (`Ctrl+Shift+P` / `Cmd+Shift+P`)
2. Search for **Python: Select Interpreter**
3. Choose the interpreter located at:
   - `.venv/bin/python` (macOS / Linux)
   - `.venv\Scripts\python.exe` (Windows)

VS Code will remember this choice.

### (Optional) Enable VS Code Run / Debug button

If you want the ▶ Run button to work correctly:

- Make sure the selected interpreter is `.venv`
- Ensure `uv sync` has completed successfully

For consistency with grading, always verify your code at least once using:

```bash
uv run python your_script.py
```

### Common issues

- **Wrong Python version shown**
  → Re-run _Python: Select Interpreter_ and choose `.venv`

- **`ModuleNotFoundError` in VS Code but not in terminal**
  → You are likely using the wrong interpreter

- **`uv` not found in VS Code terminal**
  → Restart VS Code after installing `uv`

---

## 8. Git version control (Optional)

We recommend using Git for version control. This will help you organize and track changes. But this is up to your preference, not as a requirement for submission.

Best practices:

- Commit early and often
- Use clear commit messages

---

## Summary

Core commands you’ll use:

```bash
uv sync
uv run python path/to/script.py
```

You can always refer to the [uv official doc](https://docs.astral.sh/uv/) if you want to use a certain feature. If something breaks, ask the TA for help.

Happy coding!
