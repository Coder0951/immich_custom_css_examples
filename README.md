# Immich Custom CSS Showcase — Reference

Companion doc for `immich-neon-showcase-theme.css`. This CSS goes in
**Administration > Server Settings > Theming > Custom CSS**. It restyles
real components using Immich's actual `--immich-ui-*` tokens (recolored),
plus transitions and keyframe animations to demonstrate what the custom
CSS field can do.

## Component → Color → Behavior

| Component | Color | Static style | Motion |
|---|---|---|---|
| **Header / nav** | Neon cyan (`info`) | Gradient bar, glow border | Bottom edge pulses (`neon-pulse`) |
| **Nav avatar / round buttons** | Neon cyan | Radial gradient fill | Scale + rotate on hover (spring easing) |
| **Sidebar** | Neon violet | Gradient fill, glowing border | Active link pulses; hover slides item right 6px |
| **Cards / thumbnails** | Neon green (`success`) | Glow border | Scale 1.05 + saturate image on hover |
| **Settings panels** | Neon green | Inset glow | Border glows on state change |
| **Accordions (`<details>`)** | Neon violet | Gradient header | Open state pulses; chevron rotates 45° on hover |
| **Inputs / search** | Neon orange | Gradient fill, inset glow | Focus ring glows (`warning` color) |
| **Checkboxes / radios** | Neon orange | — | Pulses while checked |
| **Buttons (default)** | Neon magenta (`primary`) | Glow border | Lift + scale on hover, press-down on active, icon rotates 15° |
| **Buttons (primary/CTA)** | Neon magenta | Gradient fill | Stronger glow + lift on hover |
| **Disabled buttons** | Grayscale | Dimmed, no glow | Static (intentionally inert) |
| **Modals** | Magenta/violet blend | Gradient fill, heavy glow | Gentle float (`float-glow`, 4s loop) |
| **Dropdowns / menus** | Neon magenta | Glow border | Item highlight on hover |
| **Alerts / errors** | Neon red (`danger`) | Left border accent | Pulses continuously to draw attention |
| **Warning banners** | Neon orange (`warning`) | Left border accent | Static |
| **Info banners / status** | Neon cyan (`info`) | Left border accent | Static |
| **Toasts** | Inherits alert/info color | — | Floats (`float-glow`) |
| **Progress / quota bars** | Orange→red gradient | Animated gradient | Continuous scan (`neon-scan`, 3s loop) |
| **Loading spinners** | — | — | Flicker (`neon-flicker`, 2s loop) |
| **Scrollbar** | Magenta→violet gradient | Glow | Brighter glow on hover |
| **Text selection** | Neon orange | Solid fill | — |
| **Page bottom edge** | Full rainbow gradient | — | Continuous horizontal scan |

## Animation Library (defined once, reused everywhere)

- **`neon-pulse`** — box-shadow breathes between a tight glow and a wide double-glow. Used on: header edge, sidebar active state, accordion open state, alerts, checked toggles.
- **`neon-scan`** — background-position slides across a 200%-wide gradient, giving a moving light-bar effect. Used on: progress bars, page-bottom edge, sidebar progress bars.
- **`neon-flicker`** — brief opacity dips mimicking a flickering neon tube. Used on: spinners/loading indicators.
- **`float-glow`** — gentle up/down translate, like the element is hovering. Used on: modals, toasts.

All animations respect `prefers-reduced-motion: reduce` — they're disabled system-wide for users with that OS setting.

## Design Notes

- Real `--immich-ui-*` variable names are preserved so this is a drop-in
  override, not a parallel token system — swapping hex values here
  re-themes the actual app, not a mock.
- A few extra `--neon-*` variables (sidebar, card, input accents) exist
  outside the official ramp purely to give the sidebar/cards/inputs their
  own distinct hue beyond the five official ramps (primary, success,
  danger, warning, info).
- Every transition uses one of two eases: `--ease-spring` (bouncy, for
  interactive/hover elements) or `--ease-smooth` (calm, for background/
  backdrop changes) — swap these globally to change the whole feel.
- To tone this down to a real theme: replace hex values with brand colors,
  drop the `animation:` lines you don't want, keep the transitions.
