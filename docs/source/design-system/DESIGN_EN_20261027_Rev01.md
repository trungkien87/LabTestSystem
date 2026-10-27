# DESIGN.md — Calm Infrastructure

**Version:** 20261027 Rev.01 · **Status:** Approved (2026-10-27)

> A neutral, enterprise-grade design system for data, storage, networking and IT-infrastructure products.
> Monochrome-first, one disciplined blue for interaction, a teal companion for assurance, and warm colors only for alerts.

**Source basis.** Values marked **[Source]** are taken from a public corporate design guideline (colors, typography, iconography, illustration, photography, diagram rules). All brand names, logos, product names and product-specific palettes have been removed and roles renamed. Sections marked **[Derived]** (components, spacing scale, elevation, responsive) are *not* defined in the source guideline; they are proposed extensions built to stay consistent with the source rules. Contrast ratios marked **[Computed]** were calculated with the WCAG 2.x relative-luminance formula.

---

## 1. Visual Theme & Atmosphere

- **Mood:** stable, reliable, professional. The interface should feel like well-run infrastructure — quiet, precise, trustworthy.
- **Color philosophy:** black, white and gray carry the overwhelming majority of every surface. Color is a *signal*, not decoration. **[Source]**
- **Accent discipline:** Primary Blue means *emphasis, interactivity, assurance*. Accent Teal complements it for an extra layer of meaning. Warm colors (yellow/orange/red) appear only for warnings and errors. **[Source]**
- **Density:** medium. Content-first layouts with generous whitespace for marketing pages; compact, data-dense tables for admin consoles. **[Derived]**
- **Personality balance:** approachable but competent — moderate friendliness (rounded 2px icon corners, light hand-drawn spot illustrations) never at the expense of professionalism. **[Source]**
- **No gradients** on text or icons. Flat color only. **[Source]**

---

## 2. Color Palette & Roles

### 2.1 Core roles **[Source]** (role names neutralized)

| Token | Hex | RGB | Role |
|---|---|---|---|
| `--color-black` | `#000000` | 0 0 0 | Primary text, dark backgrounds |
| `--color-white` | `#FFFFFF` | 255 255 255 | Page background, text on dark |
| `--color-primary` (Blue-6) | `#0067E6` | 0 103 230 | Interactive elements, links, highlights, key icons |
| `--color-accent` (Green-6) | `#26D4AC` | 38 212 172 | Complements primary: success/assurance, secondary emphasis |
| `--color-secondary-indigo` (Purple-6) | `#3743DD` | 55 67 221 | Illustration only |
| `--color-secondary-cyan` (Light-blue-6) | `#16B8E8` | 22 184 232 | Illustration only |
| `--color-warning` (Yellow-6) | `#FCBF1D` | 252 191 29 | Warning (fills, icons) |
| `--color-caution` (Orange-6) | `#F57000` | 245 112 0 | Elevated warning (fills, icons) |
| `--color-danger` (Red-6) | `#F53C3C` | 245 60 60 | Error, destructive (fills, icons) |

### 2.2 Full tonal scales **[Source]**

Each family runs 1 (lightest) → 10 (darkest). **Value 6 is the main color and is always the first choice**; 1–5 and 7–10 are supporting tints/shades.

