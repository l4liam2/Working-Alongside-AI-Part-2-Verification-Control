# Working Alongside AI — Part 2: Verification & Control

Activity 2. A static marketing site for **Marnwood Packaging Co.**, a fictional Hamilton, Ontario packaging
wholesaler, built as a verification exercise. The site contains deliberately planted inconsistencies,
contradictions and omissions.

Marnwood Packaging Co. is a fictional company created for educational use. Nothing on this site describes a
real business. Every page carries `<meta name="robots" content="noindex, nofollow">` and a footer disclaimer.

## Facilitators

Planted traps are documented in [TRAPS.md](TRAPS.md) — what's planted, where it lives, and what a
verification failure looks like for each. Nothing on the site links to that file.

Note that `TRAPS.md` is still publicly fetchable if this repo is public or the site is deployed as-is.

## Stack

Plain HTML and CSS. No JavaScript, no build step, no dependencies. One stylesheet (`style.css`).
`contact.html` is form markup only and transmits nothing.

## Deploying to GitHub Pages

Settings → Pages → Source: **Deploy from a branch** → Branch: **main**, folder: **/ (root)**.

`.nojekyll` is present so files are served as-is.

## Local preview

```
python3 -m http.server 8000
```

Then open http://localhost:8000
