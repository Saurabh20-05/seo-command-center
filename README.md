<a href="https://labs.nmgdigital.com/">
  <img src="https://labs.nmgdigital.com/assets/logos/forge-hex.svg"
       title="Forge-NMG-Labs-Hackathon"
       alt="Forge-NMG-Labs-Hackathon"
       width="200"
       height="200"/>
</a>

<p style="font-size: 11px; color: #777777; margin-top: 5px; font-family: sans-serif;">
  Presented by <a href="https://nmgdigital.com/" style="color: #777777; text-decoration: underline;">NMG Digital</a>
</p>

---

<h1 align="center">SEO Command Center</h1>



# Overview

SEO Command Center is an AI-powered technical SEO auditing platform that automates the process of analyzing website crawl data, identifying SEO issues, prioritizing recommendations, and generating professional reports.

The platform processes Screaming Frog SEO exports and transforms thousands of URLs into actionable SEO insights through a multi-agent workflow. By combining deterministic SEO analysis with local AI models, the system delivers fast, scalable, and transparent technical SEO audits without relying on external APIs.

Built using Claude Code, Ollama, Python, MCP Server, and a real-time dashboard architecture, SEO Command Center provides a complete end-to-end workflow for technical SEO analysis and reporting.

---

# Why This Project?

Technical SEO audits often require manually reviewing thousands of pages, identifying issues, prioritizing fixes, and preparing reports for stakeholders.

SEO Command Center automates this workflow by:

* Detecting technical SEO issues automatically
* Prioritizing findings based on severity
* Generating AI-assisted recommendations
* Producing client-ready reports
* Visualizing audit progress in real time
* Reducing manual auditing effort

---

# Key Features

* Automated Technical SEO Auditing
* Screaming Frog Export Processing
* Multi-Agent Workflow Architecture
* AI-Assisted SEO Recommendations
* Severity-Based Issue Prioritization
* Title Tag Optimization
* Meta Description Optimization
* Redirect Mapping Suggestions
* Live Dashboard Monitoring
* Client-Ready HTML Reporting
* Structured JSON Export
* Real-Time Audit Tracking
* Offline Local AI Processing
* Rule-Based SEO Validation Engine

---

# System Architecture

```text
Screaming Frog Export
          │
          ▼
      Data Ingestion
          │
          ▼
      SEO Analysis
          │
          ▼
    Issue Detection
          │
          ▼
   Issue Prioritization
          │
          ▼
      AI Fix Engine
          │
          ▼
    Report Generator
          │
          ▼
 Dashboard & Reports
```

---

# Multi-Agent Workflow

The platform utilizes specialized agents responsible for different stages of the auditing process.

| Agent          | Responsibility                        |
| -------------- | ------------------------------------- |
| Ingest Agent   | Reads and validates crawl exports     |
| Auditor Agent  | Detects technical SEO issues          |
| Fix Agent      | Generates AI-assisted recommendations |
| Reporter Agent | Produces structured reports           |

---

# Project Structure

```text
seo-command-center/
│
├── .claude-plugin/
│   └── plugin.json
│
├── .claude/
│   ├── hooks/
│   │   └── audit.sh
│   ├── audit.jsonl
│   └── settings.json
│
├── agents/
│   ├── ingest.md
│   ├── auditor.md
│   ├── fixer.md
│   └── reporter.md
│
├── commands/
│   └── seo-audit.md
│
├── dashboard/
│   ├── index.html
│   └── app.js
│
├── mcp/
│   └── server.py
│
├── seo/
│   ├── __init__.py
│   └── detector.py
│
├── outputs/
│   ├── report.json
│   └── report.html
│
├── scripts/
│   └── export-transcript.sh
│
├── skills/
│   └── seo-audit/
│       └── SKILL.md
│
├── run.py
└── README.md
```

---

# SEO Checks Supported

## Page Titles

* Missing Title Tags
* Duplicate Titles
* Title Too Long
* Title Too Short

## Meta Descriptions

* Missing Meta Descriptions
* Duplicate Meta Descriptions
* Meta Description Too Long

## Headings

* Missing H1 Tags
* Duplicate H1 Tags
* Multiple H1 Tags

## Response Codes

* Redirects (3xx)
* Redirect Chains
* Redirect Loops
* Client Errors (4xx)
* Server Errors (5xx)

## Content Analysis

* Thin Content Detection
* Missing Image Alt Text

## Site Architecture

* Orphan Pages
* Non-Indexable Linked Pages
* Canonical Issues

## Performance

* Slow Page Detection

---

# Tech Stack

## Backend

* Python
* Pandas
* CSV Processing
* MCP Server

## AI Layer

* Claude Code
* Ollama
* Qwen 3.5
* Local LLM Integration

## Frontend

* HTML5
* CSS3
* JavaScript

## Reporting

* JSON Reports
* HTML Reports

## Development

* Git
* VS Code

---

# Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/seo-command-center.git

cd seo-command-center
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Install MCP:

```bash
pip install mcp
```

---

# Running the Project

Run the audit:

```bash
python run.py sample-export/
```

Start the dashboard server:

```bash
python mcp/server.py
```

Open the dashboard:

```text
http://localhost:7700
```

---

# Input Format

The platform accepts Screaming Frog SEO exports.

Required file:

```text
internal_all.csv
```

Key fields analyzed:

* Address
* Status Code
* Indexability
* Title 1
* Meta Description 1
* H1-1
* Word Count
* Inlinks
* Response Time
* Canonical Link Element 1
* Redirect URL

---

# Output Files

```text
outputs/
├── report.json
└── report.html
```

### report.json

Machine-readable SEO audit report containing:

* Issue summaries
* Severity classifications
* Affected URLs
* Recommendations
* Run metadata

### report.html

Client-ready report suitable for stakeholder presentation and review.

---

# Example Workflow

1. Export website crawl data from Screaming Frog.
2. Place the export folder inside the project directory.
3. Execute the audit process.
4. Monitor progress through the live dashboard.
5. Review generated findings.
6. Export reports.
7. Apply recommended fixes.

---

# Dashboard Features

* Live Issue Counter
* Severity Breakdown
* Audit Progress Tracking
* URL Inspection
* Real-Time Updates
* Report Export Controls
* Interactive Monitoring Interface

---

# Performance Optimizations

* Rule-Based SEO Detection
* Efficient CSV Processing
* Reduced Model Calls
* Local AI Execution
* Modular Agent Architecture
* Scalable Crawl Processing
* Separation of Detection and AI Reasoning

---

# Screenshots

## Dashboard

Add dashboard screenshot here.

```text
assets/dashboard.png
```

## Generated Report

Add report screenshot here.

```text
assets/report.png
```

---

# Future Enhancements

* Hreflang Validation
* XML Sitemap Auditing
* Core Web Vitals Integration
* Schema Markup Validation
* Internal Linking Recommendations
* Historical SEO Tracking
* Multi-Site Auditing
* Automated Fix Deployment

---

# Project Highlights

* AI-Powered SEO Auditing
* Multi-Agent Architecture
* Real-Time Dashboard
* Local AI Processing
* Automated Prioritization
* Client-Ready Reporting
* Technical SEO Automation
* End-to-End Audit Workflow

---

# Conclusion

SEO Command Center demonstrates how AI agents can automate complex technical SEO workflows while maintaining transparency, scalability, and actionable reporting.

The project combines deterministic SEO analysis with AI-assisted recommendations to create a complete technical SEO audit and reporting solution suitable for agencies, consultants, marketers, and website owners.

---

# Acknowledgements

Built during Forge Sprint 01 by NMG Labs and NMG Digital.
