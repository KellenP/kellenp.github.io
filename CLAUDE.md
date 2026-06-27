# CLAUDE.md — Kellen Poole portfolio (the AI opportunity engine)

Guidance for AI assistants working in this repo. Read this first.

## What this is

A **static, hand-coded portfolio site** served by GitHub Pages at
`https://kellenp.github.io`. It is a personal "builder portfolio": a hub page
that links to six self-directed project case studies, each with a live demo, a
short STAR narrative, and an honest status.

There is **no framework, no build step, no package manager, no JavaScript app
code**. Just HTML files + one shared stylesheet + image/video assets. Edits are
the files you see; what's committed is what ships.

### Why "the AI opportunity engine"

This portfolio exists to win Kellen an **AI-focused builder / product role**. Treat
it as a living sales asset, not a finished artifact. When you work here, your job
isn't only to do the literal task — it's to spot and surface opportunities that
make the portfolio land harder for that goal:

- **Sharpen the narrative** — clearer problem framing, tighter STAR, less filler.
- **Strengthen the proof** — working demos, passing-test claims, honest limits.
- **Keep it credible** — every status label and number must be true, not aspirational.
- **Mirror the target role** — copy should speak to operational/AI builder hiring.

If you notice a weak claim, a dead link, a demo that no longer works, or an obvious
gap, **flag it** even if it's outside the literal ask. That is the point of this doc.

## Repository layout

```
index.html                 Hub: hero + "About me" + 6 project cards + demo note
shopflow.html              Case study 01 — ShopFlow-Orchestrator (agentic AI, resilience)
content-operator-os.html   Case study 02 — Content Operator OS (full-stack ops dashboard)
nightshift-manager.html    Case study 03 — NightShift Manager (AI job verification)
draincheck.html            Case study 04 — DrainCheck (Gmail API, OAuth, serverless)
resume-shock.html          Case study 05 — Resume Shock (client-side PDF → web page)
kitsmith.html              Case study 06 — KitSmith (Windows desktop audio app)
styles.css                 The entire design system (shared by every page)
kellen.jpg                 Profile photo: hero avatar, topbar avatar, favicon, OG image
shopflow-demo.mp4          Embedded showcase video on shopflow.html
shopflow-demo-poster.jpg   Poster frame for that video
.gitignore                 Excludes build artifacts of the *other* repos (node_modules, etc.)
```

Each project also lives in its **own separate GitHub repo** under `github.com/kellenp/*`
(e.g. `kellenp/shopflow-orchestrator`) and most have a Netlify live demo
(`*-kp.netlify.app`). Those are linked from here but **not part of this repo** —
this repo is only the marketing site.

## How to work in it

- **No build, no run command.** To preview, open the `.html` file in a browser or
  serve the folder statically (e.g. `python3 -m http.server`). There are no tests,
  no linters, no CI config in this repo.
- **Deploy = push to GitHub Pages.** Whatever is on the published branch goes live.
  Develop on the branch you were assigned; commit with clear messages; push only
  when changes are complete.
- **One stylesheet rules everything.** All visual changes go through `styles.css`.
  Don't add per-page `<style>` blocks unless it's a genuinely one-off layout; even
  then, prefer extending the design system. Inline `style="…"` is used sparingly
  for true one-offs (see existing pages) — match that restraint.
- **Pages are independent HTML.** There's no templating/include system, so shared
  chrome (topbar, footer, `<head>` font links) is **duplicated** across files. If
  you change the topbar or font stack, change it in **every** page for consistency.

## Conventions (match these exactly)

**Page skeleton.** Every page has: `<meta theme-color="#0f6e56">`, the same
Google Fonts `<link>` (Source Serif 4 + Spline Sans + Spline Sans Mono), then
`styles.css`. A sticky `.topbar` (brand left, link right), a `.wrap` container
(`max-width: 760px`), and a centered `footer`.

**Design system / tokens.** Defined as CSS custom properties in `:root` with a
full `prefers-color-scheme: dark` override. Aesthetic is "editorial-tech": warm
paper background, deep-forest-green accent (`--accent: #0f6e56`). Always use the
tokens (`var(--ink)`, `var(--muted)`, `var(--accent)`, `var(--line)`, …) — never
hard-code colors.

**Typography roles.**
- `Source Serif 4` — display serif for `h1`, `h2`, `.proj-name`, brand, big glyphs.
- `Spline Sans` — body text.
- `Spline Sans Mono` — eyebrows, labels, pills, dates, terminal blocks (the
  "technical" voice).

**Reusable components in `styles.css`** (prefer these over new markup):
`.hero`, `.eyebrow`, `.lede`, `.label` (section kicker), `.status` /
`.status.amber` (status pill with `.dot`), `.actions` + `.btn`/`.btn-primary`/
`.btn-ghost`, `.steps` (numbered "how it works"), `.cards`/`.card`, `.star`/
`.star-row` (the signature STAR treatment), `.pills`/`.pill`, `.callout` /
`.callout.amber` (status & limitations), `.honest` (italic disclaimer), `.term`
(monospace output block), and on the hub: `.hub-grid`/`.proj`/`.mini`.

**Case-study page structure** (the established template — follow it):
1. `.hero` — eyebrow, `h1` (project name), `.lede`, a `.status` pill, a
   `.started` line, `.actions` (primary = live demo/output, ghost = source).
2. Section: **The problem** (`.label` + `.prose`).
3. Section: **How it works** (`.steps`).
4. Section: **The story · STAR** (`.star` with S/T/A/R rows).
5. Optional: a demo/video or `#verified` / `#download` anchored section.
6. Section: **Built with** (`.pills`).
7. Section: **Status & honest limitations** (`.callout` + `.honest`).

**Motion.** Elements fade in via the `.reveal` class (staggered by `:nth-child`).
Add `reveal` to top-level hero/section children for the load animation;
`prefers-reduced-motion` is already respected.

**Links.** External links use `target="_blank" rel="noopener"` and an `↗` glyph;
internal nav uses `←`/`→`; download/anchor jumps use `↓`. Topbar "back" link on
case studies points to `/` ("← All projects"); on the hub it's the contact email.

## The honesty rule (non-negotiable)

This portfolio's credibility is its whole value. The site explicitly promises
demos run on **fictional sample data** and that status labels are **"accurate,
not aspirational."** Therefore:

- Never invent or inflate metrics, test counts, or capabilities. Numbers like
  "30/30 tests pass" must reflect reality in the linked repo.
- Keep the `.honest` disclaimers and "self-directed, AI-assisted" framing intact.
- Don't claim something is "live," "deployed," or "shipped" unless it is. The
  status taxonomy in use is roughly: **live demo / live output / desktop download /
  verified output** — pick the truthful one.
- If a change would make a claim untrue, fix the claim, don't hide it.

## Identity & contact (keep consistent)

- Name **Kellen Poole**; GitHub **github.com/kellenp**; site **kellenp.github.io**.
- Contact email appears in the topbar, hero CTA, and footer — when it changes,
  update **all** occurrences (note: the hub currently uses
  `kellenpbusiness@gmail.com`).
- Profile image is `kellen.jpg`, reused as avatar, favicon, and social/OG image.

## Commit style

Recent history uses descriptive, outcome-focused subject lines, often prefixed
with the area of work (e.g. `portfolio-audit:`). Mirror that: say what changed
and why it's better, not just "update index.html."
