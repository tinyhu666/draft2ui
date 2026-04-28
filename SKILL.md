---
name: draft2ui
description: Draft2UI converts hand-drawn UI prototype images, wireframes, rough sketches, paper mockups, low-fidelity app/web layouts, or screenshots/photos of sketches into high-fidelity UI design mockup images with GPT image2 through the built-in image_gen tool. Use when the user asks for Draft2UI, sketch-to-design, draft-to-UI, sketch-to-render, wireframe-to-hi-fi, image2 UI mockup generation, custom design style mockups, "手绘原型图", "草图转高保真", "线框图生成设计图", "低保真转高保真", or "自定义设计图风格".
---

# Draft2UI

## Purpose

Turn a rough UI sketch into a polished, production-looking app or web design image. Preserve the sketch's information hierarchy and intent, then upgrade layout, spacing, typography, color, components, and visual finish.

Use the built-in `image_gen` tool as the default GPT image2 path. Do not create code, HTML, SVG wireframes, or Figma files unless the user explicitly asks for them.

## Input Handling

- Require a sketch image, wireframe image, screenshot, or local image path. If the image is a local file path, inspect it with `view_image` first so it is visible in context before generation.
- Treat the sketch as a layout and product-intent reference, not as an edit target that must preserve hand-drawn lines.
- If the user provides no style, infer a sensible default: clean, modern, commercial, accessible, production-ready UI.
- Ask a question only when there is no usable image, or when an exact brand/style requirement is critical and cannot be inferred.
- When the sketch has multiple screens, generate the requested screen first. If the user asks for a full flow, generate one image per screen or a coherent multi-screen presentation board.

## Workflow

1. Inspect the sketch.
   - Identify platform: mobile app, WeChat mini-program, web dashboard, landing page, tablet, desktop app, or unknown.
   - Identify screen purpose, navigation, primary content blocks, controls, data cards, forms, CTAs, and rough hierarchy.
   - Note unclear or illegible labels without inventing critical product claims.

2. Normalize the design style.
   - Convert the user's style words into a compact style brief: visual direction, platform language, palette, typography, component shape, density, imagery/icon treatment, and avoid list.
   - If the user names a common style or asks for options, read `references/style-presets.md` and apply the closest preset.
   - If the user gives brand colors, product category, audience, or locale, fold those into the style brief.

3. Build a GPT image2 prompt.
   - Explicitly say the attached image is the reference for layout and information hierarchy.
   - Preserve the sketch's rough structure while improving alignment, spacing, visual rhythm, hierarchy, and component polish.
   - Request a high-fidelity flat UI screenshot/mockup, not a hand-drawn sketch.
   - Avoid device frames unless the user asks for them.
   - Keep text minimal and legible. Use exact user-provided copy when available; otherwise use short plausible UI labels.

4. Generate with `image_gen`.
   - For one requested style, make one polished design.
   - For style exploration, generate separate variants with clearly different style briefs.
   - If the user asks for a specific aspect ratio or platform, include it in the prompt.

5. Validate and iterate.
   - Check that the output follows the sketch's structure, target platform, style, and key content.
   - If the result drifts from the sketch, run one targeted regeneration emphasizing preservation.
   - If UI text is garbled and exact text matters, regenerate with fewer text elements and larger typography.

## Prompt Template

Use this structure when calling `image_gen`; fill only the fields that matter:

```text
Transform the attached hand-drawn UI prototype into a high-fidelity product design mockup.

Reference image role: layout, information hierarchy, screen intent, and rough component placement.
Target surface: <mobile app / WeChat mini-program / web dashboard / landing page / desktop app>.
Screen purpose: <what this screen does>.
Design style: <custom style brief or preset-derived style>.
Audience/product context: <optional>.

Preserve from sketch:
- <major layout regions>
- <navigation / CTAs / forms / cards / lists>
- <relative hierarchy and content grouping>

Improve:
- precise spacing, alignment, typography, hierarchy, and visual polish
- production-quality components, accessible contrast, consistent iconography
- realistic UI density for the target surface

Text policy:
- use exact provided labels when legible or supplied
- otherwise use short plausible UI labels; avoid long paragraphs

Output constraints:
- flat high-fidelity UI screenshot/mockup only
- no hand-drawn lines, wireframe placeholders, construction notes, annotations, watermarks, or fake design-tool handles
- no device frame unless explicitly requested
```

## Style Customization Rules

- Honor explicit custom style phrases over presets.
- Combine compatible requests, for example `iOS + premium fintech + dark mode`.
- If a style could harm usability, keep the mood but preserve accessibility and readable UI hierarchy.
- Do not over-decorate operational products like SaaS, CRM, admin, finance, medical, or dashboards; prioritize dense but organized information and restrained surfaces.
- Avoid making the whole image one hue family. Use a controlled neutral base plus 1-2 accents unless the user requests a branded palette.

## Examples

User: "把这张手绘原型图转成高保真，风格要苹果一点。"
Action: Inspect the attached sketch, create an iOS-native style brief, and call `image_gen` with the sketch as layout reference.

User: "这个线框图生成三版设计图：SaaS、暗黑金融、年轻潮流。"
Action: Read `references/style-presets.md`, then call `image_gen` once per style variant.

User: "输入这张小程序草图，做成微信小程序高保真。"
Action: Use WeChat mini-program conventions, mobile aspect ratio, compact navigation, and production-ready Chinese UI labels when legible.
