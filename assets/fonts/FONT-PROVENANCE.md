# Self-hosted webfont provenance

Recorded: 2026-08-08

The page previously loaded three families from the Google Fonts CDN
(`fonts.googleapis.com` stylesheet + `fonts.gstatic.com` font files). Those files
are now served from this directory and no request leaves the origin.

## Licensing

All three families are published under the **SIL Open Font License 1.1**, which
permits redistribution and self-hosting of the font files, including bundled with
a commercial work, provided the fonts are not sold on their own and the license
notice travels with them. No Google Fonts API terms apply once the files are
self-hosted — the API terms govern the hosted service, not the fonts.

| Family | Version | Designer / Foundry | License |
| --- | --- | --- | --- |
| DM Sans | v17 | Colophon Foundry, Jonny Pinhorn, Indian Type Foundry | SIL OFL 1.1 |
| Oswald | v57 | Vernon Adams, Kalapi Gajjar, Cyreal | SIL OFL 1.1 |
| IBM Plex Mono | v20 | Mike Abbink, Bold Monday / IBM | SIL OFL 1.1 |

## Delivered files

Each file is the upstream `gstatic.com` response saved byte-for-byte. Nothing was
re-subset, re-encoded, renamed internally, or otherwise modified.

| File | Bytes | SHA-256 |
| --- | --- | --- |
| `dm-sans-latin-var.woff2` | 62724 | `ca72d2bcea8f4daa783dbdfa2d9b46068c3ce38168e05918fb867aa453b4f890` |
| `oswald-latin-var.woff2` | 21472 | `571f3457dab507b6f2ce5394d593ca015251b69fea81ab7a546bd2368e9fc3ed` |
| `ibm-plex-mono-latin-400.woff2` | 14708 | `08949f728dc52d528e69b1667d15c89a5686a4ee9a296ff90983985f99c380f7` |
| `ibm-plex-mono-latin-500.woff2` | 14888 | `01d285447409c8a588692162439a038b8cbd7871309ee20267b0d2d91c6e8e22` |
| `ibm-plex-mono-latin-600.woff2` | 15620 | `0d1f0b8d0722224e32e9f28261bdc86c79115be73444ae5eceb73976a1bcdf83` |

Total 136 KB. DM Sans and Oswald are variable fonts covering weights 400–700 in a
single file each; IBM Plex Mono has no variable build on Google Fonts, so the
three static weights the page uses are stored separately.

Source URLs, for re-fetching or verifying against upstream:

```
https://fonts.gstatic.com/s/dmsans/v17/rP2Hp2ywxg089UriCZOIHQ.woff2
https://fonts.gstatic.com/s/oswald/v57/TK3IWkUHHAIjg75cFRf3bXL8LICs1_Fv40pKlN4NNSeSASz7FmlWHYg.woff2
https://fonts.gstatic.com/s/ibmplexmono/v20/-F63fjptAgt5VM-kVkqdyU8n1i8q1w.woff2
https://fonts.gstatic.com/s/ibmplexmono/v20/-F6qfjptAgt5VM-kVkqdyU8n3twJwlBFgg.woff2
https://fonts.gstatic.com/s/ibmplexmono/v20/-F6qfjptAgt5VM-kVkqdyU8n3vAOwlBFgg.woff2
```

These paths are content-hashed by Google and change when a family is revised.
Re-derive them by requesting the family CSS with a current browser User-Agent;
an older UA is served WOFF or TTF instead.

## Subsetting

**Latin subset only.** The `unicode-range` in each `@font-face` is copied verbatim
from the upstream latin subset, so glyph coverage and fallback behavior are
identical to the CDN version — no visual change, no new fallback flashes.

Every non-ASCII character on the page was checked against that range before
dropping the other subsets. The page uses `· ¿ × – — ' " " … á Á é í ñ ó ú`, all
of which the latin subset covers, including the full Spanish set in the bilingual
copy. The four arrow glyphs `← → ↗` (U+2190, U+2192, U+2197) fall outside the
latin range and render from the system fallback — that was already true on the
CDN version, so it is not a regression. `↑` (U+2191) is inside the range.

If Spanish copy is ever extended with characters outside Latin-1, or the business
name gains a glyph beyond it, add the `latin-ext` subset files rather than
widening these `unicode-range` values.

## Notes

- `ibm-plex-mono-latin-400.woff2` is declared but not requested in any state
  exercised during verification — the page's mono type is set at 500 and 600. It
  is kept because `@font-face` fetches are lazy, so an unused weight costs nothing
  until something needs it, and dropping it would risk a fallback flash in a state
  that was not exercised.
- Oswald and DM Sans are preloaded in `<head>`; they carry the hero H1 and body
  copy and are on the LCP path. Mono is not preloaded — it only sets small labels.
- Verified 2026-08-08 by loading the page with every non-localhost request
  aborted: zero external requests, no console errors, and
  `document.fonts` reported DM Sans, Oswald, and IBM Plex Mono 500/600 as
  `loaded`.
