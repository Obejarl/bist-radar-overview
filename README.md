# BIST Radar (overview)

A data pipeline and web panel that scores and ranks every listed BIST stock (631) by combining market data, company disclosures and search interest. The source code is private; this repository only describes the project. Walkthrough or code access is available on request.

## What it does

- **Two-stage scoring:** a cheap pre-score from market data, disclosure history and filings covers all 631 stocks; the expensive signal (Google Trends, about 6 s per stock) is then fetched only for the top candidates. Every stock still gets a final rank.
- **Live and full scans:** a quick scan (about 5 minutes) for intraday use and a full scan (about 50 minutes) after the close, each written to a separate Excel file.
- **Disclosure parsing:** pulls and parses KAP (Public Disclosure Platform) filings for each company.
- **Data cleaning:** separates the 807 raw company records into tradable stocks and non-equity issuers (banks, bonds) with a generated exclusion list.
- **Self-updating:** the panel detects a confirmed market close from the data itself and refreshes in the background.
- **Quality checks:** the suite includes unit, scenario and edge-case tests, plus a full-coverage audit that runs functions on all 631 stocks and looks for silent errors (empty names, truncated text, missing fields), not just crashes.

## Stack

Python, Flask, pandas, openpyxl (Excel output), Google Trends and KAP data sources.

## Status

Personal project. Private repository.
