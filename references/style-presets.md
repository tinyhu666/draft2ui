# Style Presets

Load this file when the user asks for named design styles, style variants, or a custom style that needs translation into image2 prompt language.

## Presets

`simple-tool`
: Default style when the user provides no style. Practical lightweight utility UI, neutral surfaces, clear hierarchy, low decoration, compact controls, crisp meaningful text, concrete sample data, subtle depth, accessible contrast, and final-grade product polish.

`clean-saas`
: Restrained B2B product UI, neutral surfaces, clear spacing, compact cards, blue or green accent, crisp data hierarchy, realistic filters, status chips, small charts, account/team metadata, minimal illustration.

`enterprise-dashboard`
: Dense operational dashboard, strong grid, left navigation, table/card mix, subtle borders, clear status colors, practical filters and actions, believable data rows, table density, pagination, alerts, role/status indicators.

`ai-assistant-tool`
: Modern AI workflow UI, prompt/input areas, generated result panels, confidence/status chips, model/action controls, history sidebar, subtle glowing accents only where useful, clear human-in-the-loop affordances.

`developer-console`
: Technical product console, code/log panels, monospaced data where appropriate, API keys or environment chips, terminal-like status surfaces, sidebar navigation, dense but readable tables, clear success/error states.

`productivity-workspace`
: Notes/tasks/calendar workspace, calm neutral layout, split panes, quick actions, search, tags, checklists, compact cards, keyboard-friendly states, practical utility feel.

`creator-studio`
: Media/content creation tool, canvas or preview area, timeline/layers/sidebar controls, asset thumbnails, inspector panels, export/share actions, polished but work-focused visual hierarchy.

`education-learning`
: Learning platform UI, course cards, progress indicators, lesson navigation, quizzes, readable content areas, supportive color accents, achievement/status details without childish clutter.

`social-community`
: Community or social app UI, profiles, avatars, posts/messages, reactions, follow/status chips, notification dots, lively but controlled hierarchy and concrete user/content data.

`travel-local`
: Travel, maps, or local discovery UI, destination imagery, itinerary cards, map/list toggles, ratings, distance/time labels, booking/status details, warm but legible palette.

`food-service`
: Restaurant, delivery, or booking UI, menu/product cards, ratings, delivery time, price, cart/checkout actions, tasteful food imagery, availability/status labels.

`gaming-hud`
: Game-style UI, immersive HUD/menu panels, bold contrast, progress bars, inventory/status widgets, mission/reward cards, energy/level indicators, dramatic accents while retaining readable app structure.

`anime-inspired`
: Anime/二次元-inspired UI, bright expressive palette, cel-shaded illustration or mascot areas when appropriate, playful cards, sticker-like badges, soft gradients, energetic typography accents while preserving UI clarity.

`cyberpunk-neon`
: Dark futuristic UI, neon accent lines, glassy panels, dense telemetry/status elements, high-contrast charts, sci-fi controls, disciplined readability and no decorative chaos.

`luxury-premium`
: High-end premium UI, restrained palette, elegant typography, spacious layout, refined imagery, delicate dividers, subtle metallic or editorial accents, minimal but concrete interface details.

`kids-friendly`
: Child-friendly UI, large touch targets, warm colors, simple labels, friendly illustration zones, clear progress/reward states, accessible contrast, not overly busy.

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

- No style provided: use `simple-tool`.
- `dark + premium-fintech`: dark premium finance UI with disciplined contrast and data clarity.
- `ios + healthcare-calm`: iOS-native structure with calm healthcare palette and accessible spacing.
- `wechat-mini-program + youthful-consumer`: familiar mini-program layout with brighter consumer accents.
- `enterprise-dashboard + AI`: dense dashboard with AI-assist affordances, summaries, confidence chips, and automation controls.
- `anime + education-learning`: learning UI with anime-inspired color/illustration treatment, still readable and platform-native.
- `game UI + productivity-workspace`: task/workspace structure with game-like progress, rewards, and HUD-style status accents.

## Explicit Style Overrides

If the user provides a vivid style phrase, preserve that phrase as the primary visual direction even when a preset is only approximate.

- `二次元`, `anime`, `ACG`: use `anime-inspired`.
- `游戏风`, `game`, `game UI`, `HUD`: use `gaming-hud`.
- `赛博朋克`, `cyberpunk`, `neon`: use `cyberpunk-neon`.
- `像工具`, `简单工具`, `utility`, no explicit style: use `simple-tool`.
- `高端`, `奢华`, `luxury`, `premium`: use `luxury-premium` unless finance is the stronger domain, then combine with `premium-fintech`.
- `儿童`, `kids`, `toy-like`: use `kids-friendly`.

## Prompt Language Tips

- Say "final-grade production UI design screenshot" instead of "beautiful app" or "prototype" when visual quality matters.
- Say "preserve the attached sketch's structure, component counts, and relative positions" to reduce layout drift and detail loss.
- Say "restore every visible UI cue from the sketch, then enrich vague areas with plausible domain-specific micro-details" when the result needs more fidelity and richness.
- Say "real shipped product screenshot with crisp typography, design-system components, refined material layers, subtle shadows, and believable sample data" when the result looks flat or synthetic.
- Say "all text must be meaningful, legible UI copy with concrete values; no xx, xxx, lorem ipsum, placeholder text, TODO text, or random glyphs" when text quality matters.
- Say "use the target platform's native interaction style from platform conventions" when the output looks like generic UI instead of iOS, Android, Windows, macOS, Web, or WeChat.
- Say "no wireframe placeholders or hand-drawn lines" to avoid low-fidelity artifacts.
- Say "no missing major components, no generic simplification, no blurry or garbled text, no empty placeholder blocks" when details are being dropped.
- Say "flat UI mockup, no device frame" unless a phone or laptop frame is explicitly requested.

## Detail Expansion Patterns

Use these as optional ingredients after preserving the sketch.

- Mobile apps: bottom-tab badges, profile avatars, segmented controls, search fields, native list metadata, sticky CTAs, notification dots, selected/disabled states.
- Dashboards: filters, date ranges, KPI deltas, legends, sparklines, status pills, dense tables, pagination, empty/error states, audit timestamps.
- Landing pages: product screenshots, trust logos, pricing/CTA details, feature rows, testimonial snippets, navigation states, subtle background imagery.
- Commerce: product thumbnails, ratings, discount badges, stock/shipping labels, cart summary, payment/trust cues.
- Finance: exact-looking numbers, trend arrows, risk labels, account cards, chart axes, transaction rows, security/verification hints.
- Healthcare: appointment cards, care team avatars, progress rings, medication/status tags, privacy cues, calm confirmation states.
