# Funding Opportunity Miner

An end-to-end Python pipeline for discovering, extracting and prioritizing scholarships, grants and funding opportunities from the web.

---

# Project Overview

Finding scholarships, grants, fellowships and funding opportunities is often a frustrating and highly manual process.

Relevant opportunities are scattered across university websites, government portals, foundations, international organizations and third-party directories. Search engines frequently return duplicate pages, outdated information and low-quality aggregators, making systematic discovery difficult.

This project implements an end-to-end Python pipeline that automates the entire discovery process.

Rather than relying on a predefined list of scholarships, the pipeline searches the web, identifies potentially relevant funding opportunities, extracts structured information from each page and finally prioritizes the most promising opportunities.

The final result is a ranked, actionable shortlist of funding opportunities that can be reviewed and acted upon efficiently.

---

# Why this project?

Traditional scholarship searches require manually browsing hundreds of university websites, government portals and private foundations.

The objective of this project is to demonstrate how web search, information extraction and rule-based ranking can be combined into a reproducible pipeline that significantly reduces the time required to identify relevant funding opportunities.

---

# Pipeline

The project is organized into three independent notebooks.

## Notebook 1 — Funding Discovery

The first stage performs large-scale web discovery.

It automatically:

- generates hundreds of search queries;
- searches the web using DuckDuckGo Search;
- removes duplicate URLs;
- scores every search result according to relevance;
- identifies official scholarship pages;
- penalizes low-quality aggregators and irrelevant pages;
- exports the highest-quality candidates for further analysis.

**Output**

```
funding_candidates_for_extraction.csv
```

---

## Notebook 2 — Information Extraction

The second stage visits every candidate page discovered in Notebook 1.

For each page it automatically extracts:

- scholarship amounts;
- tuition coverage;
- stipends;
- eligibility requirements;
- application deadlines;
- application links;
- page quality indicators.

The notebook combines:

- Requests
- BeautifulSoup
- Trafilatura
- Regular Expressions
- Dateparser

to maximize extraction quality while remaining lightweight and fully automated.

**Output**

```
funding_extracted_opportunities.csv
```

---

## Notebook 3 — Opportunity Prioritization

The final stage converts the extracted information into an actionable ranking.

Each opportunity receives a score based on multiple factors including:

- funding amount;
- application deadline;
- page quality;
- eligibility information;
- availability of application links;
- official vs third-party source;
- potential restrictions;
- completeness of the extracted information.

Finally, every opportunity is automatically classified into one of five categories:

- Apply Immediately
- Apply
- Review Carefully
- Low Priority
- Ignore

**Output**

```
funding_actionable_shortlist.csv
```

---

# Workflow

```text
Web Search
      │
      ▼
Notebook 1
Funding Discovery
      │
      ▼
funding_candidates_for_extraction.csv
      │
      ▼
Notebook 2
Information Extraction
      │
      ▼
funding_extracted_opportunities.csv
      │
      ▼
Notebook 3
Opportunity Prioritization
      │
      ▼
funding_actionable_shortlist.csv
```

---

# Features

- Automated scholarship discovery
- Web search query generation
- Duplicate URL removal
- Rule-based relevance scoring
- Structured information extraction
- Funding amount extraction
- Deadline detection
- Eligibility extraction
- Application link extraction
- Opportunity prioritization
- CSV and Excel export
- Modular pipeline architecture

---

# Technologies

- Python
- Pandas
- NumPy
- Requests
- BeautifulSoup
- Trafilatura
- DuckDuckGo Search (DDGS)
- Dateparser
- OpenPyXL

---

# Repository Structure

```text
.
├── notebooks
│   ├── 01_funding_discovery.ipynb
│   ├── 02_funding_extraction.ipynb
│   └── 03_funding_prioritization.ipynb
│
├── results
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

# Example Outputs

The pipeline automatically produces:

- ranked scholarship opportunities;
- extracted funding amounts;
- parsed application deadlines;
- eligibility summaries;
- application links;
- a prioritized shortlist of opportunities.

These outputs significantly reduce the amount of manual work required to identify funding opportunities worth pursuing.

---

# Future Improvements

Possible extensions include:

- semantic ranking using sentence embeddings;
- LLM-assisted eligibility analysis;
- automatic duplicate detection across funding providers;
- automatic monitoring of newly published opportunities;
- email notifications for new scholarships;
- interactive Streamlit dashboard.

---

# Disclaimer

This project is intended as a research and automation tool.

Scholarships, grants, deadlines and eligibility requirements may change over time. Users should always verify the information directly on the official funding provider's website before submitting an application.