| Step | Gray | Cold-gray | Purple | Blue | Light-blue | Green | Yellow | Orange | Red |
|---|---|---|---|---|---|---|---|---|---|
| 1 | `#F5F5F5` | `#F0F2F5` | `#EBEFFF` | `#E6F5FF` | `#E6FDFF` | `#F0FFFA` | `#FFFDEB` | `#FFF5E6` | `#FFF2F0` |
| 2 | `#E6E6E6` | `#DFE1E6` | `#CFD8FA` | `#C2E6FF` | `#BDF9FF` | `#D4FFF1` | `#FFF7C2` | `#FFE7C4` | `#FFE6E3` |
| 3 | `#CFCFCF` | `#C7CBD1` | `#A5B5FA` | `#8CCBFF` | `#91F0FF` | `#A5FADE` | `#FFEE99` | `#FFC987` | `#FFC3BD` |
| 4 | `#B5B5B5` | `#A7AEB8` | `#798DFC` | `#5CB0FF` | `#65DFF7` | `#77EDCA` | `#FFE270` | `#FFAB52` | `#FF968F` |
| 5 | `#8F8F8F` | `#808791` | `#4E65E6` | `#2789F2` | `#3DCEF2` | `#4CE0B9` | `#FFD447` | `#FF9029` | `#FA6761` |
| **6** | **`#666666`** | **`#5F6670`** | **`#3743DD`** | **`#0067E6`** | **`#16B8E8`** | **`#26D4AC`** | **`#FCBF1D`** | **`#F57000`** | **`#F53C3C`** |
| 7 | `#545454` | `#474D57` | `#252AB8` | `#0050BF` | `#0890C2` | `#18AD90` | `#D1970F` | `#CF5600` | `#CF272D` |
| 8 | `#404040` | `#333842` | `#161691` | `#003B99` | `#006996` | `#0D826F` | `#A67003` | `#A84100` | `#A81821` |
| 9 | `#303030` | `#2B2D33` | `#0E0B6B` | `#002873` | `#00496E` | `#04594E` | `#754A00` | `#7A2B00` | `#820C18` |
| 10 | `#1C1C1C` | `#1A1C1F` | `#0A0645` | `#00184D` | `#00304D` | `#023630` | `#4A2C00` | `#4A1B00` | `#4A060C` |

### 2.3 Semantic UI tokens **[Derived]** (mapped onto the source palette)

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg-page` | `#FFFFFF` | `#1C1C1C` (Gray-10) | Page canvas |
| `--bg-subtle` | `#F5F5F5` (Gray-1) | `#303030` (Gray-9) | Section bands, table header |
| `--bg-panel` | `#F0F2F5` (Cold-gray-1) | `#2B2D33` (Cold-gray-9) | Sidebars, admin panels |
| `--border` | `#E6E6E6` (Gray-2) | `#404040` (Gray-8) | Dividers, card borders |
| `--border-strong` | `#CFCFCF` (Gray-3) | `#545454` (Gray-7) | Input borders |
| `--text-primary` | `#000000` / `#1C1C1C` | `#FFFFFF` | Body, headings |
| `--text-secondary` | `#666666` (Gray-6) | `#CFCFCF` (Gray-3) | Captions, meta |
| `--text-disabled` | `#8F8F8F` (Gray-5) | `#8F8F8F` | Disabled/placeholder only |
| `--interactive` | `#0067E6` (Blue-6) | `#5CB0FF` (Blue-4) | Links, primary buttons |
| `--interactive-hover` | `#0050BF` (Blue-7) | `#8CCBFF` (Blue-3) | Hover |
| `--interactive-active` | `#003B99` (Blue-8) | `#C2E6FF` (Blue-2) | Pressed |
| `--focus-ring` | `#5CB0FF` (Blue-4) | `#5CB0FF` | 2px focus outline |
| `--success` | `#0D826F` (Green-8) text · `#26D4AC` fill | `#77EDCA` (Green-4) | Success |
| `--warning-text` | `#754A00` (Yellow-9) | `#FFD447` (Yellow-5) | Warning text |
| `--danger-text` | `#CF272D` (Red-7) | `#FF968F` (Red-4) | Error text |

### 2.4 Usage proportion **[Source]**

- Neutrals (black/white/gray) = the **majority** of every composition.
- Primary Blue: thoughtful and moderate — only where it carries meaning.
- Accent Teal: only alongside Blue, to add meaning.
- Tertiary (yellow/orange/red): **≤ 5%** of any composition.
- Illustrations: gray sets the tone, blue highlights the core message; secondary colors occasionally.

### 2.5 Contrast **[Source + Computed]**

Target: WCAG AA, **4.5:1** for text below 18 pt. **[Source]**

