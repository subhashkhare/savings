# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

**Spendly** — a Flask + SQLite expense tracker built as a step-by-step learning project. Many pieces are deliberately stubbed and labelled with the step that implements them (e.g. "coming in Step 7"). When implementing a step, replace the matching stub rather than adding parallel code.

## Commands

The virtualenv lives in `expense/` (Windows layout — `expense/Scripts/`), not `venv/`.

```powershell
expense\Scripts\activate            # activate venv (PowerShell/cmd)
pip install -r requirements.txt     # flask, werkzeug, pytest, pytest-flask
python app.py                       # dev server at http://localhost:5001 (debug on)
pytest                              # run tests (none exist yet)
pytest tests/test_x.py::test_name   # run a single test
```

There is no linter or build step configured.

## Architecture

- `app.py` — the single Flask app; all routes live here. Public pages (`/`, `/register`, `/login`, `/terms`, `/privacy`) render templates. `/logout`, `/profile`, and `/expenses/add|<id>/edit|<id>/delete` are placeholder routes returning strings, to be implemented in Steps 3, 4, 7, 8, 9.
- `database/db.py` — empty stub for Step 1. Its intended contract: `get_db()` returns a SQLite connection with `row_factory` set and foreign keys enabled; `init_db()` creates tables with `CREATE TABLE IF NOT EXISTS`; `seed_db()` inserts sample dev data. The DB file `expense_tracker.db` is gitignored.
- `templates/` — Jinja2. Every page extends `base.html`, which provides the navbar, footer, Google Fonts (DM Serif Display / DM Sans), and blocks `title`, `head`, `content`, `scripts`. Page-specific JS goes in the `scripts` block (see `landing.html`); links use `url_for(<view function name>)`.
- `static/css/style.css` — one global stylesheet for all pages. `static/js/main.js` — global JS, currently empty.
- Currency/copy is India-oriented ("Track every rupee").

`intro.md` is a pasted Claude Code session transcript, not project documentation.
