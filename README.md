# Renter Assistant (working name)

Answers NSW renters' questions correctly, citing the exact section of the
*Residential Tenancies Act 2010* (NSW). Alongside it, a benchmark that measures
how often general-purpose LLMs get NSW renting questions wrong (outdated law,
other states' law, made-up citations).

Legal information, not legal advice. Serious problems should go to a free
Tenants Advice and Advocacy Service.

## Law version

- Act: Residential Tenancies Act 2010 (NSW), Act No 42 of 2010
- Source: https://legislation.nsw.gov.au/view/html/inforce/current/act-2010-042
- Version used: _fill in the "current version for ..." date shown on the page when you download it_

## Plan (about 6 weeks)

| Week | Goal |
|---|---|
| 1 | Act split into sections. First 50 benchmark questions. Baseline: plain LLMs answer them, graded by hand |
| 2 | Benchmark grows to ~200 questions. Grading rubric plus an LLM judge checked against hand grades |
| 3 | Retrieval + answers with section citations. Experiments on what helps |
| 4-5 | Full-stack app: chat UI with clickable citations, API, Postgres + vector search, feedback, results dashboard, deploy |
| 6 | Launch to real renters, write-up, post |

## How we work

1. Each task has a card in `tasks/`.
2. Ashiq writes pseudocode first (comments only), then asks Claude for a review.
3. Ashiq turns the pseudocode into code, then asks Claude for a review.
4. Claude reviews like a senior engineer: questions and hints first, no finished
   code unless asked. Fix together, then Ashiq commits.
5. AI autocomplete off while practising.

## Layout (planned)

```
data/raw/            downloaded source files (the Act as HTML)
data/sections.jsonl  the Act split into sections (task 01)
bench/               benchmark questions, model answers, grades
src/                 code
tasks/               task cards
```
