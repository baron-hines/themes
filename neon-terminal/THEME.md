# Neon Terminal theme guide

Read this whole file before you style anything. It tells you how to make a user interface look like Neon Terminal, a dark cyberpunk theme that imitates a command line.

Follow it literally. Copy the CSS and markup from this file. Do not choose colors, fonts or sizes by eye.

## Key points

- The page is near-black. One hot cyan, `#00F0FF` (called `--cyan`), marks everything interactive.
- Copy the CSS blocks below into the project unchanged. Every color, size and effect you need is already in them.
- Neon colors are for signals only. Never set a paragraph of normal text in a neon color. Normal text is `--text` or `--dim`.
- Everything is square. Do not use rounded corners anywhere.
- Status is always a bracketed word such as `[OK]` or `[FAILING]`, never a color alone.
- Neon Terminal is dark only. It has no light mode. If the task asks for one, do not invent it. Tell the user it is not defined.
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

Add this to the page head. Both fonts are free Google Fonts.

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Chakra+Petch:wght@500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap">
```

| Font | Used for |
| --- | --- |
| Chakra Petch | Page titles, headings, panel titles, buttons. Always uppercase. |
| JetBrains Mono | Everything else, including body text, inputs, tables and labels |

## Tokens

Paste this at the top of the global stylesheet.

```css
:root {
  /* Surfaces and text */
  --void: #05080A;     /* page background */
  --panel: #0B1216;    /* windows, inputs, cards */
  --line: #1B3A45;     /* borders, dividers, window title bars */
  --dim: #6FA3AD;      /* secondary text */
  --text: #C7F9FF;     /* main text */

  /* Cyan, the action color, in five strengths */
  --cyan: #00F0FF;         /* buttons, focus borders, headings, links */
  --cyan-core: #B8FBFF;    /* hover fill on primary buttons */
  --cyan-hover: #00B8C9;   /* hover on outlined actions */
  --cyan-idle: #007884;    /* decoration only, never text */
  --cyan-tint: #003B42;    /* selected or hovered row background */

  /* Signals. Each one has one meaning. */
  --magenta: #FF2BD6;  /* highlight, section accents, destructive actions */
  --green: #39FF88;    /* success, online, the $ prompt */
  --acid: #FCEE0A;     /* warning and keyboard focus */
  --red: #FF3B5C;      /* error, down, failed */

  /* Type */
  --font-display: "Chakra Petch", system-ui, sans-serif;
  --font-mono: "JetBrains Mono", ui-monospace, monospace;

  /* Space (8px grid) */
  --space-8: 8px;   --space-12: 12px; --space-16: 16px; --space-24: 24px;
  --space-32: 32px; --space-48: 48px; --space-64: 64px;

  /* Glow is the only shadow. */
  --glow-cyan: 0 0 24px rgba(0, 240, 255, 0.45);
  --glow-soft: 0 0 14px rgba(0, 240, 255, 0.35);
  --glow-panel: 0 0 24px rgba(0, 240, 255, 0.10);
}
```

### Which color to use

| Need | Use |
| --- | --- |
| Page background | `--void` |
| Window, card, input background | `--panel` |
| Borders, dividers, window title bars | `--line` |
| Normal text | `--text` |
| Secondary text, timestamps, helper text | `--dim` |
| Primary button, page title, focus border, link | `--cyan` |
| Hovered or selected table row | `--cyan-tint` background |
| Section label such as `// alerts` | `--dim` normally, `--magenta` for one accent per screen |
| Success, online, shell prompt `$` | `--green` |
| Warning | `--acid` |
| Error, down, failed | `--red` |
| Destructive action such as Purge or Delete | `--magenta` |
| Keyboard focus outline | `--acid` |
| Disabled | `--line` outline with `--dim` text |

## Components

Paste this after the tokens.

