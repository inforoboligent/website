# Roboligent website

One static page. No build step, no framework, no server code. A browser can open
`index.html` directly.

```
index.html      the whole page: markup, inline styles, one script block at the end
styles.css      design-system tokens (colors, type, spacing) — do not edit casually
assets/         logo, favicon, social-share image
videos/         the clips the page loads on scroll
```

## Deploying

Netlify is connected to this repository and redeploys on every push to `main`.
Nothing to build: publish directory is the repository root, build command is empty.

A commit to any other branch produces a preview URL instead of touching the live
site. Use that for anything you are unsure about.

## Making a change

Most edits are text. Open `index.html` in GitHub's web editor, use Ctrl/Cmd-F to
find the sentence, change it, commit. Live in about a minute.

Replacing a video or image: upload into `videos/` or `assets/` keeping the
filename identical. Nothing else needs touching.

New sections, layout changes, anything structural: bring it back to the design
session rather than editing here.

## Do not edit without care

- The `:root` block at the top of `index.html` — the color tokens. One wrong
  value restyles the entire page.
- `styles.css` — comes from the design system; local edits get overwritten the
  next time the design is regenerated.

## Before this goes live

- [ ] `FORM_ENDPOINT` near the bottom of `index.html` is empty, so the contact
      form confirms but sends nothing. Create a Formspree (or Basin) form, paste
      the endpoint URL between the quotes, and test it once.
- [ ] `assets/favicon.png` and `assets/og-image.png` are referenced but not yet
      present. The og-image is what appears when the site is shared on LinkedIn;
      1200×630.
- [ ] Hero video: the markup sits commented out at the top of `<section id="top">`
      in `index.html`, waiting on clean landscape footage. The existing clips are
      square with a burned-in watermark, so the wide hero band crops them badly.
      To enable: add the file to `videos/`, set its name in the `src`, remove the
      comment markers.
- [ ] Compress the videos. They are phone-camera exports, larger than they need
      to be, and the page loads them on scroll. Two of the three also carry a
      burned-in watermark and a "2X" badge.
- [ ] Careers: the five LinkedIn links all point at the company jobs page.
      Replace with per-posting URLs. The descriptions were drafted from internal
      notes and have not been reviewed.
- [ ] The impact-force diagram is explicitly labelled illustrative. Replace with
      measured values once testing is done, and cite the standard.
- [ ] Unverified specs carried over from the earlier prototype: weight and
      footprint, runtime, end-effector force sensitivity, validation cycles.

## Content owners

| Section | Lives in | Owner |
| --- | --- | --- |
| Hero, stack, Physical AI | `index.html` | |
| Robin spec grid | `index.html` | |
| Applications | `index.html` | |
| Subscription | `index.html` | |
| Company credentials | `index.html` | |
| Careers rows | `index.html` | |
| Contact form destination | Formspree dashboard | |
