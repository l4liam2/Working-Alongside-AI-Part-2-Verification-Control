# Marnwood Packaging Co.

A static marketing site for **Marnwood Packaging Co.**, a fictional Hamilton, Ontario packaging
wholesaler.

Marnwood Packaging Co. is a fictional company created for educational use. Nothing on this site describes a
real business. Every page carries `<meta name="robots" content="noindex, nofollow">` and a footer disclaimer.

## Stack

Plain HTML and CSS. No JavaScript, no build step, no dependencies. One stylesheet (`style.css`).
`contact.html` is form markup only and transmits nothing.

Imagery lives in `assets/` — original SVG for the logo, the four product line drawings and the
certification badges, plus three openly licensed photographs in `assets/img/`. Sources and licences are
in [CREDITS.md](CREDITS.md).

## Deploying to GitHub Pages

Settings → Pages → Source: **Deploy from a branch** → Branch: **main**, folder: **/ (root)**.

`.nojekyll` is present so files are served as-is.

## Local preview

```
python3 -m http.server 8000
```

Then open http://localhost:8000
