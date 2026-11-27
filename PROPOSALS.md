# Proposals

Changes suggested from using the themes on real pages, not yet decided. When one is accepted, it goes into the theme's `THEME.md` (and `README.md` if it changes the philosophy) and is ticked here. When one is turned down, it's struck out here with the reason.

Most of these came from [baron-hines.github.io](https://baron-hines.github.io/), the first content site built on both themes. The themes were first designed for dashboards and tools, so most of the gaps are about pages that are mostly text.

## Accepted

- [x] **Neon Terminal: reading pages.** A `.reading` column at most `68ch` wide with 26px line height for paragraphs, lists and quotes. (2026-11-27)
- [x] **Neon Terminal: names and code keep their case.** Uppercase headings and buttons leave lowercase names and code alone, through `<code>` or `.keep-case`. (2026-11-27)
- [x] **Neon Terminal: cyan means clickable.** Section headings and card titles are `--text`. The page title is the only cyan heading. The token comment no longer lists headings under `--cyan`. (2026-11-27)

## Open

### Both themes

- [ ] **Article components.** Neither guide covers what a written page needs: tables in running text, blockquotes, code blocks, inline code, ordered lists, images with captions. Each site invents its own. For Neon Terminal, a code block could reuse the window pattern: a 32px `--line` title bar naming the language, over a `--panel` body.
- [ ] **A reading layout for Tidewater too.** Its layout rules only cover the 1376px dashboard container. A reading column (about 70 characters, IBM Plex Sans at 16/25) would match Neon Terminal's `.reading`.
- [ ] **Bar charts.** The chart rules cover lines and fills only. Proposed: bars use the line color at 15% (Neon Terminal) or 12% (Tidewater) fill with a solid 1.5px outline, and the one bar that matters (a winner, a current value) may be solid.

### Neon Terminal

- [ ] **Plain tags are `--dim`.** A topic tag like `[litellm]` in a cyan shade looks like a link. Status tags keep their signal colors. A tag that is a link may be cyan.
- [ ] **Glow on lists of cards only on hover or focus.** A list of cards that all carry `--glow-panel` breaks "one glowing element per region". Proposed: cards in a list glow on hover and focus only; a single window on its own keeps its glow.
- [ ] **Inline navigation height.** "Anything clickable is at least 44px tall" is right for tools, but a text link inside a paragraph can't be. Proposed: the rule applies to buttons, nav links and controls, not to links in running text.

### Tidewater

- [ ] **Card titles that are links.** The guide makes links `--primary` but doesn't say what a clickable card's title looks like. Proposed: `--ink` title, with the whole card as the click target and a `--primary` border on hover.