| Pair | Ratio **[Computed]** | Verdict for body text |
|---|---|---|
| White on Blue-6 `#0067E6` | 5.14:1 | ✅ |
| Blue-6 on Gray-1 `#F5F5F5` | 4.72:1 | ✅ (margin is thin) |
| Gray-6 `#666666` on white | 5.74:1 | ✅ |
| Gray-5 `#8F8F8F` on white | 3.23:1 | ❌ — disabled/placeholder only |
| Cold-gray-5 `#808791` on white | 3.63:1 | ❌ |
| Green-6 `#26D4AC` on white | 1.89:1 | ❌ — never as text on light; black on Green-6 = 11.1:1 ✅ |
| Green-8 `#0D826F` on white | 4.73:1 | ✅ |
| Red-6 `#F53C3C` on white | 3.75:1 | ❌ — use Red-7 `#CF272D` (5.27:1) for text |
| Orange-6 `#F57000` on white | 2.92:1 | ❌ — use Orange-8 `#A84100` (6.14:1) |
| Black on Yellow-6 `#FCBF1D` | 12.61:1 | ✅ (yellow is a fill, never a text color on white) |
| Blue-4 `#5CB0FF` on Gray-10 | 7.39:1 | ✅ dark-mode link |

---

## 3. Typography Rules

### 3.1 Families **[Source]**

| Script | Family | CSS stack |
|---|---|---|
| Latin, Vietnamese, Cyrillic, Greek | **Inter** (open-source, 9 weights / 18 styles) | `"Inter", system-ui, -apple-system, "Segoe UI", Roboto, sans-serif` |
| Traditional Chinese | Noto Sans TC (fallback Microsoft JhengHei) | `"Inter", "Noto Sans TC", "Microsoft JhengHei", sans-serif` |
| Simplified Chinese | Noto Sans SC | `"Inter", "Noto Sans SC", sans-serif` |
| Japanese | Noto Sans JP | `"Inter", "Noto Sans JP", sans-serif` |
| Korean | Noto Sans KR | `"Inter", "Noto Sans KR", sans-serif` |
| Thai | Kanit | `"Inter", "Kanit", sans-serif` |
| Code / data | **[Derived]** | `ui-monospace, "SFMono-Regular", Menlo, Consolas, monospace` |

Always use the Noto Sans family that matches the language — glyph strokes and punctuation placement differ between scripts. **[Source]**

### 3.2 Hierarchy **[Derived sizes; line-height ranges are Source]**

Source line-height rules: headlines **1.15–1.25×**, subheadings **1.25–1.5×**, body **1.5–1.6×**. Smaller text → larger line-height.

| Role | Size | Weight | Line-height | Letter-spacing |
|---|---|---|---|---|
| Display | 56px | 700 | 1.15 | -0.02em |
| H1 | 40px | 700 | 1.2 | -0.015em |
| H2 | 32px | 600 | 1.2 | -0.01em |
| H3 | 24px | 600 | 1.25 | 0 |
| H4 / Subheading | 20px | 600 | 1.35 | 0 |
| Lead | 18px | 400 | 1.5 | 0 |
| Body | 16px | 400 | 1.6 | 0 |
| Body small | 14px | 400 | 1.6 | 0 |
| Caption / meta | 12px | 500 | 1.5 | 0.01em |
| Button / label | 14–16px | 600 | 1.25 | 0 |

### 3.3 Spacing, measure, alignment **[Source]**

- Spacing order, small → large: letter < word < line < **paragraph**. Paragraph spacing must always exceed line spacing.
- Letter spacing never loose; line spacing never tight.
- Line length: body **40–70 characters** (≈7–15 English words); short texts **30–40 characters**. Implement as `max-width: 65ch` (body) / `38ch` (short). **[Derived CSS]**
- Alignment: **flush left** by default; **centered** only for short groupings (hero headline, short card copy). Never center long text.

### 3.4 Text color **[Source]**

- Text uses only black, white and the two gray families.
- Primary Blue for highlights (raise weight if needed) and for interactive text.
- Warm colors only for warnings/errors.
- No gradient text; no blue without a reason.

---

## 4. Component Stylings **[Derived]**

> Not specified by the source. Built to respect: neutral-dominant color, blue = interactive, 2px corner language, flat surfaces.

