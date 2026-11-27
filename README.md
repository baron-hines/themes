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

1. On a branch, add the idea to **Open** in `PROPOSALS.md`: what's wrong, what it would change, and where it was found.
2. Once it's decided:
   - **Accepted:** write it into `THEME.md` everywhere it applies: the tokens or components CSS, the color table, Writing the words, Layout rules, Do not, and a checklist question if it's something a builder could miss. Update `README.md` too if it changes the philosophy. Move the proposal to **Accepted**, ticked and dated.
   - **Turned down:** strike it out in `PROPOSALS.md` with the reason, so it isn't proposed again.
3. Open a PR. Merge with a merge commit or a squash; either works for the site's submodule, which follows `main`.
4. Projects that use the theme pick the change up on their own schedule. For baron-hines.github.io, that's a submodule bump ([its README](https://github.com/baron-hines/baron-hines.github.io#updating-a-theme) has the steps), and a matching change to its `src/styles/theme.css` if the site's own look is affected.

Small fixes that change no rule, such as typos or a broken link, can skip the proposal.

## Adding a theme

1. Create a folder named for the theme in lowercase with hyphens, for example `harbor-light/`.
2. Add a `README.md`: one bold line that sums up the theme, then **Design philosophy**, **Foundations** and **Where it's used**, like the existing ones.
3. Add a `THEME.md` with the same sections, in the same order, as the existing guides. Copy one and replace its content rather than starting blank. The baron-hines.github.io theme pages read these parts directly and fail to build without them:

   | Section | Must contain |
   |---|---|
   | `## Fonts` | An ` ```html ` block with the font `<link>` |
   | `## Tokens` | One ` ```css ` block with every token on `:root`. A comment on its own line (`/* Surfaces and text */`) starts a group of swatches. A comment after a token describes it. |
   | `## Components` | One ` ```css ` block. Style the page through `body`, which the showcase maps to its own frame. |
   | `### Markup patterns` | Under Components: one line ending in a colon, then an ` ```html ` block, for each pattern |

4. Say which mode it is in the root README's table, and whether it pairs with another theme.
5. Add an example page to `examples/` if it helps.
6. To show it on baron-hines.github.io, follow "Adding a theme" in [that repo's README](https://github.com/baron-hines/baron-hines.github.io#adding-a-theme).

## Removing a theme

1. Check where it's used. Each theme's README lists that under **Where it's used**, and baron-hines.github.io and the home server's Forgejo are the current users.
2. Remove it from those projects first. For baron-hines.github.io, follow "Removing a theme" in [its README](https://github.com/baron-hines/baron-hines.github.io#removing-a-theme). Its build fails if a theme it lists has gone from here.
3. Then delete the theme's folder and its example page, remove it from the table above, and remove any of its entries in `PROPOSALS.md`.
4. If it was half of the light/dark pair, say what replaces it in the root README.
