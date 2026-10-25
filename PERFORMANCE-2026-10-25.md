# Performance follow-up — 25 October 2026

Branch: `plesk-staging-2026-10-20` in `x9230x/omoikiri-kazakhstan.github.io`.

`omoikiri.kz` is currently served by PHP and uses the static files in Plesk's
`/staging.omoikiri.kz` directory. Changes to those files affect the live site.

## Completed and deployed

- PHP static assets now use cache headers, ETags, conditional 304 responses and
  byte ranges. Live HTTP responses were checked.
- Twelve homepage images were converted from about 18.7 MB to 1.1 MB WebP;
  below-fold images load lazily. Eight TAPS/FILTERS videos were reduced from
  about 28.6 MB to 11.1 MB and load near the viewport.
- The DISPOSER canvas now loads near the viewport on desktop and phones. Its 99
  frames were reduced from 28.7 MB PNG to 4.0 MB WebP. The old PNG files remain
  on the server for rollback; the page references the new files.
- Fixed distorted Mikura and HOME images caused by conflicting HTML dimensions
  and CSS sizing. Confirmed their displayed aspect ratios on the live page.
- The FILTERS switch now uses the compressed video for all four variants.
- RU and KZ now use the same Montserrat font files. The original Gotham files
  lack Kazakh glyphs. RU → KZ → RU and the four FILTERS switches were checked
  on the live page.

Plesk package applied: `outputs/omoikiri-layout-disposer-font-20261025.zip`.
Local rollback package for the first performance change:
`outputs/omoikiri-performance-rollback-20261025.zip`.

## Next checks

- Check the full homepage on a real phone and compare it visually with the
  current `omoikiri.ru`, especially the DISPOSER canvas and KZ line wraps.
- Profile first load on a throttled mobile connection. The full page is still
  media-rich, but heavy sections now load as the visitor scrolls.
- If KZ font changes seem delayed on a previously open product or catalog tab,
  refresh the page; those HTML files still use the old script query string and
  may keep the prior one-hour browser cache until it expires.
- Clean up old deployment ZIP files in Plesk only after identifying which are
  needed for rollback. Disk use was about 63% of the 25 GB plan, with no CPU,
  memory or I/O resource faults in the past 24 hours.

No online payment was added. Do not share passwords or secrets in chat or Git.