**Radius scale:** `--radius-xs: 2px` (tags, icon shapes) · `--radius-sm: 4px` (buttons, inputs) · `--radius-md: 8px` (cards, menus) · `--radius-lg: 12px` (modals). No pill shapes except status chips.

### Buttons

| Variant | Default | Hover | Active | Disabled |
|---|---|---|---|---|
| Primary | bg `#0067E6`, text `#FFFFFF` | bg `#0050BF` | bg `#003B99` | bg `#E6E6E6`, text `#8F8F8F` |
| Secondary | bg `#FFFFFF`, 1px `#CFCFCF`, text `#000000` | bg `#F5F5F5` | bg `#E6E6E6` | text `#8F8F8F` |
| Ghost / text | transparent, text `#0067E6` | bg `#E6F5FF` | bg `#C2E6FF` | text `#8F8F8F` |
| Danger | bg `#CF272D`, text `#FFFFFF` | bg `#A81821` | bg `#820C18` | as primary disabled |

- Height 40px (default), 32px (compact/table), 48px (marketing CTA). Padding 0 16px / 0 12px / 0 24px. Radius 4px.
- Focus: `outline: 2px solid #5CB0FF; outline-offset: 2px`.
- One primary button per view region.

### Inputs

- Height 40px, padding 0 12px, radius 4px, border 1px `#CFCFCF`, bg `#FFFFFF`, text 16px.
- Hover border `#8F8F8F`; focus border `#0067E6` + 2px `#5CB0FF` ring; error border `#CF272D` + helper text `#CF272D` 14px.
- Labels above field, 14px / 600, `#000000`; helper 12–14px `#666666`.

### Cards

- bg `#FFFFFF`, border 1px `#E6E6E6`, radius 8px, padding 24px, no shadow at rest.
- Hover (when clickable): border `#CFCFCF` + `--shadow-1`.
- Feature card: 64px spot icon **above** the headline, left- or center-aligned; never below the headline.

### Navigation

- Top bar 64px, bg `#FFFFFF`, bottom border 1px `#E6E6E6`. Items 16px / 500 `#000000`; active item `#0067E6` with 2px bottom indicator.
- Admin sidebar 240px, bg `#F0F2F5`; active row bg `#E6F5FF`, text `#0067E6`, 20px system icon left of label.

### Tables (data-dense)

- Header bg `#F5F5F5`, 14px / 600 `#666666`; row height 48px (40px compact); row divider 1px `#E6E6E6`; hover row `#F0F2F5`; numbers right-aligned, tabular figures (`font-feature-settings: "tnum"`).

### Status chips / alerts

| Status | Background | Text / icon |
|---|---|---|
| Info | `#E6F5FF` | `#0050BF` |
| Success | `#F0FFFA` | `#0D826F` |
| Warning | `#FFFDEB` | `#754A00` |
| Caution | `#FFF5E6` | `#A84100` |
| Error | `#FFF2F0` | `#CF272D` |

Alerts: 4px left border in the family's step-6 color, radius 4px, padding 12px 16px.

### Iconography **[Source]**

- **Types:** *Spot icons* support text (32px and 64px); *system icons* aid UI (20px).
- **Grids:** 64×64, 32×32, 20×20px, each with **2px padding** on all sides; draw in the live area, may extend into padding for optical balance. Use keylines for circles/squares/rectangles.
- **Stroke:** **2px**, center-aligned, pixel-perfect, **square terminals** (no round caps).
- **Corners:** outline style, **2px corner radius**; arrows and check marks use **sharp** corners. Add small filled shapes for balance.
- **Angles:** 45° increments first, 15° increments when needed.
- **Color:** 1 color (usually = text color) or max 2 to strengthen meaning; no color fills of the whole icon; no gradients.
- **Placement:** spot-32 to the **left** of a paragraph (no horizontal centering, not under a headline); spot-64 **above** a headline (never left of text, never without a headline); system icons beside or below text, may be centered, never above text.
- **Principles:** concise, concrete, competent, consistent — one icon per concept.

---

