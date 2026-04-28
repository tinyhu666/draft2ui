---
name: draft2ui
description: Use when the user asks for Draft2UI, sketch-to-design, draft-to-UI, sketch-to-render, wireframe-to-hi-fi, image2 UI mockup generation, custom UI style mockups, or high-fidelity restoration from hand-drawn UI prototype images, wireframes, rough sketches, paper mockups, low-fidelity app/web layouts, screenshots, or photos of sketches; includes "手绘原型图", "草图转高保真", "线框图生成设计图", "低保真转高保真", and "自定义设计图风格".
---

# Draft2UI

## Purpose

Turn a rough UI sketch into a faithful, detailed, final-grade product UI design image. Preserve the sketch's information hierarchy, layout intent, and visible detail cues, then upgrade spacing, typography, color, components, realism, platform interaction language, and visual finish until it reads as a polished UI design standard, not a prototype.

Use the built-in `image_gen` tool as the default GPT image2 path. Do not create code, HTML, SVG wireframes, or Figma files unless the user explicitly asks for them.

## Quality Priorities

Optimize in this order:

1. Layout fidelity: keep the same canvas orientation, screen type, major regions, relative positions, hierarchy, and repeated-item counts.
2. Detail preservation: carry forward every deliberate sketch cue: labels, icons, cards, charts, lists, controls, tabs, badges, arrows, separators, imagery blocks, and state indicators.
3. Text accuracy: transcribe legible labels exactly, use meaningful fallback copy for unclear text, and never use placeholder strings like `xx`, `xxx`, `lorem`, `TODO`, or random gibberish.
4. Platform-native interaction style: iOS, Android, Windows, macOS, Web, and WeChat mini-program outputs must use different navigation, controls, density, typography rhythm, and state conventions.
5. High-fidelity realism: make the output look like a real shipped product screenshot with crisp typography, believable data, consistent component states, precise shadows/elevation, polished surfaces, and platform-appropriate density.
6. Whole-image enrichment: fill vague or empty areas with plausible UI micro-details that support the original screen purpose without changing the product concept.
7. Style expression: apply the requested visual direction after the structure and content contract are protected.

## Input Handling

- Require a sketch image, wireframe image, screenshot, or local image path. If the image is a local file path, inspect it with `view_image` first so it is visible in context before generation.
- Treat the sketch as a layout and product-intent reference, not as an edit target that must preserve hand-drawn lines.
- If the user provides no style, use the `simple-tool` preset: clean, practical, lightweight utility UI with restrained visuals and final-grade polish.
- If the user provides an explicit style prompt, honor it over the default and over generic presets. Examples: `二次元`, `anime`, `游戏风`, `game UI`, `cyberpunk`, `pixel art`, `luxury`, or `kids`.
- Ask a question only when there is no usable image, or when an exact brand/style requirement is critical and cannot be inferred.
- When the sketch has multiple screens, generate the requested screen first. If the user asks for a full flow, generate one image per screen or a coherent multi-screen presentation board.

## Workflow

1. Inspect the sketch and make a reconstruction inventory.
   - Identify platform: mobile app, WeChat mini-program, web dashboard, landing page, tablet, desktop app, or unknown.
   - Identify screen purpose, navigation, primary content blocks, controls, data cards, charts, tables, forms, CTAs, imagery zones, and rough hierarchy.
   - Count repeated structures when visible: tabs, list rows, cards, menu items, columns, chart panels, form fields, or bottom-nav items.
   - Note all legible labels and semantic hints. For illegible labels, preserve the role and approximate text length without inventing critical product claims.
   - Note spacing relationships: top/bottom bars, left/right rails, card grouping, hero/content balance, visual weight, and empty zones.

2. Normalize the design style.
   - Convert the user's style words into a compact style brief: visual direction, platform language, palette, typography, component shape, density, imagery/icon treatment, and avoid list.
   - If no style is provided, read `references/style-presets.md` and apply `simple-tool`.
   - If the user names a common style, asks for options, or gives a vivid custom style such as `二次元` or `游戏风`, read `references/style-presets.md` and apply the closest preset while preserving the user's exact style intent.
   - If the platform is named or can be inferred, read `references/platform-conventions.md` and apply the matching platform conventions. Do not let iOS, Android, Windows, macOS, Web, and WeChat mini-program designs collapse into the same generic card UI.
   - If the user gives brand colors, product category, audience, or locale, fold those into the style brief.