```css
body {
  margin: 0;
  background-color: var(--void);
  /* Faint scanlines. Keep them on the page background only. */
  background-image: repeating-linear-gradient(0deg, rgba(0,240,255,0.035) 0px, rgba(0,240,255,0.035) 1px, transparent 1px, transparent 4px);
  color: var(--text);
  font: 400 15px/24px var(--font-mono);
}
h1, h2, h3 { margin: 0; font-family: var(--font-display); text-transform: uppercase; }
h1 { font-size: 40px; line-height: 44px; font-weight: 700; letter-spacing: 0.02em; color: var(--cyan); text-shadow: 0 0 18px rgba(0,240,255,0.5); }
h2 { font-size: 26px; line-height: 31px; font-weight: 600; }
h3 { font-size: 18px; line-height: 23px; font-weight: 600; }
a { color: var(--cyan); text-decoration: none; }
.small { font-size: 13px; line-height: 20px; color: var(--dim); }
.label { font-size: 12px; line-height: 16px; letter-spacing: 0.12em; text-transform: uppercase; color: var(--dim); }
:focus-visible { outline: 2px solid var(--acid); outline-offset: 3px; }
* { border-radius: 0; }

/* Buttons. Height is always 44px. The primary button has two cut corners. */
.btn { height: 44px; padding: 0 24px; border: 0; background: var(--cyan); color: var(--void); font: 700 15px var(--font-display); letter-spacing: 0.08em; text-transform: uppercase; cursor: pointer;
  clip-path: polygon(0 0, calc(100% - 10px) 0, 100% 10px, 100% 100%, 10px 100%, 0 calc(100% - 10px)); }
.btn:hover { background: var(--cyan-core); }
.btn:focus-visible { clip-path: none; }  /* the cut would hide the focus outline */
.btn-secondary { background: transparent; color: var(--cyan); box-shadow: inset 0 0 0 1.5px var(--cyan), var(--glow-soft); clip-path: none; }
.btn-secondary:hover { background: var(--cyan-tint); }
.btn-danger { background: transparent; color: var(--magenta); box-shadow: inset 0 0 0 1.5px var(--magenta); clip-path: none; }
.btn-danger:hover { background: rgba(255,43,214,0.12); }
.btn:disabled, .btn-secondary:disabled, .btn-danger:disabled { background: transparent; color: var(--dim); box-shadow: inset 0 0 0 1.5px var(--line); cursor: not-allowed; }

/* Inputs. A green $ sits in front of the value. */
.field-label { display: block; margin-bottom: 6px; font-size: 13px; font-weight: 700; text-transform: uppercase; }
.field { display: flex; align-items: center; gap: 8px; height: 44px; box-sizing: border-box; padding: 0 12px; background: var(--panel); box-shadow: inset 0 0 0 1px var(--line); }
.field:focus-within { box-shadow: inset 0 0 0 1.5px var(--cyan), var(--glow-soft); }
.field .prompt { color: var(--green); }
.field input { flex: 1; min-width: 0; border: 0; outline: 0; background: transparent; color: var(--text); font: 400 14px var(--font-mono); }
input[type="checkbox"] { width: 20px; height: 20px; accent-color: var(--cyan); }

/* Status tags. Put the brackets in the text, for example [OK]. */
.tag { display: inline-flex; align-items: center; height: 24px; padding: 0 8px; font-size: 12px; font-weight: 700; box-shadow: inset 0 0 0 1px currentColor; white-space: nowrap; }
.tag-ok { color: var(--green); }
.tag-warn { color: var(--acid); }
.tag-error { color: var(--red); }
.tag-idle { color: var(--dim); }
.tag-new { background: var(--magenta); color: var(--void); box-shadow: none; }

/* Window. Use it for every card or panel. */
.window { background: var(--panel); box-shadow: inset 0 0 0 1px var(--line), var(--glow-panel); }
.window-bar { display: flex; align-items: center; justify-content: space-between; gap: 12px; min-height: 32px; padding: 0 12px; background: var(--line); font-size: 12px; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; color: var(--text); }
.window-body { padding: 16px; }

/* Warning box. The header bar is solid acid yellow. */
.warning { background: var(--panel); box-shadow: inset 0 0 0 1px var(--acid); }
.warning-bar { display: flex; align-items: center; height: 28px; padding: 0 12px; background: var(--acid); color: var(--void); font-size: 12px; font-weight: 700; letter-spacing: 0.08em; }

/* Big number tile */
.stat { display: flex; flex-direction: column; gap: 6px; padding: 16px; background: var(--panel); box-shadow: inset 0 0 0 1px var(--line); }
.stat-value { font: 700 40px/44px var(--font-display); font-variant-numeric: tabular-nums; }

/* Table rows. Use a grid and set grid-template-columns on the row. */
.row { display: grid; gap: 16px; align-items: center; min-height: 48px; padding: 0 16px; border-top: 1px solid var(--line); font-size: 14px; font-variant-numeric: tabular-nums; }
.row-head { min-height: 32px; font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--dim); border-top: 0; }
a.row { color: inherit; }
a.row:hover { background: var(--cyan-tint); }

/* Segmented progress bar. Filled cells are cyan, empty cells are --line. */
.progress { display: grid; grid-template-columns: repeat(10, 1fr); gap: 3px; }
.progress i { height: 12px; background: var(--line); }
.progress i.on { background: var(--cyan); }

/* Top bar and navigation */
.topbar { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 16px; padding: 0 32px; min-height: 56px; background: var(--panel); box-shadow: inset 0 -1px 0 var(--line); }
.brand { font: 700 18px var(--font-display); letter-spacing: 0.08em; color: var(--cyan); text-shadow: 0 0 14px rgba(0,240,255,0.5); }
.nav-link { display: inline-flex; align-items: center; height: 44px; padding: 0 12px; color: var(--dim); font-size: 13px; }
.nav-link[aria-current="page"] { color: var(--cyan); font-weight: 700; }
```

### Markup patterns

Buttons and a field:

