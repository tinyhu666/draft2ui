# Platform Conventions

Load this file when the target platform is named, implied by the sketch, or important to visual fidelity. Apply these conventions after preserving the sketch structure.

## iOS

- Use iOS-native navigation: large title or compact navigation bar, bottom tab bar for primary sections, segmented controls for mode switching, sheet-style modals, grouped list surfaces.
- Use soft grouped backgrounds, SF-like typography rhythm, rounded native controls, standard status/action affordances, and generous mobile touch targets.
- Avoid Android-style floating action buttons, Windows desktop chrome, generic web sidebars, or over-dense table UI unless the sketch explicitly requires them.

## Android

- Use Material 3 conventions: top app bar, navigation bar or navigation rail, FAB when there is one primary creation action, cards with tonal surfaces, chips, snackbars, menus, and clear state layers.
- Use Roboto-like typography rhythm, expressive but controlled color roles, accessible contrast, and Android-style system spacing.
- Avoid iOS large-title/grouped-list styling, macOS window chrome, or purely web-dashboard components for native Android screens.

## Windows

- Use Fluent-style desktop UI: command bar/ribbon-style actions where appropriate, left navigation pane, title bar/window chrome, acrylic or mica-like surfaces, subtle borders, menus, tabs, data grids, and status bars.
- Favor dense but readable desktop layouts, keyboard/mouse affordances, hover/focus states, resizable panes, and clear table/list behavior.
- Avoid mobile bottom tabs, oversized touch-only controls, or macOS traffic-light window controls.

## macOS

- Use macOS app conventions: traffic-light window controls, unified toolbar, sidebar/source list, split views, inspector panels, segmented controls, popovers, sheets, and menu-oriented actions.
- Favor refined neutral materials, compact desktop density, crisp typography, subtle vibrancy, and precise alignment.
- Avoid Windows ribbon/chrome, Android FABs, mobile bottom tabs, or browser-dashboard framing unless explicitly requested.

## Web Dashboard

- Use responsive web app conventions: left sidebar or top navigation, breadcrumb/page title, filters, table/card grids, command buttons, pagination, search, toasts, modals, and clear loading/empty/error states.
- Favor browser-like density, scalable layouts, keyboard/mouse hover states, accessible contrast, and production SaaS component polish.
- Avoid pretending it is a native mobile app unless the target surface is mobile web.

## WeChat Mini-Program

- Use familiar mini-program structure: compact top bar, simple page title, list/form patterns, restrained icons, sticky action footer, simple bottom navigation when needed, Chinese labels when the sketch/user context is Chinese.
- Favor lightweight mobile density, direct task flows, and WeChat-like hierarchy rather than heavy native iOS/Android ornament.
- Avoid desktop dashboard chrome, overly complex navigation, or generic western SaaS styling.

## Cross-Platform Text Rules

- Keep UI text in one coherent locale unless the user asks for bilingual output.
- Use exact legible text from the sketch. For unclear text, infer concrete labels from context, for example `Today`, `Orders`, `Revenue`, `Active`, `Settings`, `完成`, `订单`, `收入`, or `设置`.
- Use specific sample data: realistic numbers, IDs, dates, times, percentages, prices, statuses, and names.
- Never use `xx`, `xxx`, `X`, `--`, `lorem ipsum`, `placeholder`, `sample text`, `TODO`, random letters, or fake unreadable strings.
