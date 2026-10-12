# Tidewater theme guide

Read this whole file before you style anything. It tells you how to make a user interface look like Tidewater, a calm light theme built on one cyan color.

Follow it literally. Copy the CSS and markup from this file. Do not choose colors, fonts or sizes by eye.

## Key points

- Cyan is the only brand color. The main action color is `#0E7490` (called `--primary`) with white text.
- Copy the CSS blocks below into the project unchanged. Every color, size and radius you need is already in them.
- Never show status with color alone. Every status tag contains a word such as "Healthy" or "Failing".
- Tidewater is light only. It has no dark mode. If the task asks for one, do not invent it. Tell the user it is not defined.
- If something you need is not in this file, pick the closest existing token or component. Do not add new colors.

## How to apply the theme

Do these steps in order.

1. Add the font link from the next section to the page head.
2. Paste the tokens block into the global stylesheet.
3. Paste the components block after it.
4. Build each screen with the class names and markup patterns shown here.
5. Run the checklist at the bottom before you say you are done.

If the project already uses a CSS framework (Tailwind, a component library, CSS modules), keep using it, but give it the exact values from the tokens block. The values matter, the class names do not.

## Fonts

Add this to the page head. All three fonts are free Google Fonts.

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Sora:wght@500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap">
```

| Font | Used for |
| --- | --- |
| Sora | Page titles, headings, card titles, big numbers |
| IBM Plex Sans | Everything a person reads, buttons, tables, forms |
| IBM Plex Mono | Small uppercase labels and code only |

## Tokens

Paste this at the top of the global stylesheet.

```css
:root {
  /* Cyan ramp. 700 is the brand color. */
  --cyan-50:  #ECFEFF;
  --cyan-100: #CFFAFE;
  --cyan-200: #A5F3FC;
  --cyan-300: #67E8F9;
  --cyan-400: #22D3EE;
  --cyan-500: #06B6D4;
  --cyan-600: #0891B2;
  --cyan-700: #0E7490;
  --cyan-800: #155E75;
  --cyan-900: #164E63;
  --cyan-950: #083344;

  --primary: var(--cyan-700);
  --primary-hover: var(--cyan-800);
  --focus-ring: var(--cyan-600);

  /* Neutrals. They lean cool, so never use pure grey or pure white for the page. */
  --ground: #F7FBFC;   /* page background */
  --surface: #FFFFFF;  /* cards, inputs, tables */
  --border: #D5E4E8;   /* hairlines and input borders */
  --muted: #4A6670;    /* secondary text */
  --ink: #0B2530;      /* main text */

  /* Status */
  --positive: #15803D;
  --caution: #B45309;
  --critical: #B91C1C;
  --positive-tint: #DCFCE7;
  --caution-tint: #FEF3C7;
  --critical-tint: #FEE2E2;
  --idle-tint: #E6EFF2;

  /* Type */
  --font-display: "Sora", system-ui, sans-serif;
  --font-sans: "IBM Plex Sans", system-ui, sans-serif;
  --font-mono: "IBM Plex Mono", ui-monospace, monospace;

  /* Space (4px base) */
  --space-4: 4px;   --space-8: 8px;   --space-12: 12px; --space-16: 16px;
  --space-24: 24px; --space-32: 32px; --space-48: 48px; --space-64: 64px;

  /* Shape and depth */
  --radius-input: 6px;    /* buttons and inputs */
  --radius-card: 12px;    /* cards, panels, alerts */
  --radius-pill: 999px;   /* tags */
  --shadow-raised: 0 1px 2px rgba(8, 51, 68, 0.10);
  --shadow-floating: 0 12px 28px -8px rgba(8, 51, 68, 0.28);
}
```

### Which color to use

| Need | Use |
| --- | --- |
| Primary button, links, active nav, chart line | `--primary` |
| Hover on a primary button | `--primary-hover` |
| Page background | `--ground` |
| Card, table or input background | `--surface` |
| Lines between rows, input borders | `--border` |
| Normal text | `--ink` |
| Secondary text, captions, helper text | `--muted` |
| Success | `--positive` text on `--positive-tint` |
| Warning | `--caution` text on `--caution-tint` |
| Error or destructive action | `--critical` text on `--critical-tint` |
| Idle or inactive | `--muted` text on `--idle-tint` |
| Faint highlight, hovered table row | `--cyan-50` |
| Info tag background | `--cyan-100` with `--cyan-900` text |

The lighter cyans (300, 400, 500) are for charts and decoration only. They are too light for text.

## Components

Paste this after the tokens.

```css
body { margin: 0; background: var(--ground); color: var(--ink); font: 400 16px/25px var(--font-sans); }
h1, h2, h3 { margin: 0; font-family: var(--font-display); font-weight: 600; }
h1 { font-size: 40px; line-height: 44px; letter-spacing: -0.02em; }
h2 { font-size: 28px; line-height: 34px; letter-spacing: -0.01em; }
h3 { font-size: 20px; line-height: 26px; }
a { color: var(--primary); text-decoration: none; }
.small { font-size: 13px; line-height: 20px; color: var(--muted); }
.label { font: 500 12px/20px var(--font-mono); letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); }
:focus-visible { outline: 2px solid var(--focus-ring); outline-offset: 3px; }

