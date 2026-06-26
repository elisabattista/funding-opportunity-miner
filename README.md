# Funding Opportunity Miner

An end-to-end Python pipeline for discovering, extracting and prioritizing scholarships, grants and funding opportunities from the web.

---

# Why I Built This Project

This project started from a problem I personally encountered.

While searching for scholarships to support postgraduate study in the UK, I realized that finding relevant funding opportunities was surprisingly difficult. There was no single place where scholarships were collected in a structured way. Instead, information was scattered across university websites, government portals, foundations, international organizations and countless third-party directories.

Searching manually quickly became frustrating. The same opportunities appeared repeatedly, many pages were outdated, and it was difficult to understand whether I had actually explored all the funding opportunities that matched my profile.

Eventually, I stopped thinking about scholarships as a search problem and started thinking about them as a data problem.

Instead of manually browsing hundreds of websites, I decided to build a system capable of automatically discovering funding opportunities, extracting the most useful information from each webpage and prioritizing the results according to their relevance.

That idea eventually became **Funding Opportunity Miner**.

Although the original motivation was personal, the pipeline was intentionally designed to be reusable. The same workflow can be applied to grants, fellowships, research funding, competitions or any other opportunity where information is distributed across many independent websites.

---

# Project Overview

Funding Opportunity Miner is a modular three-stage pipeline that transforms raw web search results into a structured and prioritized shortlist of funding opportunities.

Instead of relying on a predefined database of scholarships, the pipeline performs its own web discovery, evaluates search results, extracts structured information from candidate webpages and ranks opportunities using a transparent rule-based scoring system.

The project combines information retrieval, web scraping, information extraction and automated decision rules into a fully reproducible workflow.

---

# Pipeline

The project is organized into three independent notebooks.

## Notebook 1 — Funding Discovery

The first notebook is responsible for discovering relevant opportunities across the web.

It automatically:

* generates hundreds of search queries;
* performs large-scale web searches using DuckDuckGo Search;
* removes duplicate URLs;
* evaluates the relevance of every search result;
* penalizes low-quality aggregators;
* identifies official funding pages;
* exports the most promising opportunities for further analysis.

**Output**

```
funding_candidates_for_extraction.csv
```

---

## Notebook 2 — Information Extraction

The second notebook visits every candidate page discovered in Notebook 1.

For each webpage it extracts structured information including:

* scholarship amounts;
* tuition coverage;
* stipends;
* eligibility requirements;
* application deadlines;
* application links;
* page quality indicators.

The extraction pipeline combines multiple complementary techniques, including Requests, BeautifulSoup, Trafilatura, Regular Expressions and Dateparser, to remain robust across websites with very different structures.

**Output**

```
funding_extracted_opportunities.csv
```

---

## Notebook 3 — Opportunity Prioritization

The final notebook converts the extracted information into an actionable ranking.

Each opportunity is scored according to multiple criteria, including:

* funding amount;
* application deadline;
* completeness of extracted information;
* webpage quality;
* eligibility information;
* availability of application links;
* official versus third-party source;
* potential restrictions.

Finally, every opportunity is automatically assigned to one of five categories:

* Apply Immediately
* Apply
* Review Carefully
* Low Priority
* Ignore

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

* Automated discovery of scholarships and funding opportunities
* Large-scale search query generation
* Duplicate URL removal
* Rule-based relevance scoring
* Structured information extraction
* Funding amount detection
* Deadline extraction
* Eligibility extraction
* Application link detection
* Opportunity prioritization
* CSV and Excel export
* Modular pipeline architecture

---

# Technologies

* Python
* Pandas
* NumPy
* Requests
* BeautifulSoup
* Trafilatura
* DuckDuckGo Search (DDGS)
* Dateparser
* OpenPyXL

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

* ranked funding opportunities;
* extracted scholarship amounts;
* parsed application deadlines;
* eligibility summaries;
* application links;
* a prioritized shortlist of opportunities ready for manual review.

Rather than manually browsing hundreds of websites, users can focus their attention on the opportunities that are most relevant to their profile.

---

# Future Improvements

Possible extensions include:

* semantic ranking using sentence embeddings;
* LLM-assisted eligibility analysis;
* automatic duplicate detection across funding providers;
* scheduled monitoring of newly published opportunities;
* email notifications for newly discovered funding opportunities;
* an interactive Streamlit dashboard.

---

# Disclaimer

This project was originally developed to solve a real personal problem and later evolved into a reusable automation pipeline.

Although the extraction pipeline automatically collects structured information, scholarship requirements, deadlines and funding details may change over time. Users should always verify the information directly on the official funding provider's website before submitting an application.
