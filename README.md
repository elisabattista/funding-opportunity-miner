# Funding Opportunity Miner

An end-to-end Python pipeline for discovering, extracting and prioritizing scholarships, grants and funding opportunities from the web.

---

# Why I Built This Project

This project started from a problem I personally faced.

While searching for scholarships and funding opportunities for postgraduate study in the UK, I quickly realized that finding relevant funding was far more difficult than I had expected.

Scholarships were scattered across hundreds of university websites, government portals, foundations, international organizations and private institutions. Search results were filled with duplicate pages, outdated information and low-quality directories. Even after hours of searching, it was difficult to know whether I had actually found all the opportunities that matched my profile.

At that point, I stopped thinking about scholarships as a search problem and started thinking about them as a data problem.
Instead of continuing to browse manually, I decided to build a system capable of discovering funding opportunities automatically, extracting the most important information from each webpage and ranking the results according to their potential relevance.
That idea eventually became this project.

Although the original motivation was personal, the pipeline is designed to be general and can be adapted to discover grants, fellowships, competitions, research funding and many other opportunities where information is distributed across numerous websites.
---

# Project Overview

Funding Opportunity Miner is an automated three-stage pipeline that transforms raw web search results into a structured and prioritized shortlist of funding opportunities.

Rather than relying on a predefined database of scholarships, the project continuously searches the web, evaluates search results, extracts structured information from each webpage and finally ranks opportunities according to multiple decision criteria.

The pipeline combines information retrieval, web scraping, rule-based information extraction and automated scoring into a fully reproducible workflow.

---

# Pipeline

The project is organized into three independent notebooks.

## Notebook 1 — Funding Discovery

The first notebook focuses on discovering potentially relevant opportunities.

It automatically:

- generates hundreds of search queries;
- performs large-scale web searches using DuckDuckGo Search;
- removes duplicate URLs;
- scores every search result according to relevance;
- penalizes low-quality aggregators;
- identifies official funding pages;
- selects the best candidates for further analysis.

Output:

```
funding_candidates_for_extraction.csv
```

---

## Notebook 2 — Information Extraction

The second notebook visits every candidate page discovered in Notebook 1.

For each webpage it automatically extracts:

- scholarship amounts;
- tuition coverage;
- stipends;
- eligibility requirements;
- application deadlines;
- application links;
- page quality indicators.

The extraction pipeline combines several complementary techniques including:

- Requests
- BeautifulSoup
- Trafilatura
- Regular Expressions
- Dateparser

to maximize robustness across very different website structures.

Output:

```
funding_extracted_opportunities.csv
```

---

## Notebook 3 — Opportunity Prioritization

The final notebook converts the extracted information into an actionable ranking.

Each opportunity receives a score based on factors such as:

- funding amount;
- application deadline;
- completeness of extracted information;
- quality of the webpage;
- eligibility information;
- presence of application links;
- official versus third-party source;
- potential restrictions.

Finally, every opportunity is automatically classified into one of five categories:

- Apply Immediately
- Apply
- Review Carefully
- Low Priority
- Ignore

Output:

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

- Automated web discovery of funding opportunities
- Large-scale search query generation
- Duplicate URL removal
- Rule-based relevance scoring
- Structured information extraction
- Scholarship amount detection
- Deadline extraction
- Eligibility extraction
- Application link detection
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

- ranked funding opportunities;
- extracted scholarship amounts;
- parsed deadlines;
- eligibility summaries;
- application links;
- a prioritized shortlist of opportunities ready for manual review.

Instead of manually browsing hundreds of websites, users can focus only on the opportunities that are most relevant to their profile.

---

# Future Improvements

Possible extensions include:

- semantic ranking using sentence embeddings;
- LLM-assisted eligibility analysis;
- automatic duplicate detection across funding providers;
- scheduled monitoring for newly published opportunities;
- automatic email notifications;
- interactive Streamlit dashboard.

---

# Disclaimer

This project was developed as a personal automation project and research exercise.

Although the extraction pipeline is designed to collect structured information automatically, scholarship requirements, deadlines and funding details may change over time.

Users should always verify the information directly on the official funding provider's website before submitting an application.
