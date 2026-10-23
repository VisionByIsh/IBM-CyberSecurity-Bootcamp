# WebShield: Automated Website Security Auditing and Risk Assessment Tool

## Project description
WebShield is an educational Python tool that checks an authorized website for selected HTTP security headers and performs a basic CORS configuration probe. It presents findings with severity labels, evidence, and recommendations, then exports CSV reports.

**Responsible use:** Scan only websites you own or have explicit permission to test. This project is a lightweight checker, not a full vulnerability scanner or proof of exploitability.

## Technologies used
- Python 3
- Jupyter Notebook
- `requests` for HTTP requests
- `pandas` for findings tables and CSV export

## Checks included
- Strict-Transport-Security (HSTS)
- Content-Security-Policy (CSP)
- X-Content-Type-Options
- X-Frame-Options
- Referrer-Policy
- Permissions-Policy
- Basic CORS response checks using a reserved test origin

## Dataset
This project does not require a dataset. It assesses live HTTP response headers from a target that you are authorized to test. For a reproducible demo, use your own local test website or a deliberately configured lab application. Do not use third-party websites without permission.

## Files
- `YourName_WebShield.ipynb` — complete notebook source and run instructions
- `requirements.txt` — Python dependencies
- `YourName_ProjectReport.docx` — project documentation

## Setup and run
1. Install Python 3.10 or newer and Jupyter Notebook/JupyterLab.
2. Place the notebook and `requirements.txt` in the same folder.
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Start Jupyter:
   ```bash
   jupyter notebook
   ```
   If Jupyter is not installed, install it with `pip install notebook`.
5. Open `YourName_WebShield.ipynb`.
6. In the scan cell, replace `https://example.com` with a URL you own or have permission to test.
7. Run the cells from top to bottom.
8. Review the findings table and generated CSV files.

## Output
The notebook displays scan metadata and a findings table with category, check, status, severity, evidence, and remediation advice. It exports a findings CSV and a scan-metadata CSV.

## Limitations
- The scanner checks only selected headers and one OPTIONS-based CORS probe.
- It does not crawl pages, authenticate, test every API endpoint, or validate all security controls.
- Findings require manual verification. Severity labels are simple triage guidance, not CVSS scores.
