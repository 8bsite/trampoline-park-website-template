# Hopla — notes for AI coding agents

One HTML file: markup, inline CSS and inline scripts; GSAP with ScrollTrigger and SplitText, Lenis smooth scroll, all from jsDelivr. No build step, no framework.

## Files
Work from the files: a page read through a link comes back as a summary, and a page rebuilt from it would differ.
```bash
curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/index.html
curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/AGENTS.md
curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/LICENSE
curl -LO https://raw.githubusercontent.com/8bsite/trampoline-park-website-template/main/CREDITS.md
```
In Windows PowerShell type `curl.exe`. Publish `index.html` with LICENSE and CREDITS.md; this file, README.md and `previews/` are not part of the site.

## Do not break
- Keep it one file unless the user asks otherwise; no framework or bundler for copy, colour or photo changes.
- Keep the ids and the `data-8b-section` / `data-8b-motion` attributes. Each section has its styles in `<style data-8b-part="section:<id>">` and its animation, if any, in `<script data-8b-part="scene:<id>">`.
- The scripts find these classes and attributes; when you change a section's markup, keep them or update the script:
  - `section-script:nav`: `.nav__menu` `.menu__close` `.menu__list`
  - `section-script:contact`: `.ct__form` `.ct__status` `data-error` `data-sent`
  - `scene:opening`: `.op__jumper` `.op__title-in` `.op__sticker` `.op__wave` `.op__fan` `.op__card` `.op__bed`
  - `scene:zones`: `.zn__row` `.zn__disc` `.zn__name` `.zn__body`
  - `scene:airtime`: `.at__img` `.at__line` `.at__text`
  - `scene:sessions`: `.ss__title` `.ss__ticket--glow`
  - `scene:parties`: `.pt__route` `.pt__ball` `.pt__ball-in` `.pt__stop` `.pt__pop` `.pt__dash` `.pt__trail` `.pt__stops`
  - `scene:league`: `.lg__rows` `data-week`
  - `scene:prices`: `.pr__row`
  - `scene:faq`: `.fq__list` `.fq__mark` `.fq__item`
  - `scene:footer`: `.ft__mark-wrap` `.ft__mark` `.ft__disc`
- Colours, fonts, radii and shadows are CSS variables in the `:root` block (`data-8b-part="tokens"`); change them there and keep body text at 4.5:1 contrast or more.
- Animations run only when the visitor allows motion (`prefers-reduced-motion: no-preference`); the page must stay readable without them.
- A display line with `style="--len:N"` is sized to fill its width: N is its number of characters, spaces included (`Bounce` → 6, `Hopla` → 5).
- Keep the header comment and `<meta name="generator">`. Keep the "Design: 8B" footer link unless the site owner asks to remove it.

## Replace before publishing
- Everything marked `data-8b-placeholder` (og-image, favicon, phone, email, form); remove the attribute once the real value is in. With no real value: no preview image — delete the `og:image` tag and set `twitter:card` to `summary`; no phone, email or address — remove that link or row.
- Book (nav), Book a jump (first screen and prices): link to #contact now; point them to your online booking page.
- Book a party (parties): link to #contact now; point them to your party booking page or enquiry form.
- Enter this month's league (league): link to #contact now; point them to your league entry form, or remove the link.
- **The form sends nothing.** `section-script:contact` checks the fields and shows a thank-you message without sending. Pick one:
  - Formspree: set `action="https://formspree.io/f/<id>"` on the form; in the script, before the thank-you message, `await fetch(form.action, { method: 'POST', body: new FormData(form), headers: { Accept: 'application/json' } })` and show it only if the response is ok.
  - Netlify Forms (site on Netlify): add `name="contact" data-netlify="true"` and `<input type="hidden" name="form-name" value="contact">`; send with `fetch('/', { method: 'POST', headers: { 'Content-Type': 'application/x-www-form-urlencoded' }, body: new URLSearchParams(new FormData(form)) })`.
  - No form service: remove the `<form>` together with the script that handles it (it would fail without the form) and keep the email link.
