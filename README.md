# DJ1 — Group Drum Class Landing Page

Single-file landing page for **Drumset Jumpstart 1**, a 10-week online group drum class for complete beginners. Built to live in a Squarespace iframe at `jva-music.com`.

## Files

- `index.html` — everything (HTML, inline CSS, small JS). No build step.
- `assets/` — images. **Not yet committed; see [Required assets](#required-assets) below.**

## Local preview

Any static server works. From the repo root:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Where to update key content

| Change | Where to look |
| --- | --- |
| **Waitlist mailto body** | `<script>` near the bottom — the `PRIMARY_CTA_URL` constant is the source of truth and overrides every `[data-cta]` link on load. The two `href="mailto:..."` attributes (hero CTA + final CTA band) are no-JS fallbacks; update those to match if you change the script constant. |
| **Pricing** | Pricing section (`<!-- PRICING -->`). Two cards: "Full course" and "Drop-in". Edit prices inline. |
| **Cohort dates / start week** | The page intentionally doesn't list dates yet — copy in the final CTA band says "I'll be in touch as soon as dates and a start week are set." When dates are confirmed, update that paragraph and consider adding a chip/line to the hero. |
| **Cohort cap (currently 10)** | Search for `10` in the hero chip, the "How it works" tile, the FAQ, and the final CTA band. |
| **Missed-class policy** | FAQ item drafted without recordings/makeups since policy isn't set. Update before launch. |
| **Testimonial framing** | Eyebrow says "What private students say" because all three quotes are from private lessons. Once you have group-cohort wins, swap the quotes and rewrite the eyebrow. |
| **Copyright year** | Auto-set from `new Date().getFullYear()` in the footer script. |

## Required assets

Drop these into `assets/`. The HTML already references them.

| File | Dimensions | Notes |
| --- | --- | --- |
| `assets/hero.jpg` | **1000 × 1250** (4:5 portrait) | Used in the hero. A photo of Jacobo at the kit (or with sticks/pad) works best. JPEG, ~150–250 KB after compression. |

That's it for now. The page deliberately doesn't have a media/Listen section, so no audio/video embeds or Open Graph image are required to ship — but if you want a social-share image, add `assets/og.jpg` (1200 × 630) and a `<meta property="og:image">` tag in the `<head>`.

## Notes for editors

- Inline CSS is split into commented chunks (vars, layout, hero, testimonials, pricing, about, faq, cta band, footer, mobile cleanup, dark mode, print). Search for the chunk header to find the rules you want.
- External links (`jva-music.com`, privacy policy) open in a new tab via `target="_blank" rel="noopener"` so they break out of the Squarespace iframe correctly.
- The page reports its rendered height to the parent window via `postMessage` (`{type:'jva-iframe-height',height:N}`) on load, resize, font-load, and any `<details>` toggle. Use that on the Squarespace side to size the iframe without scrollbars.
- Dark mode follows the visitor's OS preference. There is no manual toggle.