```html
<button class="btn">Execute</button>
<button class="btn btn-secondary">Pause queue</button>
<button class="btn btn-danger">Purge dead</button>

<label class="field-label" for="host">Host</label>
<div class="field"><span class="prompt">$</span><input id="host" type="text" value="edge-07.example.net"></div>
<div class="small">Hostname or IPv4 address.</div>
```

Tags, a window and a warning:

```html
<span class="tag tag-ok">[ONLINE]</span>
<span class="tag tag-warn">[LAGGING]</span>
<span class="tag tag-error">[DOWN]</span>

<section class="window">
  <div class="window-bar"><span>Node / edge-07</span><span class="tag-ok">[ONLINE]</span></div>
  <div class="window-body">
    <h3>Edge relay</h3>
    <p class="small">region eu-west, uptime 41d</p>
  </div>
</section>

<div class="warning">
  <div class="warning-bar">WARNING</div>
  <div class="window-body">Node 09 latency is above 400 ms. Traffic may reroute.</div>
</div>
```

A section label and a table:

```html
<div class="label">// recent failures</div>

<div class="row row-head" style="grid-template-columns: 2fr 1fr 1fr 1fr">
  <span>Queue</span><span>Waiting</span><span>Oldest</span><span>State</span>
</div>
<a class="row" href="/queues/invoices" style="grid-template-columns: 2fr 1fr 1fr 1fr">
  <span style="font-weight:700">invoices</span><span>1,204</span><span>4s</span>
  <span class="tag tag-ok">[OK]</span>
</a>
```

If a table can be wider than the screen, put it in a wrapper with `overflow-x: auto`.

## Writing the words

- Page titles, headings, panel titles and buttons are uppercase. The CSS does this, so write them normally.
- Small section labels start with two slashes, for example `// jobs waiting`.
- Status words are uppercase inside square brackets, such as `[OK]`, `[WARN]`, `[FAILING]`, `[STALLED]`, `[IDLE]`.
- Log lines use lowercase levels in brackets, such as `[ok]`, `[warn]`, `[err]`. Color the bracket, not the whole line.
- A shell prompt looks like `user@host:~$ command`. The `$` is green.
- Body text reads like plain, short sentences. No exclamation marks, no emoji, no slang.
- An error says what went wrong and what to do next.

## Layout rules

- The page is a column on `--void`. Content sits in a container with `max-width: 1376px`, centered, with 32px side padding.
- Space between page sections is 24px to 48px. Panel padding is 16px to 24px.
- Put groups of items in `display: flex` or `display: grid` with `gap`. Do not space things with margins.
- A row of summary tiles uses `display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 16px`.
- Anything clickable is at least 44px tall.
- On phones everything stacks to one column. Tables scroll sideways inside their own wrapper. The page never scrolls sideways.

## Charts

- A line is `--cyan` for normal, `--acid` for warning, `--red` for error, `--dim` for idle. Stroke width is 1.5 to 2.
- Fill under a line is the same color at 15% opacity.
- Grid lines are `--line`. The zero line and axis text are `--dim`.
- Chart text uses JetBrains Mono at 11px.

## Do not

- Do not use rounded corners. Not on buttons, inputs, tags, cards or images.
- Do not put body text in `--cyan`, `--magenta`, `--green`, `--acid` or `--red`. Use them for titles, labels, tags and short values only.
- Do not use more than one glowing element per region of the screen. Glow means "look here".
- Do not put the scanline background on cards or panels. It belongs to the page background only.
- Do not use `--dim` text on a `--line` background. Use `--text` there, such as in window title bars.
- Do not use `--cyan-idle` for text. It is too dark. It is for decoration.
- Do not show status with color alone. Always include the bracketed word.
- Do not remove the focus outline. It is `--acid` so it stays visible on every neon color.
- Do not use emoji or icon fonts. Use text glyphs such as `$`, `//`, `>` and `[ ]`. If an icon is unavoidable, draw it as a 2px square-cap stroke with no fill.
- Do not add gradients other than the scanlines.

## Checklist before you finish

Answer each question. If any answer is no, fix it first.

- [ ] Are the font link, tokens block and components block all in the project?
- [ ] Does every color in the new code come from the tokens block?
- [ ] Is the page background `--void` with scanlines, and every panel `--panel`?
- [ ] Is every corner square?
- [ ] Is the main button `--cyan` with `--void` text, uppercase, 44px tall, with cut corners?
- [ ] Does every status tag contain a bracketed word?
- [ ] Is all normal text `--text` or `--dim`?
- [ ] Can you reach every button, link and input with the Tab key and see the yellow focus outline?
- [ ] Does every input have a visible label?
- [ ] At 400px wide, does the page stack to one column with no sideways page scroll?

## Source

This theme was designed as an example design system called Neon Terminal. The design system artifact is https://claude.ai/artifact/EK1CUW4r9Y61tmpBePmhuf (private to its owner). It holds the same tokens and a README. The NEON//QUEUES queue monitor screens built with it are the best working example of this theme on real screens.
