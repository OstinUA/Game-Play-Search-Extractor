# Contributing to Game Store Link Extractor

Thanks for taking the time to contribute. You’re helping make this extension more reliable for ASO folks, researchers, and devs who need fast, clean app-link extraction at scale.

We welcome bug fixes, UX improvements, selector hardening, better docs, and general cleanup PRs.

## Introduction

This project is intentionally lean: no backend, no frameworks, just a focused MV3 extension and a deterministic extraction pipeline.

That means every contribution should aim for:

- predictable behavior on both supported stores,
- minimal complexity overhead,
- maintainable selector/extraction logic,
- clean and auditable diffs.

## I Have a Question

Please **do not** open Issues for usage/support questions.

Issues are reserved for actionable engineering tasks (bugs, enhancements, refactors). For Q&A and help:

- Use **GitHub Discussions** (preferred, if enabled), or
- Ask in relevant developer communities and include a link to this repo.

When asking a question, include:

- what page you tested,
- what you expected,
- what actually happened,
- your browser and OS.

## Reporting Bugs

Before opening a bug report:

1. Search existing Issues to avoid duplicates.
2. Re-test on the latest `main` branch.
3. Validate on a clean Chrome profile if possible.

### Bug Report Checklist

Include all of the following:

- **Environment**:
  - OS version
  - Chrome version
  - Extension version (from `manifest.json`)
- **Target store**: Google Play or Apple App Store
- **URL tested**: exact page URL
- **Steps to reproduce**: deterministic sequence
- **Expected behavior**
- **Actual behavior**
- **Artifacts**: screenshots, console errors, short screen recording if relevant

A high-signal bug report helps us patch root cause faster.

## Suggesting Enhancements

Feature requests are welcome when they solve a real workflow problem.

Your proposal should include:

- **Problem statement**: what pain point exists now?
- **Proposed solution**: what behavior should be added/changed?
- **Use cases**: who benefits and in what scenario?
- **Scope estimate**: small patch vs larger refactor
- **Risks/trade-offs**: performance, selector fragility, UI complexity, permission expansion

If the enhancement changes extraction behavior, include examples of expected output URLs.

## Local Development Setup

### 1) Fork and clone

```bash
git clone https://github.com/<your-username>/Game-Play-Search-Extractor.git
cd Game-Play-Search-Extractor
```

### 2) Create a branch

```bash
git checkout -b feature/short-description
```

### 3) Load extension in Chrome

1. Open `chrome://extensions/`
2. Enable **Developer mode**
3. Click **Load unpacked**
4. Select your local repo directory

### 4) Make your changes

Typical files to touch:

- `popup.js` for extraction logic and runtime behavior
- `popup.html` for popup UI/UX
- `manifest.json` for permission or metadata updates
- `README.md` for docs sync

### 5) Validate manually

- test Google Play extraction flow,
- test Apple extraction flow,
- verify dedupe and canonical URL formatting,
- verify unsupported domain state.

## Pull Request Process

### Branch naming

Use descriptive branch names:

- `feature/<short-name>`
- `bugfix/<short-name>`
- `chore/<short-name>`
- `docs/<short-name>`

Examples:

- `feature/apple-selector-hardening`
- `bugfix/google-play-footer-filter`
- `docs/readme-rewrite`

### Commit messages

Use **Conventional Commits**:

- `feat: add canonicalization for app store ids`
- `fix: prevent duplicate links from repeated cards`
- `docs: rewrite readme getting started section`
- `chore: bump extension version to 3.2`

### Keep branch synced

Before opening PR:

```bash
git fetch origin
git rebase origin/main
```

### PR description requirements

Your PR should include:

- concise summary of what changed,
- why the change is needed,
- linked Issue(s) (e.g. `Closes #42`),
- before/after behavior notes,
- screenshots for popup/UI changes,
- manual test evidence for both stores.

Small, focused PRs get reviewed and merged faster.

## Styleguides

Keep implementation pragmatic and easy to diff.

### JavaScript

- Stick to modern ES6+ syntax.
- Prefer pure helper logic and clear naming.
- Avoid unnecessary abstractions for tiny codepaths.
- Fail safe on malformed URLs.

### HTML/CSS

- Keep popup markup simple and readable.
- Avoid overengineering UI for this extension’s scope.

### Formatting and linting

There is currently no enforced linter/formatter config in-repo.

Until tooling is added:

- keep style consistent with existing files,
- avoid unrelated reformatting,
- keep whitespace/noise diffs minimal.

If you propose adding ESLint/Prettier, open a dedicated PR.

## Testing

New behavior should ship with validation evidence.

At minimum, run manual checks for:

1. Google Play extraction
2. Apple App Store extraction
3. Unsupported domain handling
4. URL deduplication and canonicalization

Optional metadata sanity check:

```bash
python -m json.tool manifest.json > /dev/null
```

If your PR changes selectors or URL normalization logic, include concrete tested URLs in the PR body.

## Code Review Process

- Maintainers review incoming PRs for correctness, scope, and regressions.
- At least one maintainer approval is expected before merge.
- You may be asked to split oversized PRs into smaller logical chunks.
- Address review comments with follow-up commits or a focused squash.
- Be responsive and keep discussion technical and reproducible.

Once approved, maintainers will handle merge strategy and release timing.

Thanks again for contributing and helping keep this tool sharp.
