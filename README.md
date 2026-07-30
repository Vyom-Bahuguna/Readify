# 📖 Readify — Free Online Book Reader

A premium, Kindle-inspired digital reading platform that gives readers free access to a locally cataloged library alongside a searchable global index of millions of digitized books — with AI-assisted reading support, text-to-speech, and accessibility-first design.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [How Search Works](#how-search-works)
- [Reading Support Engine](#reading-support-engine)
- [Roadmap](#roadmap)
- [License](#license)

---

## Overview

Readify combines a polished, front-end reading interface ([index.html](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/index.html)) with a Python + SQLite backend for search, natural language processing, and reading analytics. A secondary Streamlit dashboard ([app.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/app.py)) is available as a backup/alternate interface to the same library and reading-support tools.

Readers can browse a curated local catalog, search a global book index with redirects to trusted digitized sources, and use built-in accessibility and comprehension tools — all for free, with no subscription required.

---

## Key Features

- 🌐 **Global Book Search** — Query a large digital library index and get routed to full digitized copies on Project Gutenberg, Open Library, Google Books, and the Internet Archive.
- ✍️ **Global & Indian Literature Spotlight** — Curated collections spanning world literature, including a dedicated Indian classics registry (Tagore, Kalidasa, Premchand, R. K. Narayan, Arundhati Roy, and more).
- 🎭 **28+ Premium Themes** — Instantly switch between visual themes, including gradient styles, for a personalized reading experience.
- 🔊 **Text-to-Speech Engine** — High-fidelity narration with live paragraph highlighting and adjustable playback speed.
- ♿ **Accessibility & Focus Modes** — Dyslexia-friendly letter spacing and layouts, plus sentence-by-sentence focus view for distraction-free reading.
- 📖 **Floating Dictionary** — Highlight any word to view instant definitions, save terms to your vocabulary list, and play audio pronunciations.
- 🧠 **Comprehension Quizzes & Achievements** — Interactive multiple-choice checkpoints that challenge your reading comprehension, awarding XP and badges.
- 📥 **Custom Document Importer** — Import your own text files or articles to read them in the custom Kindle-style formatting interface.
- 🖊️ **Highlighting & Vocabulary Sanctuary** — Store and review your saved definitions, vocabulary logs, and highlighted text extracts in one centralized dashboard.

---

## Project Structure

This repository is organized into a front-end interface and a supporting Python-based backend:

- 📄 **[index.html](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/index.html)** — The main client interface. A premium Kindle-style ebook reader with rich features, interactive CSS themes, text-to-speech, and accessibility options.
- 📄 **[app.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/app.py)** — Streamlit-based reading dashboard providing reading analytics, accessibility profiles, and backup library views.
- 📄 **[db_setup.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/db_setup.py)** — Database creation and seeding tool. Initializes SQL schema, creates optimization indexes, and seeds `library.db` from a CSV catalog.
- 📄 **[digital_library_starter.csv](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/digital_library_starter.csv)** — The raw CSV source catalog representing a curated collection of local works.
- 📄 **[generate_data.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/generate_data.py)** — Utility script to generate synthetic books data for catalog populating.
- 📄 **[search.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/search.py)** — Search engine utilizing SQL `LIKE` queries with a custom heuristic ranking algorithm.
- 📄 **[reading_support.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/reading_support.py)** — Natural Language Processing (NLP) helper containing syllable-counting heuristics, readability score estimation (Flesch Reading Ease), and advice compiler rules.
- 📄 **[verify_flow.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/verify_flow.py)** — Verification script to run sanity tests on search, NLP, and database routines.
- 📄 **[monitor.html](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/monitor.html)** — System and reading monitoring dashboard.
- 📄 **[.gitignore](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/.gitignore)** — Configured Git rules to keep compiled Python files, caches, and database logs out of version control.

---

## Getting Started

### 📋 Prerequisites

Ensure you have Python 3.8+ installed. Install the necessary Python packages:

```bash
pip install streamlit
```

### 🗄️ 1. Set Up the Database

First, seed the local SQLite database from the starter CSV file:

```bash
python db_setup.py
```

This generates `library.db` and configures indexes on the `title`, `author`, and `topic` fields for optimized query performance.

### 🌐 2. Run the Main Reader Interface

You can serve the web interface locally using Python's built-in HTTP server:

```bash
python -m http.server 8000
```

Once running, navigate to [http://localhost:8000](http://localhost:8000) in your web browser.

### 📊 3. Run the Streamlit Dashboard

To start the alternative reading analytics and backup UI:

```bash
streamlit run app.py
```

---

## How Search Works

The search functionality inside **[search.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/search.py)** runs custom SQL `LIKE` query matches across the `title`, `author`, `topic`, and `keywords` fields. 

Rather than returning unstructured matches, it scores and ranks matches using the following priority order:
1. **Exact Title Match** (highest priority)
2. **Topic Match**
3. **Keyword Overlap** (intersection size between query tokens and database tags)
4. **Partial Title Match**
5. **Partial Author Match**

If no entries match, it gracefully returns a fallback message recommending broader search parameters.

---

## Reading Support Engine

The **[reading_support.py](file:///c:/Users/Vyom Bahuguna/Downloads/helix-reader-main/reading_support.py)** module leverages rule-based NLP to dynamically assess any text:
- **Syllable Counting**: Uses custom English syllable estimation heuristics (handling silent vowels, endings like `-es` or `-ed`, and syllable counts for short words).
- **Readability Scoring**: Calculates the **Flesch Reading Ease** score:
  $$\text{Score} = 206.835 - 1.015 \times \text{ASL} - 84.6 \times \text{ASW}$$
  *(where $\text{ASL}$ is Average Sentence Length and $\text{ASW}$ is Average Syllables per Word)*.
- **Reading Profiles**: Maps the readability score directly to levels: *Elementary*, *Middle School*, *High School*, or *Academic*.

---

## Roadmap

- [ ] Integrate local vector embeddings for semantic search capabilities.
- [ ] Add PDF and EPUB file import parsing.
- [ ] Expand reading analytics charts to track progress over time.
- [ ] Introduce sync features to backup highlights and vocabulary bookmarks to the cloud.

---

## License

This project is licensed under the MIT License.
