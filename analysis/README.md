# HackerOne Hacktivity Data Analysis

This is a part of my 60 ECTS master's project in Data Science, where I research the effectiveness of bug bounty programs, what types of vulnerability types are the most commonly found, and how preventable these vulnerabilities are.

## Source Data

Public HackerOne hacktivity reports from February 2014 to February 2026. Scraping of reports: https://github.com/arojonasar/hackerone-reports

## Files

| File | Description |
|------|-------------|
| `h1data.ipynb` | Main analysis notebook |
| `vuln_classification.py` | OWASP Top 10 / CWE mapping and preventability scores |
| `h1reports.csv` | Dataset

---

## Analysis Outline

### Data Loading & Overview
- Load data, inspect shape, column types, and missing values.

### Data Cleaning & Feature Engineering
- Parse dates
- Convertions
- Consolidate 186 original HackerOne vulnerability type labels into 34 semantic categories.
- Filter valid reports (`substate` in `{resolved, informative}`).

### Reporting Behaviour
- Submission volume by year and month (all reports vs. valid reports).
- New programs launched per year/month.

### Overall Vulnerability Type Distribution
- Missing vulnerability type data by year.
- Top vulnerability types by report count.

### Vulnerability Types by Severity
- Severity breakdown per vulnerability type.
- Statistical tests: Chi-square test of independence, Cramér's V effect size, Kruskal-Wallis test (severity treated as ordinal).

### Root Cause Classification
- Map each consolidated type to its primary OWASP Top 10 (2025) category via `vuln_classification`.
- Assign preventability scores (1–5 scale).
- Vulnerability types by report count and preventability score.

### Vulnerability Type Trends Over Time
- Year-over-year share of each type.
- Stability of the top-type ranking.

### Preventability Analysis
- Preventability × OWASP category cross-analysis

### Severity Distribution Over Time
- Missing severity data by year.
- Severity proportions per year.

### Resolution Rates & Report Validity
- Breakdown by substate (resolved, informative, duplicate, N/A, spam).
- Overall valid-report rate.

### Time to Disclosure
- Distribution of days from submission to disclosure.
- Relationship between severity and time to disclosure.

### Bounty Analysis
- Bounty by severity.
- Zero-bounty analysis: proportion of bounties set to $0 and reasons.

### Program Maturity — New vs. Experienced Programs
- Define "new" programs by age.
- Compare vulnerability type distribution, severity, validity rates, and time to disclosure between new and experienced programs.

### Effectiveness by Vulnerability Type
- Resolution rate and average time to disclose per vulnerability type.

### Hypothesis Testing — Same Vulnerabilities Repeat Across Programs
> *Hypothesis: the same vulnerability types recur repeatedly across different programs and platforms.*

- **Cross-program coverage**: percentage of programs that report each vulnerability type.
- **Concentration analysis**: Check whether a few types dominate.
- **Cross-program similarity**: cosine similarity heatmap over the top-20 programs.
- **Chi-square test of independence**: program × vulnerability type contingency table.

---

## Research Questions

1. What vulnerability types are most commonly reported in bug bounty programs, and do the same types recur across programs and platforms?
   - 1.1 What are the root causes of the most commonly reported vulnerability types?
   - 1.2 To what extent are these vulnerabilities preventable?
2. *(Additional questions addressed and hypotheses in the full thesis.)*
