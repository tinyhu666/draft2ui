# Style Presets

Load this file when the user asks for named design styles, style variants, or a custom style that needs translation into image2 prompt language.

## Presets

`clean-saas`
: Restrained B2B product UI, neutral surfaces, clear spacing, compact cards, blue or green accent, crisp data hierarchy, minimal illustration.

`enterprise-dashboard`
: Dense operational dashboard, strong grid, left navigation, table/card mix, subtle borders, clear status colors, practical filters and actions.

`ios-native`
: iOS-style mobile UI, large title rhythm, rounded native controls, SF-like typography, soft grouped surfaces, bottom tab bar when appropriate.

`material-you`
: Material 3 mobile/web UI, tonal surfaces, rounded components, clear elevation, expressive but controlled color roles, accessible contrast.

`wechat-mini-program`
: WeChat mini-program style, mobile-first, compact top bar, simple bottom navigation or action footer, clean Chinese UI labels, familiar form/list patterns.

`premium-fintech`
: Trustworthy finance UI, sober palette, precise typography, chart/data emphasis, subtle depth, premium dark or light mode, strong security cues without clutter.

`healthcare-calm`
: Calm medical/wellness UI, high readability, generous spacing, reassuring color accents, clear next-step CTAs, low visual stress.

`ecommerce-polished`
: Product-focused commerce UI, clean catalog or detail layout, strong image areas, price/CTA clarity, trust badges, tasteful promotional accents.

`youthful-consumer`
: Energetic consumer app, bolder accent colors, expressive cards, friendly iconography, lively but still readable hierarchy.

`minimal-editorial`
: Sparse premium layout, lots of whitespace, elegant typography, few controls, muted palette, refined image or content focus.

## Combining Styles

When the user combines styles, keep the most specific domain style as the base and layer the visual mood on top:

- `dark + premium-fintech`: dark premium finance UI with disciplined contrast and data clarity.
- `ios + healthcare-calm`: iOS-native structure with calm healthcare palette and accessible spacing.
- `wechat-mini-program + youthful-consumer`: familiar mini-program layout with brighter consumer accents.
- `enterprise-dashboard + AI`: dense dashboard with AI-assist affordances, summaries, confidence chips, and automation controls.

## Prompt Language Tips

- Say "production-ready high-fidelity UI screenshot" instead of "beautiful app" when fidelity matters.
- Say "preserve the attached sketch's structure" to reduce layout drift.
- Say "no wireframe placeholders or hand-drawn lines" to avoid low-fidelity artifacts.
- Say "flat UI mockup, no device frame" unless a phone or laptop frame is explicitly requested.
