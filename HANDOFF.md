# Handoff — Roboligent website

## What exists where

| Thing | Where | Who needs it |
| --- | --- | --- |
| Deployed site | `inforoboligent/website` (GitHub, private) | whoever edits copy |
| Hosting | Netlify site `comfy-cassata-b55263` | whoever deploys |
| Design source | `Roboligent Website.dc.html`, in the Claude design project | whoever changes layout or adds sections |
| Videos, logo | `videos/`, `assets/` in both places | — |

The repo holds a flattened copy of the design: one `index.html` with inline
styles and a single vanilla script. It has no dependency on Claude and deploys
on its own. The `.dc.html` file is the editable original — same page, but
themeable and componentised. They are kept in sync by hand.

## Two ways to make a change

**Copy, numbers, a job description, a swapped video** — edit `index.html` in
GitHub's web editor and commit. Netlify redeploys in about a minute. Nothing
else to do. Mirror the same edit into the design project when convenient so the
two don't drift.

**New sections, layout, colours, anything structural** — do it in the Claude
design project, then re-export the deployable folder and upload the changed
files to the repo. Editing `index.html` for this kind of change works, but the
design source silently falls behind.

## Getting access

1. GitHub: `inforoboligent/website`, signed in as info@roboligent.com. Write
   access is enough for content edits.
2. Netlify: same login, site `comfy-cassata-b55263`. Deploys are automatic;
   the dashboard is only needed for domain and form settings.
3. The Claude design project: ask the current owner to share it. Opening a new
   Claude session and pointing it at the GitHub repo gives you the *deployed*
   page, not the design source or the reasoning behind it.

## Decisions already made, so they don't get re-opened

- One long page, no sub-pages. Audience is manufacturing buyers and investors;
  the goal is credibility, not lead capture.
- Emerald theme: ground `#f8fafc`, accent `#059669`, colour fields `#04624a`,
  sub-text `#334155`. Seven other themes were built and rejected. The `:root`
  block at the top of `index.html` holds the tokens.
- "Series elastic actuator" is deliberately not used anywhere — it is a
  searchable academic term and invites competitors into the tech stack. The page
  says "soft actuation" and "compliant force-controlled actuators" instead.
- Regen has no section of its own; the rehab work survives as one clause on the
  AFWERX credential, so the page reads as focused.
- "Austin, Texas" for recognition, "Round Rock" where the fact matters
  (facility, footer address, job locations).
- The impact-force diagram is explicitly labelled illustrative. It encodes one
  real claim — roughly a tenth the impact force — and no measured numbers.
- The hero video is commented out at the top of `<section id="top">`. Existing
  clips are 480x480 with a burned-in watermark and crop badly in a wide band.

## Open items

Ordered by what blocks a public launch.

1. **Contact form sends nothing.** `FORM_ENDPOINT` near the bottom of
   `index.html` is an empty string. Create a Formspree form, paste its endpoint
   between the quotes, submit the form once to confirm. Netlify Forms will not
   work here — it scans static HTML at deploy time and this page renders its
   form through JavaScript.
2. **Domain.** roboligent.com still points at Wix. Netlify Domain management
   shows the A and CNAME records to set at Wix. Do not touch MX records if
   company mail runs through Wix. Cancel the Wix plan only after
   `https://roboligent.com` serves the new site.
3. **Videos.** Phone exports, larger than they need to be, loaded on scroll.
   Two carry a watermark and a "2X" badge. Compress before launch; a
   professional shoot is planned in a couple of months.
4. **og-image.** `assets/og-image.png` is referenced but missing — it is what
   appears when the site is shared on LinkedIn. 1200x630.
5. **Careers.** All five rows link to the company jobs page, not per-posting
   URLs. The descriptions were drafted from internal Confluence notes and have
   not been reviewed by the hiring managers. Two of the five roles have no
   Confluence page at all.
6. **Unverified specs** carried over from the original prototype and never
   confirmed: 105 kg weight and 680x600 mm footprint, 6-12 hr runtime,
   < 0.1 N force sensitivity, 100,000 validation cycles. Everything else in the
   spec grid has been confirmed.
7. **Logo.** The wordmark is brand navy, which sits slightly against the emerald
   accent. A single-colour black and white version would resolve it.

## Do not edit casually

- The `:root` token block at the top of `index.html`. One wrong value restyles
  the whole page.
- `styles.css`. It comes from the design system and gets overwritten whenever
  the design is regenerated.
