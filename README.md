# Ayven NFC tap page — demo

A single static, mobile-first page that an NFC tag/card opens when tapped. The business shown, **Demo Dog Grooming (Livingston, West Lothian)**, is fictional. Every phone number, link and opening time is a placeholder.

Live: https://leehiggins111.github.io/ayven-nfc-demo/

## What's on the page
- Logo initial, name, location, one-line value prop, a "Demo — sample business" badge
- Large buttons: Call, WhatsApp, Book appointment, Leave a Google review, Save contact (builds a `.vcf` vCard in the browser and downloads it)
- Opening hours, social links, footer "Powered by Ayven Campus · NFC tap pages"

Everything is in `index.html` (inline CSS/JS). There's no build step and no external requests.

## Customise for a client
At the top of the `<script>` in `index.html`:
- Edit `DEFAULT` (name, initial, tagline, phone, WhatsApp link, email, website, `bookUrl`, `reviewUrl`, `accent`, hours, socials). Set `demo: false` to hide the badge.
- Or add a skin to `CLIENTS` and open `…/ayven-nfc-demo/?b=<key>`. Example: `?b=demo-cafe`.

The Google review link comes from the business's Google Business Profile ("Ask for reviews" / share review form).

## Write the URL to an NFC tag
1. Use NTAG213 (144 bytes, enough for a short URL) or NTAG215 (504 bytes). Keep the URL short. A `?b=` key helps with this.
2. Install **NFC Tools** (iOS / Android).
3. Go to **Write → Add a record → URL/URI** and enter the full `https://…` URL.
4. Tap **Write** and hold the phone to the tag.
5. Test it with an iPhone and an Android phone. iPhones read NFC in the background on XS and later. Some Android phones need NFC switched on.
6. Optional: once it's tested, lock the tag in NFC Tools (**Other → Lock tag**) so nobody can overwrite it. **Locking is permanent.**

## Deploy
GitHub Pages via `.github/workflows/deploy.yml` on every push to `main`.
