---
version: 1.0
name: SusiandtheElephants-design-system
description: >
  An editorial expedition design system built around a warm sand/dust/charcoal
  palette and a serif-meets-geometric type pairing (Cormorant Garamond + Inter Tight).
  The system leans on generous whitespace, reveal-on-scroll choreography, and
  photography-first layouts to evoke a tactile, magazine-quality travel narrative.
  Every surface feels like sun-bleached paper; every accent feels hand-placed.

  This document is the single source of truth for all pages, components, and
  artifacts. Pass it to Claude at the start of any design or build conversation.
---


# SusiandtheElephants — Design System


## 1 · Design Philosophy

The system serves an editorial expedition brand. Three principles govern every decision:

1. **Photography carries hierarchy.** Type stays restrained; images do the heavy lifting. The largest display text is italic serif at 11vw — enormous but quiet because it's light-weight and italic, not bold.
2. **Paper, not screen.** Surfaces read as sun-bleached paper (#f3eee5), ink is warm charcoal (#1f1d1a), borders are faint pencil rules (#c8bda6). No pure white, no pure black, no neon accents.
3. **Slow reveal.** Content enters with 24px upward drift and 1s fade. Nothing pops; everything arrives. Stagger children with incremental `--d` delays.


## 2 · Colors

### 2.1 Core Palette — "Sand" (default)

| Token | Hex | Role |
|---|---|---|
| `--bg` | `#f3eee5` | Page floor — the dominant background on every public page |
| `--bg-soft` | `#ebe4d6` | Subtle section alternation, card hover fills |
| `--bg-deep` | `#e0d6c2` | Image placeholder fills, empty-state backgrounds |
| `--paper` | `#faf6ec` | Elevated card surfaces, modal backgrounds |
| `--ink` | `#1f1d1a` | Primary text — headlines, nav labels, CTA text. Never pure black. |
| `--ink-soft` | `#3a352e` | Body text, paragraphs, secondary descriptions |
| `--muted` | `#6b6450` | Eyebrow labels, captions, meta text, inactive nav |
| `--muted-2` | `#8b8170` | Tertiary text, disabled states, timestamps |
| `--rule` | `#c8bda6` | Hairline dividers, borders, separators |
| `--accent` | `#6b6450` | Default accent (muted olive-brown — intentionally quiet) |

### 2.2 Dark / Night Mode

Used for hero sections, CTA bands, and the footer — not a full dark mode toggle.

| Token | Hex | Role |
|---|---|---|
| `--night` | `#14130f` | Dark section background |
| `--night-2` | `#1f1d18` | Slightly lighter dark surface (cards on dark) |
| `--night-ink` | `#e8dfce` | Primary text on dark backgrounds |
| Night body | `rgba(232, 223, 206, 0.78)` | Body text on dark |
| Night muted | `rgba(232, 223, 206, 0.6)` | Eyebrows, captions on dark |
| Night rule | `rgba(232, 223, 206, 0.12)` | Borders on dark |

### 2.3 Shadows

| Token | Value | Use |
|---|---|---|
| `--shadow` | `0 1px 0 rgba(31, 29, 26, 0.06)` | Subtle lift — cards, nav on scroll |

The system has essentially one shadow tier. Depth comes from photography, background color shifts, and the reveal animation — not from layered box-shadows.

### 2.4 Alternate Palettes (Tweakable)

These are switchable via `data-palette` on `<html>` or a root container:

**Olive:**

| Token | Hex |
|---|---|
| `--bg` | `#ece4d3` |
| `--bg-soft` | `#e0d8c2` |
| `--bg-deep` | `#cfc4a8` |
| `--paper` | `#f5efe0` |
| `--ink` | `#2a2820` |
| `--muted` | `#6e6a55` |
| `--rule` | `#b6ac8e` |
| `--accent` | `#5a5a3e` |

**Dark (full dark surface):**

| Token | Hex |
|---|---|
| `--bg` | `#1f1d1a` |
| `--bg-soft` | `#14130f` |
| `--bg-deep` | `#0e0c0a` |
| `--paper` | `#2a2722` |
| `--ink` | `#e8dfce` |
| `--ink-soft` | `#c9be9f` |
| `--muted` | `#9b8f72` |
| `--rule` | `#3a3530` |
| `--accent` | `#c9b896` |


## 3 · Typography

### 3.1 Font Stacks

| Token | Stack | Role |
|---|---|---|
| `--serif` | `"Cormorant Garamond", "Cormorant", "Times New Roman", serif` | Display, headlines, subheads, lede text |
| `--sans` | `"Inter Tight", "Inter", -apple-system, BlinkMacSystemFont, sans-serif` | Body, UI, nav, captions, buttons |
| `--mono` | `"JetBrains Mono", ui-monospace, "SF Mono", monospace` | Image captions (overlay), code, metadata badges |

### 3.2 Type Scale

| Class | Family | Size | Weight | Line Height | Letter Spacing | Style | Use |
|---|---|---|---|---|---|---|---|
| `.display` | serif | `clamp(48px, 8.5vw, 132px)` | 400 | 0.92 | -0.02em | italic | Hero headlines — the largest text in the system. Use `.roman` span for non-italic words within. |
| `.hero-sub` (expedition) | serif | `clamp(22px, 2.4vw, 32px)` | 400 | 1.12 | -0.01em | normal | Large hero sub-headline on expedition page. max-width 18ch. |
| `.headline` | serif | `clamp(40px, 6.4vw, 96px)` | 400 | 1.02 | -0.015em | normal | Section headlines. Add `.italic` class when needed. |
| `.subhead` | serif | `clamp(28px, 3.6vw, 56px)` | 400 | 1.12 | -0.01em | normal | Sub-section titles, pull quotes |
| `.lede` | serif | `clamp(22px, 2.2vw, 32px)` | 400 | 1.35 | -0.005em | italic | Opening paragraph / deck text. Max-width 30ch. Color: `--ink-soft` |
| `.body-l` | sans | `clamp(17px, 1.3vw, 20px)` | 400 | 1.6 | — | normal | Large body text. Max-width 58ch. Color: `--ink-soft` |
| `.body` | sans | `16px` | 400 | 1.65 | — | normal | Default body. Max-width 60ch. Color: `--ink-soft` |
| `.eyebrow` | sans | `0.72rem` | 500 | 1.4 | `2px` | uppercase | Section labels. Includes a 28px rule `::before` by default (suppress with `.no-rule`). Color: `--muted` |
| `.caption` | sans | `12px` | 500 | 1.4 | 0.1em | uppercase | Image captions, meta labels. Color: `--muted` |
| `.prose-editorial` | serif | `clamp(1.15rem, 0.9rem + 0.8vw, 1.4rem)` | 400 | 1.55 | `0.2px` | normal | Erzählende Fließtexte (Ledes, Wer-wir-sind-Blöcke). Cormorant Regular, Farbe `#1c1c1c`, max-width 38rem. `<em>`/`<i>` rendert als Cormorant Italic. Nicht für Navigation, Buttons, FAQ oder Preiskarten verwenden. |

### 3.3 Type Pairing Presets (Tweakable)

Switchable via `data-type` attribute:

| Preset | `--serif` | `--sans` |
|---|---|---|
| `serif-sans` (default) | Cormorant Garamond | Inter Tight |
| `all-serif` | Cormorant Garamond | Cormorant Garamond |
| `modern` | Fraunces | Inter Tight |

### 3.4 Principles

- Display type is always **italic serif at weight 400** — never bold. Boldness comes from scale, not weight.
- Body type is always **sans at weight 400** — clean, functional, recessive.
- The only "loud" typographic moments are the `.display` class (up to 180px) and the `.eyebrow` uppercase treatment. Everything in between is deliberately quiet.
- Base body `font-size` on `<body>` is `17px` with `line-height: 1.55`.
- `font-feature-settings: "ss01", "kern"` is applied globally.
- `text-wrap: pretty` on `.body-l` for better paragraph rag.


## 4 · Spacing

### 4.1 Scale

| Token | Value | Use |
|---|---|---|
| `--space-xs` | `8px` | Tight gaps — icon-to-label, inline elements |
| `--space-s` | `16px` | Default component internal padding, card gaps |
| `--space-m` | `32px` | Section sub-gaps, between content blocks |
| `--space-l` | `64px` | Major section internal spacing |
| `--space-xl` | `120px` | Large vertical breathing room |
| `--space-2xl` | `200px` | Maximum vertical separation |
| `--section-pad` | `clamp(72px, 11vw, 160px)` | Primary section top/bottom padding |

### 4.2 Density Presets (Tweakable)

| Density | `--section-pad` | `--space-xl` | `--space-2xl` |
|---|---|---|---|
| default | `clamp(72px, 11vw, 160px)` | `120px` | `200px` |
| `spacious` | `clamp(120px, 18vw, 260px)` | `160px` | `240px` |
| `tight` | `clamp(56px, 9vw, 130px)` | `80px` | `130px` |

Set via `data-density` attribute on the root element.

### 4.3 Layout

| Token | Value | Use |
|---|---|---|
| `--max` | `1440px` | Maximum content width |
| `--gutter` | `clamp(24px, 5vw, 80px)` | Page side gutters |

Container classes:
- `.container` — max-width 1440px, centered, with `--gutter` padding
- `.container-wide` — max-width 1640px, centered, with `--gutter` padding


## 5 · Components

### 5.1 Navigation (`nav`)

- **Position:** Fixed, top, full-width, z-index 100
- **Default state:** Transparent background, light text (`#f3eee5`) — designed to overlay a dark hero image
- **Scrolled state (`.scrolled`):** `rgba(243, 238, 229, 0.92)` with `blur(12px)` backdrop-filter, ink text, 1px bottom border at `rgba(31, 29, 26, 0.06)`, padding compresses from 22px to 14px
- **Logo (`.nav-logo`):** Serif italic, 22px. Ampersand styled with `.amp` (normal style, 0.6 opacity)
- **Nav links:** Sans, 13px, uppercase, weight 500, letter-spacing 0.06em, 0.78 opacity → 1.0 on hover. Active state adds 1px underline rule 8px below
- **CTA button:** Solid ink background, bg-colored text, pill-shaped (see Buttons)
- **Mobile (< 900px):** Nav links hide, grid collapses to logo + CTA

#### Nav variants

| Variant | When to use | Initial text color |
|---|---|---|
| (default, no extra class) | Pages with a dark photo hero (Home, Expedition) | `#f3eee5` (light) |
| `.nav--on-light` | Pages where the hero or top section has a light/sand background (Beratung, Reiseführer, Journal) | `--ink` (dark) |

The scrolled state (solid sand background, ink text) is identical for both variants — only the initial transparent state differs. With `.nav--on-light`, the CTA button is a solid dark pill from the start (`--ink` background, `--bg` text); on scroll both variants show the same scrolled button style.

### 5.2 Buttons (`btn`)

| Variant | Background | Text | Border | Radius | Padding | Hover |
|---|---|---|---|---|---|---|
| Default | transparent | inherit | 1px currentColor | `999px` (pill) | `16px 28px` | Ink fill, bg text |
| `.solid` | `--ink` | `--bg` | 1px `--ink` | `999px` | `16px 28px` | Transparent, ink text |
| `.light` | `rgba(243, 238, 229, 0.95)` | `--ink` | transparent | `999px` | `16px 28px` | `--bg` fill |
| `.ghost` | transparent | `#fff` | `rgba(255,255,255,0.4)` | `999px` | `16px 28px` | `rgba(255,255,255,0.12)` fill |

- Typography: Sans, 13px, uppercase, weight 500, letter-spacing 0.08em
- Arrow element (`.arrow`): 14px horizontal line with 7px chevron, translates 4px right on hover
- All buttons are **pill-shaped** — there are no square or rounded-rect buttons in this system

### 5.3 Image Frames (`image-frame`)

- Background: `--bg-deep`
- Overflow: hidden
- Default gradient overlay: `linear-gradient(180deg, transparent 60%, rgba(0,0,0,0.12) 100%)` — suppress with `.no-grad`
- Caption (`.image-caption`): Mono, 11px, uppercase, 0.12em tracking, white at 0.85 opacity, positioned bottom-left with `rgba(0,0,0,0.35)` backdrop + blur(6px)

### 5.4 Image Slots (`<image-slot>`)

Custom element for user-fillable image placeholders. Key attributes:

| Attribute | Values | Default | Purpose |
|---|---|---|---|
| `id` | string | — | **Required** for persistence |
| `shape` | `rect`, `rounded`, `circle`, `pill` | `rounded` | Corner treatment |
| `radius` | number (px) | `12` | Radius for `rounded` shape |
| `mask` | CSS clip-path | — | Overrides `shape` for custom shapes |
| `fit` | `cover`, `contain`, `fill` | `cover` | Object-fit behavior |
| `placeholder` | string | `"Drop an image"` | Empty-state label |
| `src` | URL | — | Fallback/initial image |

- Default size: 240×160px (override with CSS)
- Supports drag-and-drop (PNG, JPEG, WebP, AVIF)
- `fit="cover"` enables double-click reframe mode (pan + corner-drag resize)
- State persists via `.image-slots.state.json` sidecar

### 5.5 Sections

- `.section` — applies `--section-pad` top and bottom
- `.section.dark` — applies `--night` background, `--night-ink` text, and adjusts all child typography classes to dark-mode colors

### 5.6 Reveal Animations

**Single element (`.reveal`):**
- Initial: `opacity: 0; translateY(24px)`
- Triggered (`.in`): `opacity: 1; translateY(0)` over 1s ease / 1.2s cubic-bezier(0.2, 0.6, 0.2, 1)

**Staggered group (`.reveal-stagger`):**
- Container: flex column, 16px gap
- Children: same as `.reveal` but with individual `--d` delay variable
- Triggered (`.in` on container): all children animate in sequence

### 5.7 Footer

- Background: `--night`
- Text: `--night-ink`
- Padding: 100px top, 40px bottom
- Grid: 4 columns (2fr 1fr 1fr 1fr) with 60px gap at desktop, 2 columns at < 800px
- Column heads: Sans, 11px, uppercase, 0.22em tracking, weight 500, 0.5 opacity night-ink
- Links: default night-ink, 0.7 opacity on hover
- Bottom bar: flex between, 12px, 0.5 opacity night-ink
- Footer mark (`.footer-mark`): Serif italic, 32px
- Bottom divider: 1px at `rgba(232, 223, 206, 0.12)`


## 6 · Tweaks Panel

The Tweaks Panel is a floating control surface for live-editing design tokens. It communicates with the host via `postMessage` protocol:

**Inbound messages (from host):**
- `__activate_edit_mode` — opens the panel
- `__deactivate_edit_mode` — closes the panel

**Outbound messages (to host):**
- `__edit_mode_available` — announces the panel exists (sent on mount)
- `__edit_mode_set_keys` — persists changed values `{ edits: { key: value } }`
- `__edit_mode_dismissed` — user closed the panel

**Available control components:**

| Component | Props | Use |
|---|---|---|
| `TweakSlider` | `label, value, min, max, step, unit, onChange` | Numeric ranges (font size, spacing) |
| `TweakToggle` | `label, value, onChange` | Boolean switches (dark mode) |
| `TweakRadio` | `label, value, options, onChange` | Segmented choice (density, type pairing) — auto-falls back to dropdown if labels overflow |
| `TweakSelect` | `label, value, options, onChange` | Dropdown selection |
| `TweakText` | `label, value, placeholder, onChange` | Free text input |
| `TweakNumber` | `label, value, min, max, step, unit, onChange` | Numeric input with drag-to-scrub |
| `TweakColor` | `label, value, options, onChange` | Color/palette picker with swatch chips — supports single hex or array-of-hex palettes |
| `TweakButton` | `label, onClick, secondary` | Action buttons |
| `TweakSection` | `label` | Visual grouping header |

**Usage pattern:**
```jsx
const TWEAK_DEFAULTS = /*EDITMODE-BEGIN*/{ ... }/*EDITMODE-END*/;

function App() {
  const [t, setTweak] = useTweaks(TWEAK_DEFAULTS);
  return (
    <>
      {/* Your UI using t.propertyName */}
      <TweaksPanel>
        <TweakSection label="Section Name" />
        <TweakSlider label="Size" value={t.size} min={10} max={40}
                     onChange={(v) => setTweak('size', v)} />
      </TweaksPanel>
    </>
  );
}
```


## 7 · Responsive Behavior

| Breakpoint | Key Changes |
|---|---|
| < 800px | Footer grid → 2 columns; footer bottom → column layout |
| < 900px | Nav links hide; nav grid simplifies to logo + CTA |
| All sizes | Typography uses `clamp()` throughout — no hard breakpoints for type. Gutters scale via `clamp(24px, 5vw, 80px)`. Section padding scales via `clamp(72px, 11vw, 160px)`. |

### Touch Targets
- Buttons: minimum 48px height (16px vertical padding + 13px text + border)
- Nav links: full text area + padding
- Image slots: full slot area is the drop/click target


## 8 · Do's and Don'ts

### Do
- Use `--ink` for headlines and `--ink-soft` for body — never pure `#000`
- Use `--bg` as page floor — never pure `#fff`
- Keep display text italic serif at weight 400 — scale conveys importance, not boldness
- Use pill-shaped buttons exclusively (radius 999px)
- Apply `.reveal` or `.reveal-stagger` to content entering the viewport
- Use `clamp()` for responsive sizing — avoid hard breakpoint overrides for type
- Prefix section labels with `.eyebrow` (includes the 28px rule)
- Use `.section.dark` for contrast bands — don't invent new dark treatments

### Don't
- Don't use bold serif (> weight 400) for display text
- Don't use hard corners on buttons or interactive elements
- Don't add colored accents beyond the palette — the system is deliberately monochromatic-warm
- Don't stack multiple shadow tiers — one subtle shadow (`--shadow`) or none
- Don't exceed 60ch line width for body text
- Don't use the dark palette tokens outside `.section.dark` or footer contexts
- Don't create new animation timings — use the reveal system (1s ease fade, 1.2s cubic-bezier transform)


## 9 · File Map

| File | Purpose |
|---|---|
| `tweaks-panel.jsx` | Reusable Tweaks shell + form controls. Loads via `<script>` in any HTML page. |
| `styles.css` (main stylesheet) | All tokens, typography classes, layout, nav, buttons, image frames, reveal, footer. |
| `image-slot.js` | `<image-slot>` custom element — user-fillable image placeholders with persistence. |
| `susi-design-system.md` | **This file** — the canonical reference. Pass to Claude for any build work. |


## 10 · Applying This System

When starting a new page or component with Claude, include this file in context and say:

> "Use the SusiandtheElephants design system. Here's the reference: [this file]."

Claude should then:
1. Use only the tokens defined here (CSS custom properties, classes, spacing values)
2. Follow the typography hierarchy (serif display → sans body)
3. Apply pill-shaped buttons, paper-toned surfaces, and the reveal animation system
4. Use `.section.dark` for contrast bands rather than inventing new dark surfaces
5. Reference the Tweaks Panel components for any interactive configuration UI
