# DevSecOps CI/CD Pipeline with Automated Security Gates

## Project description
This project demonstrates a beginner-friendly DevSecOps pipeline that runs security checks automatically when code is pushed to GitHub or a pull request is opened. It combines a small Python source checker with Bandit, pip-audit, and Trivy.

## Objectives
- Detect selected risky Python coding patterns and possible hard-coded credentials.
- Run Python static analysis with Bandit.
- Audit declared Python dependencies with pip-audit.
- Scan repository files for HIGH and CRITICAL issues using Trivy.
- Make security checks part of the continuous integration workflow.

## Technologies
- Python 3.10+
- Jupyter Notebook
- Git and GitHub
- GitHub Actions
- Bandit
- pip-audit
- Trivy

## Project files
- `DevSecOps_CICD_Security_Pipeline.ipynb` — setup, local demonstration, and usage guide.
- `requirements.txt` — Python packages for the checks.
- `DevSecOps_ProjectReport.docx` — project documentation.
- `README.md` — this file.

When you run the notebook's setup cell, it creates:
- `security_scanner.py` — a small educational source scanner.
- `.github/workflows/security.yml` — the GitHub Actions workflow.

## Setup and run locally
1. Install Python 3.10 or newer and Jupyter Notebook.
2. Open the notebook and run its cells in order. The first setup cell creates the scanner and workflow.
3. Install the tools:

   ```bash
   python -m pip install -r requirements.txt
   ```

4. Scan a Python file or directory:

   ```bash
   python security_scanner.py .
   python security_scanner.py . --json security-scan-report.json
   ```

5. Run additional checks:

   ```bash
   bandit -r . -x ./.git,./.venv,./venv -ll
   pip-audit -r requirements.txt
   ```

The demo sample intentionally contains a fake credential marker, so a HIGH finding and non-zero scanner exit code are expected for that sample. Never use real credentials in demo code.

## Enable the CI/CD workflow on GitHub
1. Create a GitHub repository for the project.
2. Run the notebook setup cell and add `security_scanner.py` and `.github/workflows/security.yml` to the repository.
3. Add `requirements.txt` and your application code.
4. Commit and push the files.
5. Open the repository's **Actions** tab and select **DevSecOps Security Pipeline**.
6. Review the job logs and download the `security-scan-report` artifact if it was generated.

The workflow runs on pushes, pull requests, and manual dispatch. The pipeline is configured to fail when the selected security checks report issues at their configured thresholds.

## Dataset / test data
No external dataset is required. The notebook generates a small local demo file (`demo_app/example.py`) containing a clearly labelled fake secret and an `eval()` example to demonstrate detection. The example is intentionally unsafe and should not be used in production.

## References
- GitHub Actions: https://docs.github.com/actions
- Bandit: https://bandit.readthedocs.io/
- pip-audit: https://github.com/pypa/pip-audit
- Trivy: https://trivy.dev/
- Python subprocess documentation: https://docs.python.org/3/library/subprocess.html

## Limitations and responsible use
The custom scanner is educational and pattern-based. It may report false positives and miss complex vulnerabilities. Bandit, pip-audit, and Trivy also have defined coverage and can require configuration. A clean run does not prove that software is secure. Run scans only on repositories and code you own or are authorized to assess.
