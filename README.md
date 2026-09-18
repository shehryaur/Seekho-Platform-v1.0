# Seekho Platform v1.0

Seekho Platform v1.0 is a Streamlit-based AI curriculum engine for Pakistani teachers. It generates PCTB-aligned lesson packs with local examples, classroom activities, quizzes, answer keys, WhatsApp-ready material, and printable DOCX exports.

This repository is the first working version of the Seekho idea: a practical tool for teachers who need localized classroom material quickly, especially in resource-constrained schools.

## Core Features

- Generates complete lesson packs for Classes 1-12.
- Aligns prompts with PCTB subjects, chapters, and topics.
- Uses district context so examples feel local to students.
- Supports English, Roman Urdu, and Urdu script workflows.
- Creates teacher guides, student handbooks, 40-minute activities, quizzes, and answer keys.
- Exports lesson material to DOCX for printing or sharing.
- Stores optional analytics, feedback, waitlist entries, and generated lessons in Supabase.
- Falls back to local syllabus and district data when the database is unavailable.

## Tech Stack

| Layer | Choice |
| --- | --- |
| App framework | Streamlit |
| AI provider | Google Gemini |
| Data layer | Supabase with local fallbacks |
| Documents | python-docx |
| Styling | Custom Streamlit styling helpers |
| Language | Python |

## Repository Structure

```text
seekho_v3.py          Main Streamlit app and generation flow
database.py          Supabase integration, syllabus data, analytics, feedback
pctb_syllabus.py     Local PCTB syllabus fallback
ui_style.py          Visual styling and UI helpers
supabase_schema.sql  Database schema
seed_db.py           Syllabus seeding utility
requirements.txt     Python dependencies
.streamlit/          Streamlit configuration
```

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Set the required AI key:

```bash
GEMINI_API_KEY=your_key_here
```

Optional Supabase settings:

```bash
SUPABASE_URL=your_supabase_url
SUPABASE_ANON_KEY=your_supabase_anon_key
```

You can also set these in `.streamlit/secrets.toml`.

## Run

```bash
streamlit run seekho_v3.py
```

## Database

The app can run without Supabase by using local syllabus and district data. For persistence, analytics, feedback, and waitlist collection, create the Supabase schema from:

```text
supabase_schema.sql
```

Then seed the syllabus data with:

```bash
python seed_db.py
```

## Why It Matters

Many teachers need localized examples, board-aligned questions, and classroom-ready pacing, but they do not always have time, internet reliability, or support staff. Seekho v1.0 explores how AI can reduce that preparation burden while keeping the teacher in control.

## Status

This is an early prototype. Review generated content before classroom use, especially quizzes, answer keys, local examples, and Urdu translations.
