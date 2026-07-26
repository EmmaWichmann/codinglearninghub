# Career Compass

A browser-based learning system that turns daily SQL and Python practice into tracked progress, real skill checks, and portfolio-ready evidence for a career in data, product, or software.

## Live Demo

- **Live site:** https://emmawichmann.github.io/careercompass/
- **Repository:** https://github.com/EmmaWichmann/careercompass

## Overview

Career Compass is a personal learning and career-development tool that I design, build, and use myself. It answers one question every time I open it: *what should I do today?* Instead of a dashboard of competing options, the site recommends a single lesson, tracks whether I completed it, and turns that activity into plain-language progress evidence tied to a defined certification roadmap. I build it using AI-assisted development as a working method, not a shortcut around understanding the code.

## The Problem

Early-career professionals exploring adjacent technical roles — data analyst, product analyst, product manager, AI implementation, software engineering — tend to end up with scattered self-study: disconnected tutorials, flashcard apps, and one-off courses with no single source of truth for what to work on next or what has actually been learned. Two problems compound this:

- Self-directed practice is easy to start and hard to turn into believable, demonstrable evidence for a resume or an interview.
- Trying to prepare for several related roles at once easily turns into five separate, competing curricula instead of one coherent foundation.

## The Solution

Career Compass replaces that sprawl with a single recommended task per visit, backed by a real curriculum and real progress tracking:

- The **Today** page recommends exactly one lesson at a time, drawn from a real external course (SQLBolt for SQL, LearnPython.org for Python) rather than an in-house tutorial.
- Completing a lesson reveals a matching skill check from a custom quiz engine, and progress is recorded automatically — no manual bookkeeping.
- The **Progress** page turns that activity into plain-language evidence (lessons completed, skill checks passed, recent wins) instead of raw scores or jargon.
- The **Certifications** and **Career** pages connect daily practice to specific, named certification targets and a defined cluster of roles, so the practice stays purpose-built instead of open-ended.
- The whole system is intentionally small and static, so there is no backend to maintain and no account system to manage.

## Current Features

- **Today** — one recommended SQL or Python lesson per visit, a short explanation of why it matters, a link to the real external lesson, a "Mark Lesson Complete" action, and a matching Quick Check revealed after completion.
- **Progress** — a plain-language recap of lessons completed, skill checks passed, what's currently being learned in each language, a recent-wins feed, a collapsed future roadmap, and a reset option that requires confirmation.
- **Skill Checks** — a custom exam engine with 20-question quizzes (multiple choice and fill-in) and an 80% pass threshold; a recommendation card that surfaces the next SQL concept check; and an archive of earlier HTML, CSS, and JavaScript assessments.
- **Certifications** — the active certification target (SQL / Relational Database via freeCodeCamp), a readiness summary, and the next and later certifications in the roadmap.
- **Career** — the target role cluster and the reasoning behind the current certification order.
- **Notes** — a searchable library of my own analogies, key concepts, and practice questions, organized into collapsed categories so the page stays easy to scan.
- **Local, private progress** — all progress is stored in the browser's `localStorage`. There is no account and no server, so nothing leaves the device it's used on.
- **Link integrity check** — a small Node script that scans every HTML and Markdown file in the repository for broken internal links.

## How the System Works

- The Today page reads a small, hand-curated curriculum (11 SQL lessons, 10 Python lessons) built from real external course content and the site's own quiz topics, and shows whichever lesson hasn't been marked complete yet.
- Marking a lesson complete increments a stored progress counter, logs a "recent win," and reveals a Quick Check link into the quiz engine for that exact lesson. Once every SQL lesson is complete, Today automatically switches its recommendation to Python — there's no separate page to find or toggle to flip.
- The Progress, Certifications, and Career pages read from that same stored progress plus real skill-check results, so the numbers stay consistent across the site instead of being duplicated in multiple places and drifting out of sync.
- Everything is static HTML, CSS, and JavaScript deployed to GitHub Pages. There is no backend, so all state lives in `localStorage` on whatever device or browser is being used.

## Technology

