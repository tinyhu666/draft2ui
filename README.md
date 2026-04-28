# Draft2UI

Draft2UI is a Codex skill for turning hand-drawn UI sketches, wireframes, paper mockups, low-fidelity layouts, or screenshots of prototypes into faithful, final-grade UI design mockups with the built-in `image_gen` tool.

It is optimized for one practical goal: preserve the user's sketch while making the result look like a real product UI design, not a cleaned-up prototype.

## What It Does

- Restores the original layout, hierarchy, component counts, and screen intent.
- Preserves visible UI cues such as labels, cards, lists, charts, forms, tabs, badges, imagery blocks, and state indicators.
- Produces final-grade UI design screenshots with crisp typography, polished surfaces, realistic data, and design-system-level details.
- Avoids placeholder text like `xx`, `xxx`, `lorem ipsum`, `TODO`, and random unreadable strings.
- Uses platform-native conventions for iOS, Android, Windows, macOS, Web dashboards, and WeChat mini-programs.
- Supports explicit visual styles such as `二次元`, `游戏风`, `cyberpunk`, `luxury`, `kids`, and more.

## Install

Clone the repository and copy it into your Codex skills directory:

```bash
git clone https://github.com/tinyhu666/draft2ui.git
mkdir -p ~/.codex/skills/draft2ui
rsync -a --delete --exclude='.git' draft2ui/ ~/.codex/skills/draft2ui/
```

Restart Codex after installing or updating the skill.

## Update

```bash
cd draft2ui
git pull
rsync -a --delete --exclude='.git' ./ ~/.codex/skills/draft2ui/
```

## Usage

Attach or provide a sketch image, then ask Codex to use the skill:

```text
Use $draft2ui to turn this hand-drawn prototype into a final-grade UI design.
```

Chinese examples:

```text
Use $draft2ui 把这张手绘原型图转成高保真 UI，默认简单工具风。
Use $draft2ui 把这张线框图做成 iOS 风格的正式设计图。
Use $draft2ui 生成二次元风格，但保留原图布局和文字语义。
Use $draft2ui 做成游戏风 HUD UI，不要出现 xx 或占位文字。
```

## Default Style

If no style is provided, Draft2UI uses `simple-tool`:

- clean and practical
- lightweight utility feel
- low decoration
- compact controls
- crisp meaningful text
- concrete sample data
- final-grade product polish

If the user provides an explicit style prompt, that style takes priority over the default.

## Built-In Styles

| Preset | Best For |
| --- | --- |
| `simple-tool` | Default practical utility UI |
| `clean-saas` | B2B SaaS and admin products |
| `enterprise-dashboard` | Dense dashboards and operations tools |
| `ai-assistant-tool` | AI workflow and generation tools |
| `developer-console` | API, logs, devtools, technical consoles |
| `productivity-workspace` | Notes, tasks, calendar, workspace apps |
| `creator-studio` | Media editors, creator tools, asset workflows |
| `education-learning` | Courses, lessons, quizzes, learning platforms |
| `social-community` | Social feeds, communities, messaging |
| `travel-local` | Travel, maps, local discovery |
| `food-service` | Restaurant, delivery, booking |
| `gaming-hud` | Game UI, HUD, mission, inventory, reward screens |
| `anime-inspired` | Anime, ACG, 二次元 UI |
| `cyberpunk-neon` | Futuristic dark neon interfaces |
| `luxury-premium` | High-end premium product UI |
| `kids-friendly` | Child-friendly, large-target, warm UI |
| `ios-native` | iOS app screens |
| `material-you` | Android and Material 3 UI |
| `wechat-mini-program` | WeChat mini-program UI |
| `premium-fintech` | Finance and investment products |
| `healthcare-calm` | Medical, wellness, care products |
| `ecommerce-polished` | Catalog, product detail, checkout |
| `youthful-consumer` | Young consumer apps |
| `minimal-editorial` | Sparse premium editorial layouts |

## Explicit Style Mapping

- `二次元`, `anime`, `ACG` -> `anime-inspired`
- `游戏风`, `game`, `game UI`, `HUD` -> `gaming-hud`
- `赛博朋克`, `cyberpunk`, `neon` -> `cyberpunk-neon`
- `像工具`, `简单工具`, `utility`, no explicit style -> `simple-tool`
- `高端`, `奢华`, `luxury`, `premium` -> `luxury-premium`
- `儿童`, `kids`, `toy-like` -> `kids-friendly`

## Platform Conventions

Draft2UI keeps visual style and platform behavior separate:

- iOS uses native navigation bars, tab bars, grouped surfaces, segmented controls, and iOS-like type rhythm.
- Android uses Material 3 top bars, navigation bars or rails, FABs, chips, state layers, and Android spacing.
- Windows uses Fluent-style desktop chrome, navigation panes, command bars, data grids, hover/focus states, and dense desktop controls.
- macOS uses traffic-light window controls, unified toolbars, sidebars, split views, inspector panels, sheets, and popovers.
- Web dashboards use responsive layouts, sidebars or top navigation, filters, tables, modals, toasts, and browser-like density.
- WeChat mini-programs use compact mobile structure, familiar list/form patterns, sticky action footers, and Chinese labels when appropriate.

See `references/platform-conventions.md` for the detailed rules.

## Quality Contract

Draft2UI prompts the image model to follow this order:

1. Preserve layout fidelity.
2. Preserve visible details.
3. Keep text meaningful and accurate.
4. Apply platform-native interaction style.
5. Improve realism and UI texture.
6. Enrich vague areas with plausible product details.
7. Apply the requested visual style.

The skill should generate a design-standard UI image, not a wireframe, not a lo-fi prototype, and not a decorative poster.

## Repository Structure

```text
draft2ui/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── platform-conventions.md
    └── style-presets.md
```

## Notes

- Draft2UI generates images. It does not create HTML, React, Figma files, or SVG wireframes unless the user explicitly asks for those.
- Exact text in sketches is preserved when legible. Unclear text is replaced with semantic UI copy and concrete sample data.
- Explicit user style always wins over the default style.
