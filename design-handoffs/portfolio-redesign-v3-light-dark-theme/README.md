# Handoff: Portfolio Redesign

## Overview
A redesign of Marc Seger's personal portfolio (Product Manager, Data & AI). Light, warm-paper background with bold geometric type, pill buttons, rounded card-based work section, a subtle crossing diagonal-line background pattern, and a cursor-following spotlight glow.

## About the Design Files
`portfolio-redesign-light.html` is a **design reference** — a static, plain HTML/CSS/JS prototype showing the intended look and interactions. It is not meant to be dropped in as-is into a real codebase; recreate it in the portfolio's existing stack (plain HTML/CSS/JS is fine here since that's what the current site uses) matching this file's structure, styling, and behavior.

## Fidelity
High-fidelity. Colors, typography, spacing, and interactions are final — implement pixel-for-pixel.

## Screens / Views
Single page, two sections:

**1. Nav + Hero**
- Sticky-free top nav: name "Marc Seger" (700 weight, 18px) left; links "Work / View CV (underlined, accent) / GitHub / LinkedIn" right, 14px/500.
- Eyebrow label "PRODUCT MANAGER" — IBM Plex Mono, 13px, letter-spacing 0.1em, accent color.
- H1 "Product Manager, data & AI." — Space Grotesk 700, 92px, line-height 1, letter-spacing -0.03em, max-width 820px.
- Body copy below, 20px/1.6, muted gray, max-width 560px.
- Three pill buttons: primary (dark fill) "View CV", two secondary (outlined) "GitHub", "LinkedIn".

**2. Selected Work**
- Header row: "Selected work" (36px/700) left, "01—02" mono counter right.
- Two-column card grid (stacks to 1 column under 720px).
- Each card: white bg, 28px radius, 40px padding, subtle shadow, lifts on hover (translateY -6px + larger shadow).
  - Top row: card number (mono) left, stat pill (accent-tinted bg) right — "76.7% direction accuracy" / "63.8% win rate".
  - Title (26px/700), description (15px/1.65, muted).
  - Two text links at bottom: accent-colored primary action + muted "Code →".

## Interactions & Behavior
- **Cursor spotlight**: a soft radial gradient glow follows the mouse across the whole page background (CSS custom properties `--x`/`--y` updated on `mousemove`, driving a `radial-gradient` in the background).
- **Card hover**: lift + shadow grow, 0.25s ease transform/box-shadow transition.
- All links are placeholders (`href="#"`) — wire up to real CV/GitHub/LinkedIn/project URLs.
- Responsive: cards stack to one column, H1 shrinks to 52px under 720px width.

## Design Tokens
- **Colors** (all OKLCH): background `oklch(0.97 0.006 85)`, text `oklch(0.18 0.008 85)`, muted text `oklch(0.4-0.42 0.008 85)`, accent (brick orange) `oklch(0.68 0.16 45)` / accent text `oklch(0.5 0.16 45)`, accent tint bg `oklch(0.68 0.16 45 / 0.12)`, dark fill `oklch(0.2 0.01 85)`.
- **Typography**: Display/body — Space Grotesk (400/500/600/700). Mono accents (eyebrow, card numbers, stat pills) — IBM Plex Mono (400/500). Both via Google Fonts.
- **Radius**: pills/buttons 100px, cards 28px.
- **Shadow**: resting `0 1px 2px oklch(0.18 0.008 85 / 0.06)`; hover `0 20px 40px oklch(0.18 0.008 85 / 0.12)`.
- **Max content width**: 1180px.

## Assets
None — no images. If desired, add a portrait or project screenshots; none are used in this version.

## Files
- `portfolio-redesign-light.html` — light theme, full working prototype (open directly in a browser).
- `portfolio-redesign-dark.html` — dark theme variant, same layout/interactions. Background `oklch(0.1 0.008 60)` (near-black), text `oklch(0.93 0.012 60)`, cards `oklch(0.24 0.014 60)`, accent stays `oklch(0.72 0.15 45)` (brighter tint for dark bg). Cursor spotlight radius reduced to 350px with higher opacity (0.35) for visibility on black.
