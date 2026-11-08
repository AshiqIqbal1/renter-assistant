# Task 01: Split the Act into sections

**Why:** every answer has to cite a section, so the Act needs to become a list
of sections we can search, quote and link to.

**Input:** `data/raw/rta-2010.html` (you download it in Step 0)

**Output:** `data/sections.jsonl`, one JSON object per line, one line per section:

```json
{"number": "41", "heading": "...", "part": "Part 3 ...", "text": "...", "url": "https://legislation.nsw.gov.au/view/html/inforce/current/act-2010-042#sec.41"}
```

The `#sec.41` anchor format is a guess. Find the real one in Step 1.

---

## Step 0: Setup (15 min)

```sh
cd ~/renter-assistant
git init
python3 -m venv .venv
source .venv/bin/activate
pip install beautifulsoup4
```

Download the Act. The site blocks scripts (Cloudflare), so use the browser:

1. Open https://legislation.nsw.gov.au/view/html/inforce/current/act-2010-042
2. Check the page holds the **whole** Act: scroll to the end, or search for the
   last Schedule. If it only shows part, look for a "whole Act" or print view.
3. File > Save Page As > "Web Page, HTML Only" > `data/raw/rta-2010.html`
4. Copy the "current version for ..." date into the README under "Law version".

First commit. You write the message.

## Step 1: Explore (20 min)

Open the saved file in the browser, right-click a section heading > Inspect.
Write your answers here:

1. Which tag + class wraps one whole section?
   -
2. Where is the section number? The heading?
   -
3. How can you tell which Part a section belongs to?
   -
4. What does a section's link anchor look like?
   -

## Step 2: Pseudocode (20 min)

In `src/parse_act.py`, write the plan as **comments only**. No real code yet.
Then tell Claude: "review pseudocode".

## Step 3: Code (45 to 90 min)

Turn the comments into code. Useful: `bs4.BeautifulSoup`, `json`, `pathlib`.
Then tell Claude: "review code".

## Done when

- `python src/parse_act.py` creates `data/sections.jsonl`
- every line is valid JSON and no `text` is empty
- section numbers are unique and stored as **strings** (amended Acts add
  sections like "85A")
- the first section is "1"
- 3 random sections match the website word for word

## You'll practise

HTML/DOM structure, CSS selectors, BeautifulSoup, JSON Lines, writing a script
someone else can rerun.