## 5. Layout Principles **[Derived unless noted]**

- **Base unit:** 4px (aligns with the 2px icon padding and 20/32/64px icon grids).
- **Spacing scale:** `4, 8, 12, 16, 24, 32, 48, 64, 96, 128` px.
- **Grid:** 12 columns, max content width 1200px, gutter 24px (desktop) / 16px (mobile), side margin ≥ 16px.
- **Section rhythm:** 96px vertical padding (desktop marketing), 64px (tablet), 48px (mobile); 24px inside cards; 16px between related form fields.
- **Whitespace:** neutral backgrounds and generous whitespace do the work; separate sections with `#F5F5F5` bands rather than color blocks.
- **Media aspect ratios [Source]:** 1:1, 3:2, 4:3, 16:9 (landscape or portrait) for photos and illustrations.
- **Text measure [Source]:** see §3.3.

### Imagery **[Source]**

- **Photography types:** contextual (people benefiting from the product, with enough context), still-life (hardware detail, UI on laptop/tablet/phone), abstract (visualizing speed, scale and other non-physical ideas).
- Professional, clearly themed, inclusive and locally appropriate models. Avoid unnatural lighting/flare, stock overlays, obvious posing, off-palette colors, unnatural contrast, compositions without a focal point.
- **Illustration:** spot illustrations are hand-drawn with textured strokes to soften technical topics; product illustrations are compact and minimalist. Gray base + blue highlight; other families sparingly.

### Network / architecture diagrams **[Source]**

- **Type A (standardized):** canvas **900px** wide. Core product/service shapes in **Primary Blue**; third-party devices in **Cold-gray-2 `#DFE1E6`**. Uniform label size **15pt**, black or white. All strokes **1pt**. Relationships = **solid black lines with arrowheads**, arrowhead aspect **1:2**, always leave a gap before the target. Grouping = **Cold-gray-4 `#A7AEB8` dashed** outline, round caps, **4pt dash / 4pt gap**. Prefer the actual app/package icon over a blue title badge.
- **Type B (expressive):** freer, more visual compositions for web and print, still within palette and proportion rules.

---

## 6. Depth & Elevation **[Derived]**

Flat by default — hierarchy comes from surface tone and borders, not shadows.

| Level | Token | Value | Use |
|---|---|---|---|
| 0 | — | none, 1px `#E6E6E6` border | Cards, panels at rest |
| 1 | `--shadow-1` | `0 1px 2px rgba(0,0,0,.06), 0 1px 3px rgba(0,0,0,.08)` | Hovered card, sticky header |
| 2 | `--shadow-2` | `0 4px 12px rgba(0,0,0,.10)` | Dropdown, popover, tooltip |
| 3 | `--shadow-3` | `0 12px 32px rgba(0,0,0,.16)` | Modal, drawer |

Surface stack (light): `#FFFFFF` page → `#F5F5F5` band → `#F0F2F5` panel. Dark: `#1C1C1C` → `#303030` → `#2B2D33`; in dark mode prefer lighter surfaces over shadows. Overlay scrim: `rgba(0,0,0,.48)`.

---

## 7. Do's and Don'ts

### Do
- Keep neutrals dominant; let blue mean "you can act here" or "this matters". **[Source]**
- Use step-6 of a family first; use other steps only to support it. **[Source]**
- Use Inter for Latin/Vietnamese and the matching Noto Sans / Kanit for CJK and Thai. **[Source]**
- Keep body line-height 1.5–1.6×, measure 40–70 characters, flush-left. **[Source]**
- Meet 4.5:1 text contrast; use the darker steps (Red-7, Orange-8, Yellow-9, Green-8) for status text. **[Source + Computed]**
- Draw icons on the 20/32/64px grids, 2px stroke, square terminals, 2px corners. **[Source]**

