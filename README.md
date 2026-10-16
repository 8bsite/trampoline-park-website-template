# Free HTML trampoline park website template with GSAP scroll animations — Hopla

**Website for a trampoline park or indoor family activity venue: a free HTML template in one file, with GSAP scroll animations, no build step, MIT license. Made by [8B](https://8b.com/), the AI website builder.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) ![one HTML file: no build](https://img.shields.io/badge/one%20HTML%20file-no%20build-orange) ![GSAP: ScrollTrigger](https://img.shields.io/badge/GSAP-ScrollTrigger-88ce02)

**[Live demo](https://8bsite.github.io/trampoline-park-website-template/)** · **[Use this template](https://github.com/new?template_name=trampoline-park-website-template&template_owner=8bsite)** · **[Download ZIP](https://github.com/8bsite/trampoline-park-website-template/archive/refs/heads/main.zip)**

<a href="https://8bsite.github.io/trampoline-park-website-template/"><img src="previews/desktop.png" alt="Hopla, a free HTML template: first screen on a desktop" width="76.1%"></a> <a href="https://8bsite.github.io/trampoline-park-website-template/"><img src="previews/phone.png" alt="Hopla, a free HTML template: first screen on a phone" width="21.9%"></a>

<p align="center"><a href="https://8bsite.github.io/trampoline-park-website-template/"><img src="previews/scroll.gif" alt="Hopla, a free HTML template: scrolling through the first sections on a desktop" width="40%"></a><br><sub>Scroll animation</sub></p>

A one-page site for an indoor trampoline park with zones, sessions, birthday parties, a café, a league table, prices and booking. Cream, red and yellow fields with wobbly trampoline-bed edges and big condensed type; the page bounces as you scroll: a jumper is launched off the first screen, photo discs hop down the zone list and a red ball hops along the party route.

Good for: trampoline park or bounce centre; indoor play centre or soft play; climbing, ninja or adventure park; kids' party venue; any family leisure venue with sessions, passes and bookings. Free for personal and commercial use (MIT), made by [8B](https://8b.com/).

## Quick start

Pick one:

- **With an AI coding agent** (Claude Code, Codex, Cursor, Windsurf…). Download the files into your project (in Windows PowerShell type `curl.exe`):
  ```bash
  curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/index.html
  curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/AGENTS.md
  curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/LICENSE
  curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/CREDITS.md
  ```
  Then give your agent this prompt:
  ```text
  Read AGENTS.md, then edit index.html. Use this template as the base for a site for <your venue: what it is (trampoline park, play centre, climbing or adventure park), city and address, activities or zones, sessions and opening hours, prices, parties, how to book>. Keep the layout, the motion and the single-file format; replace the brand name, copy, photos, prices, hours, links and contacts, and recolour it through the CSS variables if needed.
  ```
  Give the agent the downloaded file, not a link: an agent reads a link as a summary and would rebuild a different page.
- **No code.** Download the ZIP, unzip it, replace the contacts and texts in `index.html`, put `index.html` into an empty folder and drag that folder onto [Netlify Drop](https://app.netlify.com/drop). The page is online in a minute.
- **On GitHub.** Click **[Use this template](https://github.com/new?template_name=trampoline-park-website-template&template_owner=8bsite)** to get your own copy, then **Settings → Pages → Deploy from a branch → main**. Your site appears at `https://<you>.github.io/<repo>/`.

## What's on the page

- **Navigation** — fixed top bar: wordmark, Book button, Menu button opening a full-screen link overlay with contacts
- **Bounce at Hopla, the trampoline park in Sheffield** — first screen: one giant word with a photo of a jumper in front, wordmark, two stickers, two short texts; then a red panel with heading, button and three tilted photos
- **One roof, six ways off the ground** — list of six activity zones in a zig-zag: big name, one line, age sticker, round photo (demo: trampoline zones)
- **The best bit is the middle** — full-width photo with a two-line statement held on screen while you scroll
- **One shed, five crowds** — timetable of five sessions as tickets: time, name, text, ages, photo (ground turns from morning yellow to night)
- **Birthday parties, sorted** — birthday parties: heading, text, price line, button, and a five-step route with numbered tilted photos
- **The Landing** — on-site café: wide photo, round coffee photo, sticker, text, short price list
- **Ninja Wall League** — ranking table of six results on a dark field, with heading, text, entry link and photo (demo: ninja wall times)
- **House rules, short version** — red wall of five tilted rule stickers and one photo (house rules)
- **Pick a pass** — five ticket-shaped passes with name, price and one line, plus two buttons
- **Asked a lot** — questions and answers (native &lt;details&gt;) next to a heading and a phone line
- **Come and jump** — address, opening hours, phone, email, directions and a booking request form (placeholders)
- **Footer** — links, address and phone, copyright with the Design: 8B credit, a giant outlined HOPLA wordmark with three round photos

## Before you publish

- Replace everything marked `data-8b-placeholder` (social preview image, favicon, phone, email, form) and the invented demo facts — prices, dates, address. [AGENTS.md](AGENTS.md) lists them.
- The contact form does not send anything yet: connect it to a form service (Formspree, Netlify Forms) or remove it; [AGENTS.md](AGENTS.md) shows both.

## Customize

- **Colours and fonts**: CSS variables in the `:root` block at the top of `<head>`.
- **Text**: edit it in place. A big display line with `style="--len:N"` fills its width: set N to its new number of characters.
- **Photos**: replace `src`, delete `srcset` and `sizes` (they list Unsplash sizes) and update the `alt` texts.
- **Animations**: each section's animation is one `<script data-8b-part="scene:<id>">` block at the end of the file. For native scroll, delete the Lenis block in `page-init`.

## For developers

- **Stack.** HTML and CSS (custom properties, cascade layers) with GSAP 3.13.0, ScrollTrigger, SplitText, MotionPathPlugin, Lenis 1.3.27 from jsDelivr. No build step, no framework, no npm. 126 KB.
- **Layout of the file.** `<head>`: CSS variables, shared classes, then one style block per section. Then the markup, one element per section with a one-line comment above it. End of `<body>`: small behaviour scripts, the libraries, smooth scroll (`page-init`), the effects, one animation script per section.
- **Browsers.** Chrome and Edge 111+, Safari 16.2+, Firefox 113+ (it uses color-mix(), cascade layers, small/dynamic viewport units).
- **Accessibility.** Motion runs only when the visitor's system allows it; with "reduce motion" the page is complete and still. FAQ answers use native `<details>` and open without JavaScript. Every photo has alt text.
- **External requests.** fonts.gstatic.com, images.unsplash.com, cdn.jsdelivr.net. No analytics, no cookies. To self-host everything (offline use, or Google Fonts and GDPR in the EU), download those files and change the URLs.
- **Licences of the parts.** GSAP is free, commercial use included, under its own standard licence (not MIT); Lenis is MIT; fonts are SIL OFL; photos are under the Unsplash License. See [CREDITS.md](CREDITS.md).

## FAQ

**Can I use it for a client or a commercial site?** Yes. The code is MIT: use it, change it, sell the site you build with it.

**Do I have to keep the "Design: 8B" link?** No. It is welcome, not required.

**Can I use it in React, Next.js, Astro or Vue?** Yes. Move each section's markup and style block into a component and run its animation script in `useGSAP()` (React) or `onMounted` (Vue); start Lenis once. Or keep it as a separate static landing page next to your app (`example.com` for the landing, `app.example.com` for the app).

**Why doesn't the contact form send?** It is a demo. Connect it to Formspree, Netlify Forms or your backend; AGENTS.md has the steps.

**Where are the photos from?** Unsplash; they load from Unsplash's servers. Replace them with your own when you can.

## More free templates

[More 8B templates on GitHub](https://github.com/8bsite) · [8b.com](https://8b.com/)

## License

The template code is MIT licensed — see [LICENSE](LICENSE). Photos, fonts and libraries keep their own licences — see [CREDITS.md](CREDITS.md).