- Invented demo facts (ask the user for the real ones; do not make up prices, dates or addresses):
  - Place: an indoor park in an old steel shed in Sheffield; the address "Unit 3, Furnace Yard, Sheffield S3" (menu overlay, contact, footer); Sheffield also in the page title, meta description and the hidden text of the first heading (opening).
  - Directions: forty free parking spaces in the yard and the Shalesmoor tram stop two minutes away (faq "Where do we park?", contact, "Free parking" sticker).
  - Phone and email (replaced with placeholders) in the menu overlay, faq, contact and footer.
  - Opening hours: Monday to Thursday 9:30 to 20:00, Friday 9:30 to 22:00, Saturday 9:00 to 22:00, Sunday 9:00 to 19:00 (contact); "Open 7 days" sticker and "Late nights on Fridays and Saturdays" (opening).
  - Session times: Little Hops weekdays 9:30 to 12:00, Open Jump every day 12:00 to 16:00, After School weekdays 16:00 to 18:30, Rebound Tue and Thu 18:45 to 19:30, Glow Night Fri and Sat 19:30 to 22:00 (sessions); dodgeball leagues on Mondays and ninja coaching on Wednesdays (sessions); a quiet hour every Sunday at nine (faq).
  - Pass prices: Hour Jump £14, Long Jump £18, Little Hops £8.50, Glow Night £16 (two and a half hours, 13+), Frequent Flyer £29 a month with unlimited Open Jump and a monthly guest pass (prices); grip socks £2.50 (rules, prices).
  - Party offer: from £19 per child, ten jumpers minimum, invitations included, ninety minutes, an hour on the courts with a coach, the party room for forty-five minutes, pizza, squash, fruit, party bags and a balloon for every guest (parties).
  - Café menu prices: flat white £3.10, hot chocolate £3.40, cheese toastie £5.20, kids' pizza slice £3.80, slushie £2.60, fruit pot £2.20; hot food all day, free Wi-Fi, a plug at every table, high chairs, a changing room (landing).
  - Ages: "Ages 3 to 93" (opening); zone ages All ages, 6+, 7+, 8+, 6+, Under 5s (zones); session ages Under 5s with a grown-up, 5 and up, 7 to 16, Adults 16+, 13 and up (sessions); children under eight need a grown-up in the building, waivers for under-18s signed by a parent or carer (faq).
  - Venue numbers: sixty-two linked trampolines and a foam pit "the size of a swimming pool" (opening); forty linked beds, nine thousand foam blocks, twelve obstacles, three slam-dunk runways (zones, league); "Six zones" (opening sticker).
  - Free things and promises: spectators never pay, one grown-up jumps free with every child under five, free entry for carers, free lockers, coaches on every court, "we'll email back within the hour" (landing, sessions, prices, faq, rules, contact form text and its data-sent message).
  - Rules and policies: online waiver that lasts a year, only birthday cakes may be brought in, the café caters for most allergies, step-free access to the café, toilets and two of the courts, walk-ins when there is space (rules, faq).
  - League: six named people with times (Maisie R. 41.82 s, Dev P. 42.10 s, Tomasz K. 43.57 s, Ruby A. 44.03 s, Kwame O. 45.66 s, Lou B. 46.20 s), the caption "October, after four Sundays", the table settling every Sunday night and the prize of a year of free jumping (league).
  - Company: "© 2026 Hopla Trampoline Park Ltd" (footer).
- `<title>`, the meta description and the og tags; photos (Unsplash, see CREDITS.md) when the user has their own.

## Notes
- The wavy section edges are inline SVGs (class m-wave); each coloured section starts with one. Their colour follows the section's background.
- The sessions background colour run and the Glow Night glow use --color-4, --color-5, --color-2 and --color-3: recolour through the tokens and the run follows.
- The rules and the FAQ mention an online waiver, but the page has no waiver link: add one if you use a waiver service, or edit the text.
- Without motion (reduce motion or no JavaScript) the sessions section stays on the yellow morning ground; with motion it ends on the night ground. Both are complete and readable.
- The footer wordmark stays split into letters (SplitText) after it lands; this is invisible but shows in the DOM.
- The league note under the table describes the animation ("Rows start in last Sunday's order…"); edit or remove it with the rows.

## Common edits
- Rebrand: search the old name (`Hopla`) in any letter case and replace every match; change the favicon letter and colours in `<link rel="icon">`.
- Photos: replace `src` and delete `srcset` and `sizes` (they list Unsplash sizes), keep `width`/`height` to the new photo's ratio, update `alt` and CREDITS.md.
- Remove a section: delete its markup, its `section:<id>` and `scene-style:<id>` styles, its `scene:<id>` and `section-script:<id>` scripts, and links to `#<id>`.
- Native scroll instead of smooth scroll: delete the Lenis block in `page-init` and the Lenis `<script>` tag.

## Check and publish
- Open the page at 375 and 1440 px, with reduced motion on, with the console open.
- Search `data-8b-placeholder` and the old name: nothing should be left but class names.
