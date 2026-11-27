# Neon Terminal

**Signal in the dark.** Neon Terminal is a dark theme for command-line-flavored interfaces: near-black surfaces, one hot cyan for action, and a few neon colors that each mean one thing.

To build with it, follow [THEME.md](THEME.md). It has the tokens, the components and the rules, written to be followed literally by people and AI agents alike. This page is the why.

## Design philosophy

- **The dark is the canvas, neon is the signal.** Almost everything is near-black, deep panel blue, or pale cyan-white text. Neon only shows up where it carries meaning. If everything glows, nothing does.
- **One color means "act".** `--cyan` is for things you can click or that have focus: buttons, links, the focus border. The page title is the single exception, one per screen. Section headings and card titles stay `--text`, so cyan never lies about what's interactive.
- **Every other neon has exactly one job.** Green is success and the shell prompt. Acid yellow is warning and keyboard focus. Red is failure. Magenta is a highlight or a destructive action, once per screen.
- **Status is never color alone.** It's a bracketed word, `[ONLINE]` or `[DOWN]`, so it reads in monochrome, to a screen reader, and to someone who can't tell green from red.
- **Square, and cut.** Nothing is rounded. The primary button gets two cut corners instead of a radius, the theme's one flourish.
- **Glow means "look here".** Glow is the only shadow, and there's one glowing thing per region of the screen.
- **Texture belongs to the room, not the furniture.** Faint scanlines sit on the page background only, never on panels or cards.
- **It talks like a shell.** Section labels are comments (`// alerts`), buttons are verbs (Execute, Purge), log levels are bracketed (`[ok]`, `[warn]`, `[err]`). No exclamation marks, no emoji.
- **Monospace, but readable.** JetBrains Mono carries everything except titles. Long text gets a narrower column and more line height, because long lines of mono are hard to track.

## Foundations

| | |
|---|---|
| **Color** | Surfaces `--void`, `--panel`, `--line`. Text `--text` and `--dim`. Action `--cyan` (with hover, idle and tint strengths). Signals `--green`, `--acid`, `--red`, `--magenta`. |
| **Type** | Chakra Petch for titles, headings and buttons, uppercase. JetBrains Mono for everything else. Names and code keep their case. |
| **Space** | An 8px grid. Panels pad 16 to 24px. Sections sit 24 to 48px apart. |
| **Shape** | Square everywhere. A 10px corner cut on primary buttons. |
| **Depth** | No shadows, only glow: `--glow-cyan`, `--glow-soft`, `--glow-panel`. |
| **Icons** | None. Text glyphs instead: `$` for the prompt, `//` for labels, `[ ]` for status, `>` for navigation. |

## Where it's used

- [baron-hines.github.io](https://baron-hines.github.io/), as the dark mode. The [Neon Terminal page there](https://baron-hines.github.io/projects/themes/neon-terminal/) shows every token and component live.
- The self-hosted Forgejo on the home server, as its dark theme.

Its light counterpart is [Tidewater](../tidewater/).
