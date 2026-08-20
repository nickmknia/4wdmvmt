# 4wdmvmt GitHub Pages Site Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and publish a single-page static professional site for 4wdmvmt on GitHub Pages at the custom domain 4wdmvmt.com.

**Architecture:** Three static files at the repo root — `index.html`, `style.css`, `CNAME` — served directly by GitHub Pages from `main`. No build step, no JavaScript, no framework.

**Tech Stack:** Plain HTML5 + CSS3. GitHub Pages (branch: `main`, root).

**Spec:** `docs/superpowers/specs/2026-08-20-4wdmvmt-github-pages-design.md`

## Global Constraints

- No JavaScript, no build tooling, no CSS framework (per spec Scope).
- Single page only — no multi-page navigation (per spec Scope).
- Placeholder copy only; user edits real copy into `index.html` afterward (per spec Content).
- Style: system font stack, generous whitespace, neutral palette (near-black text on white/off-white) with one subtle accent color, single-column centered layout, responsive to mobile without a framework (per spec Design).
- Verify layout in an actual viewport (desktop + mobile width) before calling any step done — do not rely on visual inspection of source alone (per spec Testing/repo CSS guidance).

---

### Task 1: Page markup (`index.html`)

**Files:**
- Create: `index.html`

**Interfaces:**
- Produces: an `index.html` with a `<link rel="stylesheet" href="style.css">` in `<head>`, and this DOM structure inside `<body>`:
  - `<main class="page">` wrapping everything
  - `<h1>` — business name
  - `<p class="tagline">` — one-line tagline
  - `<section class="services">` containing an `<h2>Services</h2>` and a `<ul>` of `<li>` items
  - `<footer class="contact">` containing a `mailto:` link with the contact email
- Consumes: nothing (first task).

- [ ] **Step 1: Write `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>4WDMVMT</title>
  <meta name="description" content="4WDMVMT — professional consulting and services.">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main class="page">
    <h1>4WDMVMT</h1>
    <p class="tagline">Practical consulting for teams that need to move fast and get it right.</p>

    <section class="services">
      <h2>Services</h2>
      <ul>
        <li>Strategy &amp; advisory</li>
        <li>Project delivery</li>
        <li>Ongoing consulting engagements</li>
      </ul>
    </section>

    <footer class="contact">
      <p>Get in touch: <a href="mailto:nick@nickkesh.com">nick@nickkesh.com</a></p>
    </footer>
  </main>
</body>
</html>
```

- [ ] **Step 2: Verify markup renders**

Open `index.html` directly in a browser (double-click it or run `open index.html` on macOS). Confirm the heading, tagline, services list, and contact link all display, and the mailto link is clickable. There's no `style.css` yet, so it will look unstyled — that's expected at this step.

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "Add site markup for 4wdmvmt landing page"
```

---

### Task 2: Styling (`style.css`)

**Files:**
- Create: `style.css`

**Interfaces:**
- Consumes: the class names from Task 1 — `.page`, `.tagline`, `.services`, `.contact`, plus bare `h1`, `h2`, `ul`, `li`, `a`.
- Produces: nothing consumed by later tasks.

- [ ] **Step 1: Write `style.css`**

```css
:root {
  --color-text: #1a1a1a;
  --color-bg: #fafafa;
  --color-accent: #2a6f4c;
  --color-muted: #555;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  background: var(--color-bg);
  color: var(--color-text);
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  line-height: 1.5;
}

.page {
  max-width: 640px;
  margin: 0 auto;
  padding: 4rem 1.5rem;
}

h1 {
  font-size: 2.25rem;
  letter-spacing: 0.02em;
  margin: 0 0 0.75rem;
}

.tagline {
  font-size: 1.125rem;
  color: var(--color-muted);
  margin: 0 0 3rem;
}

h2 {
  font-size: 1rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--color-muted);
  margin: 0 0 1rem;
}

.services ul {
  list-style: none;
  margin: 0 0 3rem;
  padding: 0;
}

.services li {
  padding: 0.5rem 0;
  border-bottom: 1px solid #e0e0e0;
}

.contact a {
  color: var(--color-accent);
  text-decoration: none;
  font-weight: 600;
}

.contact a:hover {
  text-decoration: underline;
}

@media (max-width: 480px) {
  .page {
    padding: 2.5rem 1.25rem;
  }

  h1 {
    font-size: 1.75rem;
  }
}
```

- [ ] **Step 2: Verify styling in an actual viewport**

Run `open index.html` (macOS) to load it in the default browser. Resize the browser window down to a mobile width (~375px, e.g. via the browser's device toolbar/responsive mode) and confirm:
- Content stays centered and readable at desktop width.
- At mobile width, padding shrinks and the heading resizes per the `@media` rule — no horizontal scrollbar, no overflow.
- The services list and contact link remain legible and tappable-sized on mobile.

If anything overflows or misaligns, fix `style.css` and re-check before moving on — per repo guidance, don't claim the fix works without checking an actual viewport, and if two fix attempts don't render correctly, stop and flag it rather than keep patching.

- [ ] **Step 3: Commit**

```bash
git add style.css
git commit -m "Add minimal styling for 4wdmvmt landing page"
```

---

### Task 3: Custom domain (`CNAME`) and GitHub Pages publish

**Files:**
- Create: `CNAME`

**Interfaces:**
- Consumes: nothing.
- Produces: nothing (final task).

- [ ] **Step 1: Write `CNAME`**

```
4wdmvmt.com
```

(No trailing content, no `http://` prefix — GitHub Pages expects just the bare domain.)

- [ ] **Step 2: Commit**

```bash
git add CNAME
git commit -m "Add CNAME for custom domain 4wdmvmt.com"
```

- [ ] **Step 3: Push to GitHub**

```bash
git push -u origin main
```

- [ ] **Step 4: Enable GitHub Pages (manual, one-time)**

In the GitHub repo (`nickmknia/4wdmvmt`) go to Settings → Pages, set Source to the `main` branch / root directory, and save. GitHub will detect the `CNAME` file and pre-fill the custom domain field.

- [ ] **Step 5: Point DNS at GitHub Pages (manual, user-owned step)**

At your domain registrar for 4wdmvmt.com, add:
- Four `A` records at the apex (`@`) pointing to GitHub Pages' IPs: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- (Optional) a `CNAME` record for `www` pointing to `nickmknia.github.io`, if you want `www.4wdmvmt.com` to work too

This step is outside this repo and not something the assistant performs — do it directly with your registrar.

- [ ] **Step 6: Verify live site**

Once DNS propagates (can take up to a few hours) and GitHub Pages shows the domain as verified with HTTPS enforced, visit `https://4wdmvmt.com` and confirm the page loads with the same content/styling verified in Tasks 1–2.
