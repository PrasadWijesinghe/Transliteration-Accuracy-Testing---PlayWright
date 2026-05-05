# Test Automation

This project runs a Playwright-based automation script against a Sinhala translation frontend and writes the observed results back into an Excel workbook.

## What It Does

- Reads test inputs from the workbook in this folder, `IT23228030_Assignment 1 - Test cases.xlsx`
- Detects the input, expected output, actual output, and status columns automatically when possible
- Opens the configured frontend URL in Chromium
- Sends each Singlish input to the UI
- Captures the translated Sinhala output
- Writes results back to the spreadsheet

## Requirements

- Python 3.10 or newer
- Google Chrome / Chromium support for Playwright

## Installation

Install the Python dependencies:

```bash
pip install -r IT23228030_requirements.txt
```

Install the Playwright browser binaries:

```bash
playwright install chromium
```

## Usage

Run the script from this folder:

```bash
python IT23228030_test_automation.py
```

Common options:

- `--excel PATH` to use a different Excel file
- `--sheet NAME` to choose a workbook sheet
- `--header-row N` to force the header row
- `--max-header-scan-rows N` to limit header detection
- `--url URL` to change the frontend address
- `--headless` to run without opening a visible browser window
- `--output PATH` to save results to a different file
- `--save-every N` to save after every N rows
- `--wait-ms N`, `--retries N`, and `--retry-wait-ms N` to tune response waiting
- `--type-delay-ms N`, `--timeout-ms N`, and `--slow-mo-ms N` to tune browser timing
- `--keep-open` to leave the browser open after the run finishes

Example:

```bash
python IT23228030_test_automation.py --headless --url https://www.pixelssuite.com/chat-translator
```

## Default Input File

The script looks for this workbook by default:

- `IT23228030_Assignment 1 - Test cases.xlsx`

If the workbook does not use the expected column names, you can override them with:

- `--input-col`
- `--expected-col`
- `--actual-col`
- `--status-col`

## Output

The script writes the results into the same workbook by default and fills the `Actual output` and `Status` columns.

## Notes

- The frontend URL can also be provided through the `FRONTEND_URL` environment variable.
- The script is designed for the chat translator UI and includes retry logic for delayed responses and overlay popups.
