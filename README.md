# Calvin Januri — Portfolio (Retro / Pixel Theme)

Single-file HTML portfolio styled like an 8-bit game menu (title screen, character stats, quest log, inventory, level select, achievements, continue/contact). All fonts and images are embedded as base64, so `index.html` works standalone with no build step or external files.

## Concept

The page is framed as if you're navigating a retro game:

| Game screen | Real content |
|---|---|
| Title screen | Hero — name, role, intro |
| Character sheet / Stats | About me + skill percentage bars |
| Quest log | Work experience |
| Inventory | Tools & soft skills |
| Level select | Projects |
| Achievements | Education & certificates |
| Continue? | Contact info |

## Typography

| Role | Font | Used for |
|---|---|---|
| Display | [Press Start 2P](https://fonts.google.com/specimen/Press+Start+2P) | Headlines, nav, buttons, tags — short bursts of text only (it's a true bitmap-style font, very wide) |
| Body | [VT323](https://fonts.google.com/specimen/VT323) | Paragraphs, lists, labels — a CRT-terminal style monospace, set larger than usual since VT323 renders small |

Both are open source (SIL Open Font License) and embedded directly in the HTML `<style>` as base64 `@font-face` rules — no external font requests, no Google Fonts dependency.

## Color palette

| Name | Hex | Usage |
|---|---|---|
| Ink | `#0c0a1a` | Page background, primary text on light surfaces |
| Panel | `#181334` | Card/box background |
| Panel 2 | `#221c4d` | Secondary card background (inventory slots) |
| Paper | `#f4ecd8` | Primary text color, borders |
| Paper Dim | `#c9c2ab` | Secondary/muted text |
| Coral | `#ff5d5d` | Primary accent — headline shadows, CTA buttons, "stage" tags |
| Coral Dim | `#8a2f37` | Headline drop-shadow (darker coral) |
| Mint | `#57e0c4` | Secondary accent — links, kicker labels, one stat bar |
| Gold | `#ffc857` | Highlight accent — buttons, active nav state, "LV." tag |

Design rule: no gradients, no rounded corners anywhere — corners are chunky pixel-stepped (via CSS `clip-path`) instead of `border-radius`, to keep the 8-bit feel consistent.

## Layout structure

- `.hud` — fixed top nav bar (game HUD), collapses to a MENU button under 860px
- `.hero` — full-height title screen with pixel-grid background and blinking "press start" cursor
- `.pixel-box` — reusable bordered "dialog box" component used for every card/section (stat panel, quest card, inventory slot, level card, achievement card, contact box)
- `.crt-overlay` / `.crt-vignette` / `.crt-flicker` — fixed-position scanline texture, edge vignette, and a one-time power-on flicker animation on load
- Responsive breakpoints at `860px` (nav → hamburger, grids collapse) and `520px` (tighter type scale)
- Respects `prefers-reduced-motion`: disables the flicker and speeds up all transitions for users who've asked for reduced motion

## Assets

- Portrait photo and project/certificate screenshots are the real images from Calvin's original CV and portfolio PDFs, cropped/compressed and embedded as base64 JPEGs
- No stock photos, no AI-generated imagery

## Editing this file

Everything lives in one file (`index.html`):
- Colors/fonts/spacing → CSS variables and rules in the `<style>` block at the top
- Content → HTML further down, organized by `<section id="...">` matching the table above
- Interactivity (mobile menu, scroll-reveal, active nav highlight, stat bar fill animation) → `<script>` block at the bottom, plain JS, no dependencies

## License / attribution

- Press Start 2P and VT323 fonts: SIL Open Font License 1.1
- All other code and content: yours to reuse/edit freely