/* Buttons. Height is always 44px. */
.btn { height: 44px; padding: 0 24px; border: 0; border-radius: var(--radius-input); background: var(--primary); color: #fff; font: 600 15px var(--font-sans); cursor: pointer; }
.btn:hover { background: var(--primary-hover); }
.btn-secondary { background: var(--surface); color: var(--primary); box-shadow: inset 0 0 0 1.5px var(--primary); }
.btn-secondary:hover { background: var(--cyan-50); }
.btn-danger { background: var(--surface); color: var(--critical); box-shadow: inset 0 0 0 1.5px var(--critical); }
.btn-danger:hover { background: var(--critical-tint); }
.btn-ghost { background: transparent; color: var(--primary); padding: 0 16px; }
.btn-ghost:hover { background: var(--cyan-50); }
.btn:disabled, .btn-secondary:disabled, .btn-danger:disabled { background: var(--border); color: var(--muted); box-shadow: none; cursor: not-allowed; }

/* Form fields */
.field-label { display: block; margin-bottom: 6px; font-size: 14px; font-weight: 600; }
.input { width: 100%; height: 44px; box-sizing: border-box; padding: 0 12px; border: 1.5px solid var(--border); border-radius: var(--radius-input); background: var(--surface); color: var(--ink); font: 400 16px var(--font-sans); }
.input:focus { outline: 0; border-color: var(--primary); box-shadow: 0 0 0 3px var(--cyan-200); }
input[type="checkbox"] { width: 20px; height: 20px; accent-color: var(--primary); }

/* Tags. Always put a word inside. */
.tag { display: inline-flex; align-items: center; height: 24px; padding: 0 10px; border-radius: var(--radius-pill); font-size: 13px; font-weight: 600; white-space: nowrap; }
.tag-ok       { background: var(--positive-tint); color: var(--positive); }
.tag-warn     { background: var(--caution-tint);  color: var(--caution); }
.tag-error    { background: var(--critical-tint); color: var(--critical); }
.tag-idle     { background: var(--idle-tint);     color: var(--muted); }
.tag-info     { background: var(--cyan-100);      color: var(--cyan-900); }
.tag-selected { background: var(--primary);       color: #fff; }

/* Card */
.card { padding: 24px; border-radius: var(--radius-card); background: var(--surface); box-shadow: var(--shadow-raised), inset 0 0 0 1px var(--border); }
.card-floating { box-shadow: var(--shadow-floating), inset 0 0 0 1px var(--border); }

/* Alert */
.alert { display: flex; gap: 12px; padding: 16px; border-radius: var(--radius-card); background: var(--cyan-50); box-shadow: inset 0 0 0 1px var(--cyan-200); }
.alert-error { background: #FEF2F2; box-shadow: inset 0 0 0 1px #FECACA; }

/* Big number tile */
.stat { display: flex; flex-direction: column; gap: 8px; padding: 24px; border-radius: var(--radius-card); background: var(--surface); box-shadow: var(--shadow-raised), inset 0 0 0 1px var(--border); }
.stat-value { font: 600 40px/44px var(--font-display); letter-spacing: -0.02em; font-variant-numeric: tabular-nums; }

/* Table rows. Use a grid and set grid-template-columns on the row. */
.row { display: grid; gap: 16px; align-items: center; min-height: 52px; padding: 0 24px; border-top: 1px solid var(--border); font-variant-numeric: tabular-nums; }
.row-head { min-height: 36px; font: 500 12px var(--font-mono); letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); border-top: 0; }
a.row { color: inherit; }
a.row:hover { background: var(--cyan-50); }

/* Top bar and navigation */
.topbar { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 16px; padding: 0 32px; min-height: 64px; background: var(--surface); box-shadow: inset 0 -1px 0 var(--border); }
.nav-link { display: inline-flex; align-items: center; height: 64px; padding: 0 12px; color: var(--muted); font-size: 15px; }
.nav-link[aria-current="page"] { color: var(--primary); font-weight: 600; box-shadow: inset 0 -3px 0 var(--primary); }
```

### Markup patterns

Buttons and a field:

```html
<button class="btn">Create project</button>
<button class="btn btn-secondary">Pause all</button>
<button class="btn btn-danger">Purge dead</button>

<label class="field-label" for="name">Project name</label>
<input class="input" id="name" type="text">
<div class="small">Shown to everyone on the team.</div>
```

A status tag, a card and an alert:

```html
<span class="tag tag-ok">Healthy</span>
<span class="tag tag-warn">Slow</span>
<span class="tag tag-error">Failing</span>

<section class="card">
  <h3>Harbor redesign</h3>
  <p class="small">A short description, two lines at most.</p>
</section>

<div class="alert alert-error">
  <div>
    <strong>Upload failed</strong>
    <div>The file is over the size limit. Try a smaller one.</div>
  </div>
</div>
```

A table:

```html
<div class="row row-head" style="grid-template-columns: 2fr 1fr 1fr 1fr">
  <span>Queue</span><span>Waiting</span><span>Oldest</span><span>State</span>
</div>
<a class="row" href="/queues/invoices" style="grid-template-columns: 2fr 1fr 1fr 1fr">
  <span style="font-weight:600">invoices</span><span>1,204</span><span>4s</span>
  <span class="tag tag-ok">Healthy</span>
</a>
```

If a table can be wider than the screen, put it in a wrapper with `overflow-x: auto`.

## Layout rules

- The page is a column on `--ground`. Content sits in a container with `max-width: 1376px`, centered, with 32px side padding.
- Space between page sections is 32px to 48px. Space between cards is 16px to 24px. Card padding is 24px.
- Put groups of items in `display: flex` or `display: grid` with `gap`. Do not space things with margins.
- A row of summary tiles uses `display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px`.
- Anything clickable is at least 44px tall.
- On phones everything stacks to one column. Tables scroll sideways inside their own wrapper. The page never scrolls sideways.

## Charts

- Line color is `--primary`. Fill under the line is `rgba(14, 116, 144, 0.12)`.
- Use `--caution` for a line or bar that is in a warning state and `--critical` for one in an error state.
- Grid lines are `--border`. The zero line and axis text are `--muted`.
- Use stroke width 2 and round line joins.

## Writing the words

- Sentence case everywhere. Only the small mono labels are uppercase.
- A button says what happens: "Create project", "Retry failed". Never "Submit" or "OK".
- An error says what went wrong and what to do next.
- No exclamation marks. No emoji.

## Do not

- Do not add colors that are not in the tokens block.
- Do not use white text on `--cyan-300`, `--cyan-400`, `--cyan-500` or `--cyan-600`. It fails the contrast test. White text is only for `--cyan-700` and darker.
- Do not use gradients, glows or neon effects. They belong to a different theme.
- Do not use sharp corners on cards or buttons.
- Do not remove the focus outline.
- Do not use red and green as the only difference between two things. Always add a word.
- Do not use icon fonts or emoji. Icons are inline SVG, 20px, 2px stroke, round caps, no fill, colored like the text beside them.

## Checklist before you finish

Answer each question. If any answer is no, fix it first.

- [ ] Are the font link, tokens block and components block all in the project?
- [ ] Does every color in the new code come from the tokens block?
- [ ] Is the main button `--primary` with white text and 44px tall?
- [ ] Does every status tag contain a word?
- [ ] Can you reach every button, link and input with the Tab key and see the focus outline?
- [ ] Does every input have a visible label?
- [ ] Is body text `--ink` or `--muted`, and never a cyan lighter than 700?
- [ ] At 400px wide, does the page stack to one column with no sideways page scroll?

## Source

This theme was designed as an example design system called Tidewater. The design system artifact is https://claude.ai/artifact/VRrFRKw8EzXqia9oDtZgk8 (private to its owner). It holds the same tokens and a README. The Queuewatch queue monitor screens built with it are the best working example of this theme on real screens.
