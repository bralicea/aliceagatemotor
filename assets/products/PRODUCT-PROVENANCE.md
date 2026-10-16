# Hero catalog product provenance

Recorded: 2026-08-07

These product cutouts are used only inside the hero selector as catalog
references. Their presence does not assert that Alicea’s Gate Motor
Pro stocks, sells, installs, is authorized by, or is a dealer for the pictured
manufacturers or models.

## CAME BXV — Slide

- Product page supplied by Bryan:
  `https://www.came.com/us/installers/solutions/gates-operators/sliding-gates-operators/bxv`
- Official source image:
  `https://static.came.com/img/installer/Automations_Access_Control/series/Bxv.png`
- `came-bxv.png` is the source response saved byte-for-byte: 1440×810,
  SHA-256 `a1a66265db86249d09cffbe8727559f89e88af1a8a0cdf362546ad2856dc7f98`.
- `came-bxv-cutout.png` is a 538×810 delivery derivative. Fully transparent outer
  pixels were removed, then the original binary alpha silhouette was contracted
  by two pixels and softened by less than one pixel to exclude the opaque white
  fringe baked into the source edge. The visible product was not resized or
  recolored. SHA-256
  `eca0fa6b2dab838ec68f81f3781bd8db0791f40c8be655cc70f0a9767f1410f9`.
- `came-bxv-cutout-v3.png` is the current 538×810 delivery derivative. It uses an
  8-bit softened alpha mask and samples product color from approximately three
  percent inside the preserved silhouette, eliminating the pale stair-step
  carried by the source’s outermost RGB pixels. The silhouette, output size,
  product colors, and card scale remain unchanged; the exact source and prior
  derivative remain beside it. SHA-256
  `faf6419dc1ba69a75d1b4acad11563528cc7b58ce50a86b5d8b77f6edf176405`.
- ImageMagick reported no embedded EXIF, XMP, ICC, or other profile in the source.

## LiftMaster LA400 — Swing

- Related Remote Access catalog source:
  `https://lirp.cdn-website.com/44a7821c051c40c4a30240e8066ecb97/dms3rep/multi/opt/LA400-1920w.png`
- Manufacturer product page:
  `https://www.liftmaster.com/24vdc-residential-linear-actuator/p/LA400UL`
- `liftmaster-la400.png` is the related-catalog source response saved
  byte-for-byte: 420×420, SHA-256
  `43d6a506ea101bcd882b01f4d9a0129e766a3c97d5ef3085d65514eabeb4ccfd`.
- `liftmaster-la400-cutout.png` is a 354×99 delivery derivative. Only fully
  transparent outer pixels were removed; the product pixels were not resized,
  recolored, or recompressed. SHA-256
  `2ec47c353cae338bdf4001d554c1c2373bf947c712734cfa0b7fe8f321c1365c`.
- ImageMagick reported no embedded EXIF, XMP, ICC, or other profile in the source.

### Higher-resolution replacement, 2026-08-09

The 420×420 source above yields only 354×99 of actual product, which the hero
card upscaled on every retina display (1.77× at 1440@2x, 2.36× at 1920@2x, 1.38×
at 390@3x) while the CAME and ENFORCER references were still being downscaled.
The Remote Access CDN caps that asset at 420×420 regardless of the `-1920w` or
`-2400w` width label, so a larger rendition was sourced.

- Replacement source page: All Security Equipment distributor listing for the
  LiftMaster LA400 primary arm.
- Source image URL:
  `https://cdn.shopify.com/s/files/1/0537/7916/9453/products/LiftMaster-Replacement-Arm_91ddfffe-c1e9-487f-9423-74ead1eb3b9b.jpg`
- `liftmaster-la400-1000-source.jpg` is that response saved byte-for-byte:
  1000×1000, 24920 bytes, SHA-256
  `e255d9af4ee17b15137ea2d4550a2bef2877fa3e0d0b4a398bb6a58c75e39207`. Its
  embedded EXIF (172 bytes) and ICC (424 bytes) profiles are retained in this
  source copy and were not stripped.
- `liftmaster-la400-cutout-v2.png` is the 911×241 delivery derivative and the
  file the page now references. SHA-256
  `79caed5cac6ddb02405f8f3dc3bfa69ac2d5fa3505353f159447907f7dee9453`.
- Derivation: the white studio background was removed with a canvas-edge
  connected-matte flood fill at 20% tolerance, which protects the interior
  specular highlights on the actuator shaft — those reach 100% luminance and are
  destroyed by any global threshold. The product body measures roughly 30%
  luminance and the baked contact shadow spans roughly 30–95%, so the two are not
  separable by luminance; the detached lower shadow band (rows 242–255, verified
  as a separate opaque region with a transparent gap above it) was removed by
  cropping. The soft gradient still attached beneath the housing was kept and
  reads as a contact shadow. The product was not resized, recolored, redrawn, or
  otherwise retouched.
- The superseded `liftmaster-la400-cutout.png` (354×99) and its 420×420 source
  were removed during the September 2, 2026 cleanup.
- The product now renders downscaled at every tested viewport and pixel ratio
  (0.69× at 1440@2x, 0.92× at 1920@2x, 0.54× at 390@3x).

The replacement asserts nothing new: it remains a catalog reference used only to
distinguish the swing system type, with no stock, dealer, authorization, or
installed-model claim.

## ENFORCER SK-2323-SDQ — Keypad

Localized 2026-08-08. This reference previously hotlinked to the related Remote
Access catalog CDN; it is now served from this directory like the other two, so
the page makes no third-party requests.

- Related Remote Access catalog source:
  `https://lirp.cdn-website.com/44a7821c051c40c4a30240e8066ecb97/dms3rep/multi/opt/SK-2323-SDQ-1920w.webp`
- Manufacturer product page: not recorded. ENFORCER is a SECO-LARM brand, but
  seco-larm.com returns 403 to non-browser clients, so no specific product URL
  was confirmable at the time of writing. Fill this in from a browser rather than
  guessing the path.
- `enforcer-sk2323sdq.webp` is the source response saved byte-for-byte:
  1440×1440 WebP with alpha, 41860 bytes, SHA-256
  `9eb78cb4a1a81fb68148c1a198b2f5a2fdabd4e1d2103a9d1f122688c1a2987f`.
- No derivative was cut. The product already spans the full 1440-pixel height with
  transparent margins only on the left and right, and the hero panel scales it
  with `object-fit:contain`, so trimming to the 480×1440 content box would render
  at an identical size while forcing a lossy WebP re-encode. The file is used as
  delivered.
- ImageMagick reported no embedded EXIF, XMP, ICC, or other profile in the source.
