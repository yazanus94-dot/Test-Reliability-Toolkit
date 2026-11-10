# Test-Reliability-Toolkit

![Python 3.9+](https://img.shields.io/badge/python-3.9%2B-blue)

Three small, focused, zero-dependency Python command-line tools for QA engineering and repository quality. Each tool is stdlib-only (no runtime dependencies), ports to Python 3.9+, and follows the same engineering standards: full test suite, CI on GitHub Actions, MIT license, and a conventional-commits discipline.

## Tools

| Tool | What it does | Install & test |
|------|-------------|----------------|
| **[api-smoke-tester](https://github.com/yazanus94-dot/api-smoke-tester)** | Declarative HTTP API smoke tests described in one JSON file — status codes, headers, JSON fields, body text, latency. Secrets are interpolated from environment variables, so no token ever lives in the repo. | `python -m pip install -e .` → `apismoke --help` |
| **[flaky-test-detector](https://github.com/yazanus94-dot/flaky-test-detector)** | Finds unreliable tests by comparing JUnit XML reports from multiple CI runs (pytest, Maven, Jest-JUnit, Playwright, Cypress…). Separates *flaky* from *always-failing* and understands retried tests. | `python -m pip install -e .` → `flaky-detect run1.xml run2.xml …` |
| **[repo-doctor](https://github.com/yazanus94-dot/repo-doctor)** | A health check for Git repositories — score out of 100 plus prioritized findings: missing docs, non-conventional commit messages, large blobs anywhere in history, stale branches, bus factor. | `python -m pip install -e .` → `repo-doctor <path>` |

## Why standalone instead of one monorepo

Each tool has its own issues, releases, and evolution pace. Splitting them means each repo shows a single clear-purpose project instead of one mixed suite. This repository is retained as the original provenance archive (`archive/`) and landing page pointing at the maintained roots.

## Repository contents

- `archive/` — original zip archives of the three tools, kept for provenance.
- The three tool **repositories** above (each with `src/` layout, `pyproject.toml`, `tests/`, `examples/` and CI workflow).

## Reproduce the exact state of any tool

```bash
git clone https://github.com/yazanus94-dot/<tool-name>.git
cd <tool-name>
python -m pip install -e .
python -m unittest discover -s tests -v
```
