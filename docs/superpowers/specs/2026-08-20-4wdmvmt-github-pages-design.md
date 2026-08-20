# 4wdmvmt GitHub Pages Site — Design

## Purpose

A simple, professional single-page website for 4wdmvmt (a consulting/services
business), hosted on GitHub Pages at the custom domain 4wdmvmt.com. Lists
basic business information: name, tagline, services, and contact info.

## Scope

- Single static HTML page, no build tooling, no JavaScript.
- Hosted via GitHub Pages from the `main` branch root.
- Custom domain (4wdmvmt.com) via a `CNAME` file; DNS records managed by the
  user outside this repo.

Out of scope: multi-page navigation, CMS/build pipeline, analytics, contact
forms, blog content (that's `mysite/`'s job).

## File structure

```
index.html      Single page: business name, tagline, services list, contact
style.css       Minimal/clean styling, responsive
CNAME           Contains "4wdmvmt.com"
```

## Hosting

- GitHub Pages source: `main` branch, root directory.
- No build step — pushing to `main` publishes directly.
- User enables Pages in repo Settings → Pages, and separately configures DNS
  at their registrar to point 4wdmvmt.com at GitHub Pages. DNS setup is not
  performed as part of this work.

## Design

- Typography-led, minimal/clean aesthetic: system font stack, generous
  whitespace, neutral palette (near-black text on white/off-white background)
  with one subtle accent color.
- Single-column, centered layout, responsive down to mobile widths without a
  CSS framework.

## Content

Placeholder copy (user edits directly in `index.html` afterward):

- Business name: 4WDMVMT
- Tagline: one-line description of consulting/services focus
- Services: three placeholder bullet items
- Contact: user's email

## Testing / verification

- Open `index.html` directly in a browser and at a mobile viewport width to
  confirm layout holds up (per this repo's CSS/mobile guidance: test in an
  actual viewport before calling it done).
- No automated tests — static content only.
