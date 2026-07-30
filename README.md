# 🧬 Helix Reader — Next-Gen Kindle Rebuild

A premium, feature-rich, Kindle-inspired digital library application providing access to **15,000 locally cataloged works** and querying a global index of **158 million digitized books**.

## 🚀 Live & Local Links

- 🌐 **Live Website Link:** **[https://hardik-arora.github.io/helix-reader/](https://hardik-arora.github.io/helix-reader/)**
- 🏠 **Local Server Link:** **[http://localhost:8000](http://localhost:8000)**

If you need to start the server again manually in the future, run:
```bash
python3 -m http.server 8000
```
from inside the `helix-reader` folder.

---

## 📂 Repository File Directory

This project combines a premium web interface with a self-contained Python NLP and database backend:

*   **`index.html`**: The Kindle-style digital reader interface with dynamic theme engines, AI Summarizer, and Searchable Dictionary.
*   **`app.py`**: Streamlit-based backup dashboard interface.
*   **`generate_data.py`**: Generates the initial CSV books catalog database.
*   **`db_setup.py`**: Seeds `library.db` and configures SQL indexes.
*   **`search.py`**: Matches terms across title/author/keywords using LIKE queries.
*   **`reading_support.py`**: NLP syllables analysis, readability score calculator, and advice compiler.
*   **`library.db`**: Pre-configured SQLite relational database.
*   **`verify_flow.py`**: Integration testing validation script.

---

## 🌟 Key Features

1. **🌐 158 Million Book Index & Platform Selector**: Query the global digital library in real-time. Clicking "Read Book" launches a platform redirect modal connecting readers directly to digitized copies on **Project Gutenberg, Open Library, Google Books, and Internet Archive**.
2. **✍️ Global Authors Spotlight**: Features legendary literature spanning all continents, including a dedicated Indian literature registry (Rabindranath Tagore, Kalidasa, Arundhati Roy, R. K. Narayan, Premchand, Wings of Fire, and classical epics).
3. **🎭 Premium Styling & Themes**: Toggle between 28 premium themes (including 8 gorgeous linear gradients) instantly.
4. **🔊 Text-to-Speech (TTS) Voice Engine**: High-fidelity paragraph reading voice synthesis with active highlighting and speed controls.
5. **♿ Reading Focus Modes**: Dyslexic-friendly layouts (dyslexic letter-spacing) and sentence-by-sentence focus view toggles.
6. **📖 Floating Dictionary**: Highlight any word in the reader to view meanings, save vocabulary words, and trigger audio pronunciation.
7. **🧠 Quizzes & Badges**: Interactive multi-choice comprehension checkpoints with XP points and achievements.
8. **📥 Custom Document Importer**: Add personal logs or external articles and read them in the custom layout.
9. **🖊️ Highlighting & Vocabulary Sanctuary**: Store vocabulary logs and colored highlight extracts.
