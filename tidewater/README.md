# Tidewater

**Cyan, then quiet.** Tidewater is a calm light theme built on one hue. Cyan carries every action, the neutrals lean cool to sit beside it, and everything else stays out of the way.

To build with it, follow [THEME.md](THEME.md). It has the tokens, the components and the rules, written to be followed literally by people and AI agents alike. This page is the why.

## Design philosophy

- **One hue does the talking.** Cyan 700 is the brand color: the darkest step that still reads as cyan, and dark enough that white text on it passes 4.5:1. Every button, link and active state uses it, so there's never a question of what to press.
- **The rest of the ramp has rules.** Steps 50 to 200 tint surfaces and halos. Steps 300 to 500 are for charts and illustration only, never text. 800 is hover, and 900 is text on a cyan tint.
- **Neutrals lean cool.** The page is `--ground`, a cool near-white, never pure white or grey. Cards sit on it in white with a hairline border and a soft shadow, so depth comes from layering, not from decoration.
- **Status is never color alone.** Every status tag holds a word, "Healthy" or "Failing", next to its color.
- **Gentle, not bubbly.** Controls have a 6px radius and cards 12px. Only tags are pills.
- **Two kinds of elevation, used sparingly.** `--shadow-raised` for cards resting on the page, `--shadow-floating` only for things that actually float, like menus and dialogs.
- **Plain words, sentence case.** Buttons say what happens ("Create project", never "Submit"). Errors say what went wrong and how to fix it. Only the small mono labels are uppercase.
- **No neon.** No glows, gradients or effects. Those belong to the other theme.

## Foundations

| | |
|---|---|
| **Color** | A cyan ramp from 50 to 950, with 700 as `--primary`. Neutrals `--ground`, `--surface`, `--border`, `--muted`, `--ink`. Status `--positive`, `--caution`, `--critical`, each with a tint. |
| **Type** | Sora for titles and headings. IBM Plex Sans for everything people read. IBM Plex Mono for labels and code. |
| **Space** | A 4px base. Cards pad 24px. Stacked controls sit 16px apart, sections 48px. |
| **Shape** | `--radius-input` 6px, `--radius-card` 12px, `--radius-pill` for tags. |
| **Depth** | `--shadow-raised` and `--shadow-floating`. |
| **Icons** | Inline SVG, 20px, 2px stroke, round caps, no fill, colored like the text beside them. |

## Where it's used

- [baron-hines.github.io](https://baron-hines.github.io/), as the light mode. The [Tidewater page there](https://baron-hines.github.io/projects/themes/tidewater/) shows every token and component live.
- The self-hosted Forgejo on the home server, as its light theme.

Its dark counterpart is [Neon Terminal](../neon-terminal/).
