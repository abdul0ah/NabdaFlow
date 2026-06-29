# NabdaFlow — Clinic Landing Site

A single-page, self-contained marketing site for **NabdaFlow**, an AI automation agency
for clinics in the UAE. Bilingual (English / Arabic with full RTL), deep-teal cinematic
design, no build step required.

Tagline: *AI solutions that keep your clinic's pulse flowing.*
Founders: Abdullah & Rabie.

---

## How to open / run

This is a plain static site. There is **no build step and no dependencies**.

- To preview: just open `index.html` in any web browser (double-click it), **or**
- Serve it locally (nicer for development):
  ```bash
  # Python
  python3 -m http.server 8000
  # then visit http://localhost:8000

  # or Node
  npx serve .
  ```

Everything — HTML, CSS, JavaScript, and the logo (embedded as Base64) — lives inside
`index.html`. There are no external file dependencies, so the page works offline and
can be hosted anywhere.

---

## File structure

```
nabdaflow-site/
├── index.html   ← the entire website (HTML + CSS + JS + embedded logo)
└── README.md    ← this file
```

---

## Live integrations (already wired in)

- **Booking (Cal.com):** https://cal.com/nabdaflow/15-minute-clinic-consultation
  - Used on every "Book a consult / Book a 15-Minute Consult" button.
- **Waitlist form (Formspree):** endpoint `https://formspree.io/f/mnjkpqyz`
  - The waitlist form submits here via fetch; on success it shows an inline thank-you state.
  - NOTE: Formspree sends a one-time confirmation email on the very first real submission —
    click the link in it once to activate the form permanently.

To change either, search `index.html` for `cal.com/nabdaflow` or `formspree.io/f/` and swap the value.

---

## Sections (in order)

1. **Hero** — headline "A smarter operating system for your clinic *starts here.*",
   dual CTA (book consult + what we build), softly pulsing background logo, parallax orbs.
2. **The name** — explains نَبْض (Nabda = pulse) + Flow; bilingual copy differs intentionally
   (the Arabic is NOT a direct translation, so it reads correctly for an Arabic-only reader).
3. **Common issues** — three hover-animated cards (after-hours messages, no-shows, repeat questions).
4. **How we work** — 4-step scroll-driven timeline (the cyan line fills and steps light up as you scroll).
5. **What we build** — six service tabs (Patient Communication, Bookings & No-Shows,
   Patient Qualification, Website & Landing Pages, Marketing & Growth, Custom Clinic Systems).
6. **FAQ** — accordion, 5 questions.
7. **CTA** — book consult / join waitlist.
8. **Waitlist** — the Formspree form (name, clinic, email, WhatsApp, interest).
9. **Footer**.

---

## Design notes / conventions

- **Palette:** deep teal dark theme throughout; electric cyan (`#2fe9ff`) accent for emphasis.
- **Fonts:** Space Grotesk (headings), Inter (body), IBM Plex Sans Arabic (Arabic), Fraunces (the "name" statement).
- **Bilingual system:** every translatable bit is two `<span>`s — `data-en` and `data-ar`.
  The EN/AR toggle flips `dir` on `<body>` and the CSS show/hides the right one. When editing
  copy, update BOTH spans so the toggle stays in sync.
- **No em-dashes in body copy** (deliberate stylistic choice).
- **Motion is intentional:** scroll reveals, the how-it-works fill, hover glows, a light logo pulse.
  All of it respects `prefers-reduced-motion` (disabled for users who ask for less motion).
- Avoid adding any continuously-animating canvas / moving lines across the page — these were
  tried and removed for being distracting / janky. Keep motion subtle.

---

## To-do before going live

- [ ] Activate the Formspree form (submit once, click the confirmation email).
- [ ] Confirm the Cal.com event is live and set to a 15-minute slot.
- [ ] Host it (drag `index.html` onto Netlify Drop, or use GitHub Pages / Cloudflare Pages / Vercel).
- [ ] (Recommended) point a short domain at it, e.g. `nabdaflow.ae`, for trust + email deliverability.
- [ ] Optional: replace the embedded logo with a true transparent PNG/SVG if one becomes available
      (current one has a faint edge at extreme zoom from being cut out of a non-transparent source).

---

## Known notes

- The logo is embedded as Base64 inside `index.html`. To swap it, replace the
  `--logo-light` data URI in the `:root` CSS block.
- Tested working across desktop, Arabic RTL, and mobile.
