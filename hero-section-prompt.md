# Prompt: Build the Hero Section

Build the hero section for a one-page design portfolio as static HTML/CSS/JS (no framework). Match the following spec exactly.

## Structure

1. **Sticky header** above the hero, full width:
   - Left: wordmark/name, links to `#top`
   - Right: local-time readout (`Intl.DateTimeFormat`, updates every 15s, format `HH:MM` + timezone label) + a single nav link to the footer contact anchor
   - Background: semi-transparent paper color with `backdrop-filter: blur(10px)`, becomes visible once the user scrolls (or is visible from the start — your call, but keep it minimal)
   - Include a visually-hidden "skip to content" link as the very first focusable element, for accessibility

2. **Hero body**, generous vertical padding (roughly 10–14vw top, 6–8vw bottom):
   - Small eyebrow line above the headline: a location or context tag, uppercase, monospace, muted color
   - One large headline, two lines:
     - Line 1: regular/bold weight, sets the practice's one-line thesis
     - Line 2: a short (2–4 word) italic accent fragment in a contrasting weight — this is the visual focal point
   - One supporting sentence below the headline, max ~44 characters per line, muted ink color, not pure black
   - A small meta row beneath: 2–3 short labels (location, project count, availability), monospace, uppercase, separated by generous gaps

## Color Palette (monochrome, no accent color)

- Background ("paper"): near-white, warm-neutral — not pure `#FFFFFF`, something like `#FAFAF8`
- Primary ink: near-black, not pure `#000000` — something like `#0A0A0A`
- Secondary/soft ink (supporting text): a lighter warm gray, `#3A3A38`
- Muted (labels, meta): a mid warm gray, `#8A8A84`
- Hairline dividers: `#DEDDD6`
- No blue/color accent anywhere — all emphasis comes from type weight, scale, and italics, not color

## Typography

- Display font: a bold, condensed/grotesque sans (e.g. Archivo, Neue Haas, or similar) for the main headline
- Body font: a clean humanist sans (e.g. Inter) for supporting text
- Label font: a monospace (e.g. IBM Plex Mono) for the eyebrow, meta row, and header time readout
- Headline sizing: fluid via `clamp()`, roughly `clamp(2.75rem, 9vw, 7.5rem)`, line-height ~0.92, tight letter-spacing (`-0.02em`)
- Headline is set in lowercase throughout (a deliberate stylistic choice, not a mistake)

## Animation

- On page load: headline lines and supporting text fade + slide up (translateY ~18px → 0, opacity 0 → 1), staggered by ~100–150ms per line — restrained, not bouncy, ~0.6s ease
- No parallax, no cursor-follow effects, no heavy motion in the hero itself — the identity here is restraint; type and whitespace do the work, not movement
- The local-time readout in the header should tick live (re-render every 15s) but not animate visually
- Wrap all animation in a `prefers-reduced-motion: reduce` media query that disables it entirely for users who request it

## Responsive Behavior

- Headline scales fluidly with `clamp()`, never requires manual breakpoint overrides for font-size
- Below ~640px: meta row stacks vertically instead of running inline
- Maintain generous whitespace at all sizes — don't compress padding aggressively on mobile, restructure instead

## Deliverable

Output clean, semantic HTML with a linked external stylesheet (no inline styles except where noted), and a small vanilla JS block for the load-in animation and time readout. No build tooling, no dependencies beyond a Google Fonts link.