3. Build a text and data contract.
   - Extract exact legible text from the sketch or user request. Keep the same language unless the user asks to translate.
   - For unclear text, infer concrete, semantic UI copy from the component role and product context: use real-looking menu names, metric labels, dates, prices, counts, names, IDs, or status values.
   - Never output `xx`, `xxx`, `X`, `--`, `lorem ipsum`, `sample text`, `placeholder`, `TODO`, or nonsense strings as UI content.
   - Use fewer, larger, cleaner text elements when exact copy matters. Prefer crisp meaningful labels over many tiny unreadable labels.
   - Sample numbers must be specific and plausible, for example `128`, `4.8`, `$29.00`, `12 Mar`, `INV-2048`, `98%`, or `3,420`, not vague placeholders.

4. Decide the enrichment plan.
   - Preserve all inventoried structure first.
   - Add realistic product details around the whole image: secondary actions, status chips, avatars, thumbnails, icons, small captions, chart ticks, table metadata, empty-state hints, notification dots, dividers, hover/selected states, and believable sample data.
   - Keep added details subordinate to the sketch. Enrichment should make the same design feel complete, not become a new screen.
   - For sparse sketches, enrich blank zones with domain-appropriate content blocks instead of leaving generic whitespace.

5. Build a GPT image2 prompt.
   - Explicitly say the attached image is the reference for layout and information hierarchy.
   - Include a "fidelity contract" listing the regions, components, counts, labels, and relative positions that must be preserved.
   - Include a "text contract" with exact labels and semantic fallback copy.
   - Request a final-grade, high-detail, realistic UI design screenshot/mockup, not a hand-drawn sketch, lo-fi prototype, concept poster, or generic app illustration.
   - Ask for design-system polish: crisp anti-aliased type, 8pt grid spacing, refined neutral surfaces, subtle depth, consistent iconography, real component states, accessible contrast, and platform-native interaction patterns.
   - Avoid device frames unless the user asks for them.
   - Keep text minimal and legible. Use exact user-provided copy when available; otherwise use short plausible UI labels and concrete sample data.
   - Include strong negative constraints against missing components, generic simplification, blurry/garbled text, placeholder strings, low-detail blocks, wireframe remnants, and decorative drift.

6. Generate with `image_gen`.
   - For one requested style, make one polished design.
   - For style exploration, generate separate variants with clearly different style briefs.
   - If the user asks for a specific aspect ratio or platform, include it in the prompt.

7. Validate and iterate.
   - Compare the output against the reconstruction inventory: region placement, repeated counts, key labels, control types, chart/list/card presence, and hierarchy.
   - Check that text is meaningful, legible, and free of `xx`/placeholder/gibberish. If not, regenerate with a shorter text contract and larger type.
   - Check that the platform language is recognizable: navigation, controls, density, type rhythm, window/chrome behavior, and interaction states should match the target platform.
   - If details are missing, regenerate with a stricter preservation list and explicitly name the omitted elements.
   - If the output is too flat or not UI-like, regenerate emphasizing "final-grade product UI design screenshot", design-system components, real app states, crisp typography, refined material layers, subtle shadows, and believable sample data.
   - If the output adds unrelated concepts, regenerate emphasizing "same product concept, no new primary sections beyond the sketch".
   - If UI text is garbled and exact text matters, regenerate with fewer text elements, larger typography, and exact labels only.

## Prompt Template

Use this structure when calling `image_gen`; fill only the fields that matter:

