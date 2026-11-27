# Themes

Two design systems, kept as plain files so people and AI agents can apply them the same way every time:

| Theme | Mode | In one line |
|---|---|---|
| [Neon Terminal](neon-terminal/) | Dark | Signal in the dark: near-black, one hot cyan for action, neon only where it means something. |
| [Tidewater](tidewater/) | Light | Cyan, then quiet: one calm hue for every action, cool neutrals, nothing extra. |

Each one is complete on its own and has only its own mode. Together they make a light/dark pair: [baron-hines.github.io](https://baron-hines.github.io/) uses Tidewater in light mode and Neon Terminal in dark mode, and so does the home server's Forgejo.

## What a theme covers

- **Tokens:** every color, font, space step, radius, shadow or glow, as CSS custom properties.
- **Components:** buttons, form fields, status tags, cards or windows, alerts, big-number tiles, table rows, the top bar and navigation, as CSS to paste in.
- **Markup patterns:** the HTML that goes with the components.
- **Rules:** which color for which job, how to write labels, buttons and errors, layout, charts, a "do not" list, and a checklist to run before calling a screen done.

## What's in each folder

| File | For |
|---|---|
| `README.md` | People: the design philosophy and foundations. |
| `THEME.md` | Building: tokens, components, markup and rules, written to be followed literally by a person or an AI agent. |

[`examples/`](examples/) has a sample page per theme, and the [themes pages on baron-hines.github.io](https://baron-hines.github.io/projects/themes/) render every token and component live, straight from these files.

## Changing a theme

Ideas from using the themes go in [PROPOSALS.md](PROPOSALS.md) first. An accepted proposal is written into that theme's `THEME.md` (and `README.md` if it changes the philosophy), so `THEME.md` stays the single source a build follows.
