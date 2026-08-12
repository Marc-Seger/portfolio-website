# Task: Add a curtain-reveal loading screen to the site

I want a one-time intro loading screen that plays on first visit, then reveals
the actual homepage. Reference implementation is in `loader-snippet.html`
(attached alongside this prompt) — it's a self-contained HTML/CSS/JS block
that already works standalone.

## What it does

1. On page load, a full-screen black overlay covers the page. Centered on it:
   my initials "MS", a thin progress bar, and a small percentage counter that
   ticks from 0 to 100.
2. Once it hits 100%, the black overlay splits into two panels (top half
   slides up off-screen, bottom half slides down off-screen) — a curtain
   effect — revealing the real homepage underneath.
3. It only plays once per browser session (uses `sessionStorage`), not on
   every page navigation.
4. It respects `prefers-reduced-motion` — users with that preference skip
   straight past it.
5. Once the reveal finishes, the overlay is fully removed from the DOM so it
   never blocks clicks/interaction afterward.

## What I need you to do

1. Look at how the site is built (framework, if any — plain HTML, React,
   Next.js, etc.) and figure out the cleanest way to wire this in given the
   actual codebase.
2. Integrate the markup/CSS/JS from `loader-snippet.html`:
   - If it's a static/plain HTML site: this can likely be dropped in close
     to as-is, right after `<body>` opens on the entry page(s).
   - If it's a component-based framework (React/Next/Vue/etc.): convert this
     into an idiomatic component that mounts once at the app root/layout
     level and unmounts itself after the reveal animation completes. Keep
     the same timing and easing.
3. Match the colors to the site's actual design tokens instead of the
   hardcoded hex values in the snippet:
   - Black/ink color used in the snippet (`#14120f`) → replace with the
     site's real ink/black color variable if one exists.
   - Cream color used in the snippet (`#f4efe6`) → replace with the site's
     real background/cream color variable if one exists.
   - Font stack → replace with whatever font the site's headline/nav uses,
     if there's a project font already set up (e.g. a custom @font-face or
     a framework font import), rather than the generic system stack in the
     snippet.
4. Make sure it doesn't cause a layout shift or flash of unstyled content —
   the overlay should be present and covering the page before first paint if
   possible (e.g. inline critical CSS if the framework's build pipeline
   would otherwise delay stylesheet load).
5. Double check it doesn't replay on internal client-side route
   changes/navigations if the framework does client-side routing — it
   should only ever show on true first load of a session.

## Acceptance criteria

- Fresh session / first visit: loading screen plays once, then reveals the
  homepage via the curtain-split animation.
- Reloading or navigating within the same session: no loading screen,
  content just shows immediately.
- New session (new tab in incognito, or after clearing sessionStorage):
  loading screen plays again.
- `prefers-reduced-motion: reduce` set: loading screen is skipped entirely,
  homepage shows immediately.
- No console errors, no layout shift, no interaction blocked after the
  overlay is gone.

Let me know what framework/stack you find and how you're planning to
integrate it before making changes, in case it needs adjusting.
