---
name: draft2ui
description: Use when the user asks for Draft2UI, sketch-to-design, draft-to-UI, sketch-to-render, wireframe-to-hi-fi, image2 UI mockup generation, custom UI style mockups, or high-fidelity restoration from hand-drawn UI prototype images, wireframes, rough sketches, paper mockups, low-fidelity app/web layouts, screenshots, or photos of sketches; includes "手绘原型图", "草图转高保真", "线框图生成设计图", "低保真转高保真", and "自定义设计图风格".
---

# Draft2UI

## Purpose

Turn a rough UI sketch into a faithful, detailed, production-looking app or web design image. Preserve the sketch's information hierarchy, layout intent, and visible detail cues, then upgrade spacing, typography, color, components, realism, and visual finish.

Use the built-in `image_gen` tool as the default GPT image2 path. Do not create code, HTML, SVG wireframes, or Figma files unless the user explicitly asks for them.

## Quality Priorities

Optimize in this order:

1. Layout fidelity: keep the same canvas orientation, screen type, major regions, relative positions, hierarchy, and repeated-item counts.
2. Detail preservation: carry forward every deliberate sketch cue: labels, icons, cards, charts, lists, controls, tabs, badges, arrows, separators, imagery blocks, and state indicators.
3. High-fidelity realism: make the output look like a real shipped product screenshot with crisp typography, believable data, consistent component states, precise shadows/elevation, polished surfaces, and platform-appropriate density.
4. Whole-image enrichment: fill vague or empty areas with plausible UI micro-details that support the original screen purpose without changing the product concept.
5. Style expression: apply the requested visual direction after the structure and content contract are protected.

## Input Handling

- Require a sketch image, wireframe image, screenshot, or local image path. If the image is a local file path, inspect it with `view_image` first so it is visible in context before generation.
- Treat the sketch as a layout and product-intent reference, not as an edit target that must preserve hand-drawn lines.
- If the user provides no style, infer a sensible default: clean, modern, commercial, accessible, highly detailed, production-ready UI.
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
   - If the user names a common style or asks for options, read `references/style-presets.md` and apply the closest preset.
   - If the user gives brand colors, product category, audience, or locale, fold those into the style brief.

3. Decide the enrichment plan.
   - Preserve all inventoried structure first.
   - Add realistic product details around the whole image: secondary actions, status chips, avatars, thumbnails, icons, small captions, chart ticks, table metadata, empty-state hints, notification dots, dividers, hover/selected states, and believable sample data.
   - Keep added details subordinate to the sketch. Enrichment should make the same design feel complete, not become a new screen.
   - For sparse sketches, enrich blank zones with domain-appropriate content blocks instead of leaving generic whitespace.

4. Build a GPT image2 prompt.
   - Explicitly say the attached image is the reference for layout and information hierarchy.
   - Include a "fidelity contract" listing the regions, components, counts, labels, and relative positions that must be preserved.
   - Request a high-fidelity, high-detail, realistic flat UI screenshot/mockup, not a hand-drawn sketch.
   - Ask for polished materials: crisp anti-aliased type, refined neutral surfaces, subtle depth, consistent iconography, realistic data/content, and platform-native component states.
   - Avoid device frames unless the user asks for them.
   - Keep text minimal and legible. Use exact user-provided copy when available; otherwise use short plausible UI labels.
   - Include strong negative constraints against missing components, generic simplification, blurry text, low-detail placeholders, wireframe remnants, and decorative drift.

5. Generate with `image_gen`.
   - For one requested style, make one polished design.
   - For style exploration, generate separate variants with clearly different style briefs.
   - If the user asks for a specific aspect ratio or platform, include it in the prompt.

6. Validate and iterate.
   - Compare the output against the reconstruction inventory: region placement, repeated counts, key labels, control types, chart/list/card presence, and hierarchy.
   - If details are missing, regenerate with a stricter preservation list and explicitly name the omitted elements.
   - If the output is too flat, regenerate emphasizing "real shipped product screenshot", refined material layers, crisp typography, subtle shadows, and believable sample data.
   - If the output adds unrelated concepts, regenerate emphasizing "same product concept, no new primary sections beyond the sketch".
   - If UI text is garbled and exact text matters, regenerate with fewer text elements, larger typography, and exact labels only.

## Prompt Template

Use this structure when calling `image_gen`; fill only the fields that matter:

```text
Transform the attached hand-drawn UI prototype into a high-fidelity product design mockup.

Reference image role: layout, information hierarchy, screen intent, and rough component placement.
Target surface: <mobile app / WeChat mini-program / web dashboard / landing page / desktop app>.
Screen purpose: <what this screen does>.
Design style: <custom style brief or preset-derived style>.
Audience/product context: <optional>.

Fidelity contract from the sketch:
- Canvas and layout: <orientation/aspect ratio, major regions, relative positions>
- Navigation and controls: <tabs, sidebars, bottom nav, buttons, filters, forms>
- Content structures: <cards, lists, tables, charts, imagery blocks, repeated item counts>
- Labels and semantic hints: <exact legible labels; role/length for illegible labels>
- Visual hierarchy: <primary, secondary, tertiary areas and grouping>

Improve:
- precise spacing, alignment, typography, hierarchy, and visual polish
- production-quality components, accessible contrast, consistent iconography
- realistic UI density for the target surface
- crisp anti-aliased text, refined material surfaces, subtle depth/shadows, believable data/content

Whole-image detail expansion:
- enrich vague areas with domain-appropriate micro-details while preserving the same product concept
- add realistic secondary UI details: status chips, avatars, thumbnails, chart ticks, table metadata, dividers, badges, selected states, or helper captions where appropriate
- avoid empty generic blocks unless the sketch intentionally shows empty space

Text policy:
- use exact provided labels when legible or supplied
- otherwise use short plausible UI labels; avoid long paragraphs

Output constraints:
- flat, high-fidelity, highly detailed, realistic UI screenshot/mockup only
- no missing major components from the sketch
- no hand-drawn lines, wireframe placeholders, construction notes, annotations, watermarks, fake design-tool handles, blurry text, low-detail generic cards, or decorative layout drift
- no device frame unless explicitly requested
```

## Style Customization Rules

- Honor explicit custom style phrases over presets.
- Combine compatible requests, for example `iOS + premium fintech + dark mode`.
- If a style could harm usability, keep the mood but preserve accessibility and readable UI hierarchy.
- Never trade structural fidelity for decorative novelty. Apply the style to the existing layout skeleton.
- Use material/detail language that fits the platform: native mobile surfaces for apps, restrained density for dashboards, editorial polish for landing pages, and familiar compact patterns for mini-programs.
- Do not over-decorate operational products like SaaS, CRM, admin, finance, medical, or dashboards; prioritize dense but organized information and restrained surfaces.
- Avoid making the whole image one hue family. Use a controlled neutral base plus 1-2 accents unless the user requests a branded palette.

## Examples

User: "把这张手绘原型图转成高保真，风格要苹果一点。"
Action: Inspect the attached sketch, create an iOS-native style brief, and call `image_gen` with the sketch as layout reference.

User: "这个线框图生成三版设计图：SaaS、暗黑金融、年轻潮流。"
Action: Read `references/style-presets.md`, then call `image_gen` once per style variant.

User: "输入这张小程序草图，做成微信小程序高保真。"
Action: Use WeChat mini-program conventions, mobile aspect ratio, compact navigation, and production-ready Chinese UI labels when legible.