### Don't
- Don't use non-neutral colors for running text. **[Source]**
- Don't overuse blue or use it "just because". **[Source]**
- Don't put many secondary/tertiary colors in one composition; tertiary ≤ 5%. **[Source]**
- Don't use gradients on text or icons; no more than 2 colors per icon. **[Source]**
- Don't center long text; don't let line spacing exceed paragraph spacing. **[Source]**
- Don't use Green-6, Red-6, Orange-6, Yellow-6 or Gray-5 as small text on white (fail AA). **[Computed]**
- Don't use rounded stroke caps or rounded arrowheads/check marks in icons. **[Source]**
- Don't add heavy shadows, glows or glassmorphism. **[Derived]**

---

## 8. Responsive Behavior **[Derived]**

| Breakpoint | Width | Columns | Gutter | Side margin |
|---|---|---|---|---|
| `xs` | < 576px | 4 | 16px | 16px |
| `sm` | 576–767px | 8 | 16px | 24px |
| `md` | 768–1023px | 8 | 24px | 32px |
| `lg` | 1024–1279px | 12 | 24px | 40px |
| `xl` | ≥ 1280px | 12 | 24px | auto (max 1200px content) |

- Type scale steps down on `xs`: Display 40px, H1 32px, H2 26px, H3 22px; body stays 16px.
- Touch targets ≥ 44×44px; compact 32px buttons are desktop-only.
- Top nav collapses to a hamburger + full-height drawer below `md`; admin sidebar collapses to a 64px icon rail at `md`, then to a drawer at `xs`.
- Data tables: horizontal scroll inside the container (never page-level scroll) or switch to stacked cards below `sm`.
- Spot-32 + paragraph rows keep icon-left layout at all sizes; spot-64 feature grids go 3 → 2 → 1 columns.
- Network diagrams: render at 900px intrinsic width, scale down proportionally; provide a pinch/zoom or "open full size" option on mobile.

---

## 9. Agent Prompt Guide

### Quick reference

```
Canvas        #FFFFFF  | dark #1C1C1C
Text          #000000  | secondary #666666 | disabled #8F8F8F
Border        #E6E6E6  | strong #CFCFCF
Panel         #F5F5F5 / #F0F2F5
Interactive   #0067E6  → hover #0050BF → active #003B99 | focus ring #5CB0FF
Accent        #26D4AC  (fills only; text uses #0D826F)
Warning/Error #FCBF1D / #F57000 / #F53C3C (fills) — text: #754A00 / #A84100 / #CF272D
Font          Inter; body 16px/1.6; headings 1.15–1.25
Radius        2 / 4 / 8 / 12 px
Spacing       4-pt scale: 4 8 12 16 24 32 48 64 96
Icons         outline, 2px stroke, square caps, 2px corners, 20/32/64 grid
```

### Ready-to-use prompts

1. **Landing page:** "Build a landing page following DESIGN.md: white canvas, black Inter headlines (H1 40px/700/1.2), gray-6 body copy 16px/1.6 at max 65ch, flush-left. One primary blue (#0067E6) CTA in the hero; a 3-column feature grid with 64px outline spot icons above each headline; alternate sections with #F5F5F5 bands; no gradients, no heavy shadows."
2. **Admin dashboard:** "Create an infrastructure admin console per DESIGN.md: 240px cold-gray-1 sidebar with 20px system icons, 64px top bar, data table with 48px rows and #F5F5F5 header, status chips using the tinted alert palette. Blue only for links, selected state and the single primary action."
3. **Settings form:** "Design a settings form per DESIGN.md: 40px inputs with 1px #CFCFCF border, 4px radius, labels above at 14px/600, blue focus ring #5CB0FF, error text #CF272D, one primary and one secondary button right-aligned."
4. **Architecture diagram:** "Draw a Type A network diagram per DESIGN.md: 900px canvas, core components as blue shapes, external devices as #DFE1E6 shapes, 15pt labels, 1pt strokes, solid black arrows with 1:2 arrowheads and a gap before targets, groups outlined with #A7AEB8 dashed 4pt/4pt round-cap strokes."
5. **Dark mode:** "Convert this screen to dark mode per DESIGN.md: page #1C1C1C, surfaces #303030 / #2B2D33, text #FFFFFF / #CFCFCF, links #5CB0FF, borders #404040; prefer lighter surfaces over shadows."
