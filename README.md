# Dentist Website Design — Lumio Dental

A calm, modern, multi-page static website for a dental practice. Built with
plain HTML, CSS, and a small amount of vanilla JS — no build step, no
framework, no dependencies beyond two Google Fonts.

> **"Lumio Dental" is a placeholder name.** Swap it for your real practice
> name, address, phone number, and team before launch — see "What to
> customize" below.

## Pages

| File             | Purpose                                                |
|-------------------|---------------------------------------------------------|
| `index.html`      | Home — hero, treatment overview, philosophy, testimonial |
| `services.html`   | Full treatment list with details + FAQ                |
| `team.html`       | Practice values + team member profiles                |
| `contact.html`    | Booking form, hours, address, map placeholder, FAQ     |

## Structure

```
.
├── index.html
├── services.html
├── team.html
├── contact.html
└── assets/
    ├── css/
    │   ├── base.css       # design tokens + shared styles (header, footer, buttons, FAQ, CTA, page-hero)
    │   ├── home.css        # homepage-only styles
    │   ├── services.css    # services page-only styles
    │   ├── team.css        # team page-only styles
    │   └── contact.css     # contact page-only styles
    └── js/
        ├── main.js          # mobile nav toggle, scroll-reveal animation, FAQ accordion
        └── contact-form.js  # contact form front-end handling (see note below)
```

Shared components (header, footer, buttons, FAQ accordion, CTA band, page
hero) live once in `base.css` and are reused across pages. Each page has its
own stylesheet for layout that's unique to that page only — this avoids the
duplicate-selector trap where the same class gets redefined in multiple
files.

## Design system

- **Colors** are drawn from clinical materials rather than generic
  "trustworthy blue": porcelain white background, deep teal-ink for text,
  a single cyan-teal accent, and one warm coral reserved only for the
  booking call-to-action so it's never confused with the rest of the
  palette. All tokens are CSS variables in `base.css`, under `:root`.
- **Type**: Fraunces (serif, display/headings) + Work Sans (body/UI).
- **Signature motif**: an abstract smile-arc line motif (visible in the
  hero SVG and the divider at the bottom of the hero section), used instead
  of stock photography or generic icon sets.

## What to customize before launch

1. **Practice name & branding** — replace "Lumio Dental" throughout all
   four HTML files (search for `Lumio`).
2. **Contact details** — phone number, email, and address appear in the
   header, footer, and `contact.html`. Search for `+31 10 123 4567`,
   `hello@lumiodental.nl`, and `Witte de Withstraat`.
3. **Opening hours** — edit the table in `contact.html` (`#hours`).
4. **Team photos** — `team.html` currently uses abstract placeholder
   avatars (SVG silhouettes on solid color blocks) instead of real photos.
   Replace `.team-photo` divs with real `<img>` tags once you have photos.
5. **Map** — the map on `contact.html` is a stylized illustration, not a
   real map. Swap `.map-placeholder` for an embedded Google Maps iframe or
   a static map image pointing at your real address.
6. **Booking form** — `assets/js/contact-form.js` only shows a confirmation
   message in the browser; it does **not** send data anywhere yet. Connect
   it to a real backend, serverless function, or a form service (e.g.
   Formspree) before relying on it for real bookings.
7. **Insurance / legal copy** — the FAQ answers reference Dutch dental
   insurance norms (basisverzekering) as a starting point. Adjust for your
   country's system and your own practice's policies.

## Running locally

No build step needed. Either open `index.html` directly in a browser, or
serve the folder so relative paths and fonts behave exactly as in
production:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Accessibility & performance notes

- Keyboard focus is visible on all interactive elements (`:focus-visible`).
- `prefers-reduced-motion` is respected — animations are disabled for users
  who request it.
- All images currently in use are inline SVG (no external image requests
  besides the two Google Font files), so the only thing to optimize once
  you add real photography is the photos themselves.
