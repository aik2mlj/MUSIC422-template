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

You will be provided with the following files.

- `pyproject.toml`
- `uv.lock`
- `.python-version`

I also optionally provided a `.gitignore` file to help you avoid committing unnecessary files if you use Git.

Make sure all these files are in the **same directory**.

From that directory, run:

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

## 7. Git version control (Optional)

We recommend using Git for version control. But this is up to your preference, not as a requirement for submission.

### Best practices:

- Create a **private repository** (GitHub / GitLab / local only)
- Commit early and often
- Use clear commit messages

### Important:

- **Do NOT create a public repository**
- Public repos make your homework searchable and can lead to **plagiarism issues**
- You are responsible for keeping your work private

---

## Summary

Core commands you’ll use:

```bash
uv sync
uv run python path/to/script.py
```

If something breaks, ask the TA for help.

Happy coding!
