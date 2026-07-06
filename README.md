# DaVinci Cafe — Premium Café Website (Merged, Single-File Version)

A fully responsive, animated café website built with **HTML5 + Tailwind CSS (CDN) + vanilla JavaScript**.
No build step, and no separate files to keep together — each `.html` file below is fully
self-contained (CSS and JS are inlined), so you can open either one directly in a browser
or upload just that one file anywhere.

## Files

```
index.html   → the full public site (nav, hero, menu, reservations, gallery, events, blog,
               testimonials, contact, cart, checkout, modals) — CSS and JS included inline
admin.html   → the demo staff dashboard (menu, reservations, orders, gallery, inventory) —
               CSS included inline, static/demo data only
README.md    → this file
```

**Editing note:** since this is the merged version, the CSS lives inside a `<style>` tag near
the top of each HTML file, and the JS lives inside a `<script>` tag near the bottom of
`index.html`. Find them with Ctrl/Cmd+F for `<style>` or `MENU_DATA`. If you'd rather edit
CSS/JS as separate files again (often easier for ongoing edits), ask and a split version
can be regenerated from this one.

## Why vanilla JS instead of GSAP / React / Framer Motion

The brief allowed either approach. This build uses dependency-free vanilla JS (IntersectionObserver
for scroll reveals, CSS keyframes for parallax/floating/marquee effects) so the whole site runs by
opening a single HTML file — no npm install, no bundler, no CDN version mismatches. If you later want
to port it to React, the `MENU_DATA`, `GALLERY_DATA`, and `TESTIMONIALS_DATA` arrays at the top of
`app.js` map directly to component props/state.

## Editing content

- **Menu items** → edit the `MENU_DATA` array in `app.js`. Each item needs `id`, `name`, `category`,
  `price`, `desc`, `img`, and optional `popular` / `seasonal` flags for badges.
- **Gallery photos** → edit `GALLERY_DATA` in `app.js` (`cat`, `h` for masonry height, `img`, `caption`).
- **Testimonials** → edit `TESTIMONIALS_DATA` in `app.js`.
- **Text content** (hero copy, about story, staff names, FAQ, contact info) → edit directly in `index.html`,
  it's all plain HTML with clear section comments.
- **Colors/fonts** → edit the `tailwind.config` block at the top of `index.html` (and mirrored in
  `admin.html`). All custom colors (`espresso`, `roast`, `bark`, `cream`, `parchment`, `caramel`, `ember`,
  `rust`) are used as Tailwind utility classes like `bg-caramel` or `text-ember`.
- **Images** — all placeholder photos are from Unsplash (free to use). Swap any `<img src="...">` or
  `img:` field for your own photography before launch.

## Features included

Hero with animated gradient + floating bean/steam particles, sticky glass nav, custom loading screen,
scroll progress bar, custom cursor (desktop), scroll-reveal + image-reveal animations, animated counters,
dark/light mode (persisted), full menu with category filters + "popular"/"seasonal" badges + quantity
selector + add-to-cart, chef's recommendations strip, live occupancy indicator (simulated), reservation
form with date/time/guest stepper + confirmation modal, masonry gallery with category filters + keyboard-
navigable lightbox, events section with booking buttons that deep-link to the reservation form, blog
cards, auto-sliding testimonial carousel with star ratings, FAQ accordion, newsletter form, Instagram
placeholder grid, contact form + map placeholder + social icons, cart drawer with quantity controls,
promo codes (`EMBER10`, `OAKFAM`), pickup/delivery toggle with delivery fee, checkout modal with a demo
payment form and order confirmation, WhatsApp floating button, demo live-chat widget with canned replies,
cookie consent banner, and a separate demo admin dashboard (`admin.html`) with overview stats, menu
table, reservations table, orders table, gallery manager, and inventory bars.

## What's intentionally a UI demo, not a live backend

This is a front-end template with no server. To go to production you'd connect:

- **Reservations & contact/newsletter forms** → a backend endpoint or a form service (e.g. your own API,
  Formspree, etc.) instead of the current in-page confirmation.
- **Checkout/payment** → a real payment processor (Stripe, etc.) instead of the demo card form.
- **Admin dashboard** → real data from your order/reservation database instead of the static arrays in
  `admin.html`.
- **Map placeholder** → an embedded Google Maps / Mapbox iframe with your address and API key.
- **Instagram feed** → the Instagram Basic Display API or a service like SnapWidget/Elfsight.

## Accessibility & performance notes

- Skip-to-content link, visible focus states via Tailwind's default focus rings on interactive elements,
  `alt` text on all images, keyboard support in the lightbox (Esc/←/→).
- `prefers-reduced-motion` is respected — animations collapse to near-instant for users who request it.
- All images use `loading="lazy"` except nothing above the fold is lazy (hero has no `<img>`, it's CSS).