```text
Transform the attached hand-drawn UI prototype into a final-grade high-fidelity product UI design mockup.

Reference image role: layout, information hierarchy, screen intent, and rough component placement.
Target surface and platform: <iOS app / Android app / WeChat mini-program / web dashboard / landing page / Windows desktop app / macOS app>.
Screen purpose: <what this screen does>.
Design style: <custom style brief or preset-derived style>.
Style priority: <explicit user style if supplied; otherwise simple-tool default>.
Platform interaction style: <platform conventions from references/platform-conventions.md>.
Audience/product context: <optional>.

Fidelity contract from the sketch:
- Canvas and layout: <orientation/aspect ratio, major regions, relative positions>
- Navigation and controls: <tabs, sidebars, bottom nav, buttons, filters, forms>
- Content structures: <cards, lists, tables, charts, imagery blocks, repeated item counts>
- Labels and semantic hints: <exact legible labels; role/length for illegible labels>
- Visual hierarchy: <primary, secondary, tertiary areas and grouping>

Text and data contract:
- Exact legible text: <list exact labels from the sketch/user request>
- Inferred semantic labels for unclear text: <specific labels matching component roles>
- Concrete sample data: <specific numbers, dates, names, IDs, statuses, prices, percentages>
- Text quality: crisp, readable, meaningful UI copy; no `xx`, `xxx`, `X`, `--`, lorem ipsum, placeholder text, TODO text, random characters, or gibberish

Improve:
- precise spacing, alignment, typography, hierarchy, and visual polish
- production-quality components, accessible contrast, consistent iconography
- realistic UI density for the target surface
- crisp anti-aliased text, refined material surfaces, subtle depth/shadows, believable data/content
- platform-native controls, navigation, window/app chrome, hit targets, and interaction states

Whole-image detail expansion:
- enrich vague areas with domain-appropriate micro-details while preserving the same product concept
- add realistic secondary UI details: status chips, avatars, thumbnails, chart ticks, table metadata, dividers, badges, selected states, or helper captions where appropriate
- avoid empty generic blocks unless the sketch intentionally shows empty space

Text policy:
- use exact provided labels when legible or supplied
- otherwise use short plausible UI labels and concrete sample data; avoid long paragraphs
- never use `xx`, `xxx`, lorem ipsum, placeholder strings, or nonsense text

Output constraints:
- final-grade, flat, high-fidelity, highly detailed, realistic product UI design screenshot/mockup only
- no missing major components from the sketch
- no hand-drawn lines, wireframe placeholders, prototype placeholders, construction notes, annotations, watermarks, fake design-tool handles, blurry/garbled text, low-detail generic cards, concept-art styling, poster-like composition, or decorative layout drift
- no device frame unless explicitly requested
```

## Style Customization Rules

- Honor explicit custom style phrases over presets and over the `simple-tool` default.
- When the user says `二次元`/`anime`, use an anime-inspired UI style. When the user says `游戏风`/`game UI`, use a game HUD/menu style. Do not dilute explicit styles back into generic SaaS.
- Keep explicit styles in UI-design form: apply the style to color, typography mood, illustration/icon language, component treatment, and motion/state cues while preserving platform conventions, text accuracy, and layout fidelity.
- Combine compatible requests, for example `iOS + premium fintech + dark mode`.
- If a style could harm usability, keep the mood but preserve accessibility and readable UI hierarchy.
- Never trade structural fidelity for decorative novelty. Apply the style to the existing layout skeleton.
- Use material/detail language that fits the platform: iOS uses native grouped surfaces and tab/navigation bars; Android uses Material 3 patterns; Windows uses Fluent controls and desktop chrome; macOS uses toolbar/sidebar/window conventions; Web dashboards use browser-native density and responsive grids; WeChat uses compact mini-program patterns.
- Do not over-decorate operational products like SaaS, CRM, admin, finance, medical, or dashboards; prioritize dense but organized information and restrained surfaces.
- Avoid making the whole image one hue family. Use a controlled neutral base plus 1-2 accents unless the user requests a branded palette.

## Examples

User: "把这张手绘原型图转成高保真，风格要苹果一点。"
Action: Inspect the attached sketch, create an iOS-native style brief, and call `image_gen` with the sketch as layout reference.

User: "这个线框图生成三版设计图：SaaS、暗黑金融、年轻潮流。"
Action: Read `references/style-presets.md`, then call `image_gen` once per style variant.

User: "输入这张小程序草图，做成微信小程序高保真。"
Action: Use WeChat mini-program conventions, mobile aspect ratio, compact navigation, and production-ready Chinese UI labels when legible.
