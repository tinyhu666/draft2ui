# Style Presets

Load this file when the user asks for named design styles, style variants, or a custom style that needs translation into image2 prompt language.

## Presets

`clean-saas`
: Restrained B2B product UI, neutral surfaces, clear spacing, compact cards, blue or green accent, crisp data hierarchy, realistic filters, status chips, small charts, account/team metadata, minimal illustration.

`enterprise-dashboard`
: Dense operational dashboard, strong grid, left navigation, table/card mix, subtle borders, clear status colors, practical filters and actions, believable data rows, table density, pagination, alerts, role/status indicators.

`ios-native`
: iOS-style mobile UI, large title rhythm, rounded native controls, SF-like typography, soft grouped surfaces, bottom tab bar when appropriate, native list cells, badges, segmented controls, realistic empty/loading/selected states.

`material-you`
: Material 3 mobile/web UI, tonal surfaces, rounded components, clear elevation, expressive but controlled color roles, accessible contrast, FABs/menus/chips where appropriate, polished state layers.

`wechat-mini-program`
: WeChat mini-program style, mobile-first, compact top bar, simple bottom navigation or action footer, clean Chinese UI labels, familiar form/list patterns, restrained icons, list metadata, action sheets or sticky footers when relevant.

`premium-fintech`
: Trustworthy finance UI, sober palette, precise typography, chart/data emphasis, subtle depth, premium dark or light mode, strong security cues without clutter, realistic numbers, trend labels, risk/status badges, account/product details.

`healthcare-calm`
: Calm medical/wellness UI, high readability, generous spacing, reassuring color accents, clear next-step CTAs, low visual stress, appointment details, progress indicators, profile/photo placeholders, privacy cues.

`ecommerce-polished`
: Product-focused commerce UI, clean catalog or detail layout, strong image areas, price/CTA clarity, trust badges, tasteful promotional accents, product thumbnails, ratings, inventory badges, shipping/payment hints.

`youthful-consumer`
: Energetic consumer app, bolder accent colors, expressive cards, friendly iconography, lively but still readable hierarchy, avatars, reactions, badges, recommendations, playful microcopy without clutter.

`minimal-editorial`
: Sparse premium layout, lots of whitespace, elegant typography, few controls, muted palette, refined image or content focus, precise captions, subtle metadata, editorial imagery, delicate dividers.

## Combining Styles

When the user combines styles, keep the most specific domain style as the base and layer the visual mood on top:

- `dark + premium-fintech`: dark premium finance UI with disciplined contrast and data clarity.
- `ios + healthcare-calm`: iOS-native structure with calm healthcare palette and accessible spacing.
- `wechat-mini-program + youthful-consumer`: familiar mini-program layout with brighter consumer accents.
- `enterprise-dashboard + AI`: dense dashboard with AI-assist affordances, summaries, confidence chips, and automation controls.

## Prompt Language Tips

- Say "production-ready high-fidelity UI screenshot" instead of "beautiful app" when fidelity matters.
- Say "preserve the attached sketch's structure, component counts, and relative positions" to reduce layout drift and detail loss.
- Say "restore every visible UI cue from the sketch, then enrich vague areas with plausible domain-specific micro-details" when the result needs more fidelity and richness.
- Say "real shipped product screenshot with crisp typography, refined material layers, subtle shadows, and believable sample data" when the result looks flat or synthetic.
- Say "no wireframe placeholders or hand-drawn lines" to avoid low-fidelity artifacts.
- Say "no missing major components, no generic simplification, no blurry text, no empty placeholder blocks" when details are being dropped.
- Say "flat UI mockup, no device frame" unless a phone or laptop frame is explicitly requested.

## Detail Expansion Patterns

Use these as optional ingredients after preserving the sketch.

- Mobile apps: bottom-tab badges, profile avatars, segmented controls, search fields, native list metadata, sticky CTAs, notification dots, selected/disabled states.
- Dashboards: filters, date ranges, KPI deltas, legends, sparklines, status pills, dense tables, pagination, empty/error states, audit timestamps.
- Landing pages: product screenshots, trust logos, pricing/CTA details, feature rows, testimonial snippets, navigation states, subtle background imagery.
- Commerce: product thumbnails, ratings, discount badges, stock/shipping labels, cart summary, payment/trust cues.
- Finance: exact-looking numbers, trend arrows, risk labels, account cards, chart axes, transaction rows, security/verification hints.
- Healthcare: appointment cards, care team avatars, progress rings, medication/status tags, privacy cues, calm confirmation states.