- Plain HTML, CSS, and vanilla JavaScript — no framework, no bundler, no build step, and no `package.json` dependencies.
- Deployed as a static site via GitHub Pages.
- A custom, lightweight exam engine (`shared/exam-engine.js` + `data/exam-data.js`) that generates quiz questions from structured topic and concept data. It's built to cover 10 languages internally; the live UI currently focuses the active learning path on SQL and Python, with HTML, CSS, and JavaScript kept as an archive.
- Client-side persistence with `localStorage` — no database, no authentication, no server.
- A dependency-free Node.js script (`scripts/check-links.js`) that checks every internal `href`/`src` in the repository and fails if any resolve to a missing file.

## AI-Assisted Development Workflow

I build Career Compass using AI (Claude and Codex) as a coding partner: I describe the problem or the change I want, review what's generated, test it myself in the browser, and iterate from there. The repository's commit history reflects that loop directly — small, incremental changes rather than large untested rewrites, with several commits recording AI co-authorship.

I'm not presenting this as production-grade software engineering experience. I'm early in my technical career, and AI-assisted development lets me focus on product thinking, problem definition, testing, and documentation while I continue building hands-on coding fluency in parallel — the same kind of skill growth this product exists to track. Every meaningful change gets manually tested in a browser, including a click-through of the affected pages and a check for console errors, and the link-integrity script above runs before a change is committed.

## Career Compass and EmmaGetsHired Ecosystem

Career Compass and EmmaGetsHired are two connected products I'm building as part of the same career strategy, each with its own live site and repository:

- **Career Compass** (this project) — the learning and strategy engine: daily practice, skill checks, and progress evidence.
- **[EmmaGetsHired](https://emmawichmann.github.io/emmagetshired/)** — the job search and application platform.

Today, the two are separate deployed sites with no shared code or data between them. The intent is for skills and evidence built up in Career Compass to eventually support features in EmmaGetsHired — for example, using demonstrated SQL or Python proficiency, or tracked learning progress, as real input to the job-search side of the system. That connection is a planned direction, not a built integration yet.

## What I Am Currently Learning

- **Active focus:** SQL, using SQLBolt, following a defined progression from `SELECT`/`FROM` through filtering, aggregation, joins, subqueries, and NULL handling.
- **Next:** Python fundamentals, using LearnPython.org — variables and data types, strings, lists, dictionaries, control flow, loops, and functions.

Both sit inside a broader shared-foundation approach, documented in this repository, that I'm building deliberately instead of five separate, disconnected curricula:

- SQL and Data
- Python and Automation
- Product Thinking
- Technical Communication
- Systems and Workflow Thinking
- Light Technical Building

That foundation is aimed at a cluster of roles I'm keeping open rather than one fixed job title: Data Analyst, Product Analyst, Product Manager, AI Implementation Specialist, and Software Engineer.

## Roadmap

The certification roadmap that Career Compass tracks toward, in order:

1. **SQL / Relational Database** (current) — freeCodeCamp, after the SQLBolt phase and a SQL portfolio project.
2. **Python** (next) — freeCodeCamp Scientific Computing with Python or Data Analysis with Python.
3. **APIs + JSON / Data Workflows** — freeCodeCamp Back End Development and APIs.
4. **Data Visualization / BI** — freeCodeCamp Data Visualization.
5. **AI / Data Foundations** — IBM SkillsBuild digital credentials, later.

The reasoning behind this order, and the broader role-cluster strategy, is documented in the repository itself (`notes/CAREER_STRATEGY.md`, `notes/LEARNING_SYSTEM.md`).

## Running the Project Locally

Career Compass has no dependencies and no build step.

1. Clone the repository:
   ```
   git clone https://github.com/EmmaWichmann/careercompass.git
   cd careercompass
   ```
2. Serve the folder with any static file server, for example:
   ```
   python3 -m http.server 8000
   ```
3. Open `http://localhost:8000/` in a browser.
4. Optional — check for broken internal links before committing a change:
   ```
   node scripts/check-links.js
   ```
   This only requires Node.js; there is nothing to `npm install`.

## Project Status

Career Compass is an actively evolving personal project, not a finished or production product. It has no user accounts, no backend, and no multi-device sync — all progress lives in a single browser's local storage. I iterate on it regularly as both a learning tool and a portfolio piece, and the features described above reflect the current state of the repository rather than a fixed final version.
