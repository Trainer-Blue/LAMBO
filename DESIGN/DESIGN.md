---
name: Tactical Field Utility
colors:
  surface: '#111500'
  surface-dim: '#111500'
  surface-bright: '#373c1e'
  surface-container-lowest: '#0c1000'
  surface-container-low: '#191e04'
  surface-container: '#1d2207'
  surface-container-high: '#272c10'
  surface-container-highest: '#32371a'
  on-surface: '#e1e6bc'
  on-surface-variant: '#c6c8b6'
  inverse-surface: '#e1e6bc'
  inverse-on-surface: '#2e3316'
  outline: '#909282'
  outline-variant: '#46483b'
  surface-tint: '#bbcf7c'
  primary: '#bbcf7c'
  on-primary: '#293500'
  primary-container: '#86984c'
  on-primary-container: '#232e00'
  inverse-primary: '#54651e'
  secondary: '#c2caaa'
  on-secondary: '#2c331c'
  secondary-container: '#424a31'
  on-secondary-container: '#b1b999'
  tertiary: '#c5c8bc'
  on-tertiary: '#2e3129'
  tertiary-container: '#8f9287'
  on-tertiary-container: '#282b23'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#d7ec95'
  primary-fixed-dim: '#bbcf7c'
  on-primary-fixed: '#161e00'
  on-primary-fixed-variant: '#3d4c05'
  secondary-fixed: '#dee6c4'
  secondary-fixed-dim: '#c2caaa'
  on-secondary-fixed: '#171e09'
  on-secondary-fixed-variant: '#424a31'
  tertiary-fixed: '#e2e4d8'
  tertiary-fixed-dim: '#c5c8bc'
  on-tertiary-fixed: '#1a1d15'
  on-tertiary-fixed-variant: '#45483f'
  background: '#111500'
  on-background: '#e1e6bc'
  surface-variant: '#32371a'
typography:
  display-lg:
    fontFamily: Chivo
    fontSize: 40px
    fontWeight: '800'
    lineHeight: 48px
    letterSpacing: -0.02em
  display-lg-mobile:
    fontFamily: Chivo
    fontSize: 30px
    fontWeight: '800'
    lineHeight: 36px
    letterSpacing: -0.01em
  headline-lg:
    fontFamily: Chivo
    fontSize: 28px
    fontWeight: '700'
    lineHeight: 34px
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Chivo
    fontSize: 22px
    fontWeight: '600'
    lineHeight: 28px
  headline-sm:
    fontFamily: Chivo
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: Chivo
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Chivo
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Chivo
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-lg:
    fontFamily: JetBrains Mono
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 18px
    letterSpacing: 0.06em
  label-md:
    fontFamily: JetBrains Mono
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0.08em
  label-sm:
    fontFamily: JetBrains Mono
    fontSize: 10px
    fontWeight: '500'
    lineHeight: 14px
    letterSpacing: 0.1em
spacing:
  gutter: 1rem
  gutter-mobile: 0.75rem
  gutter-desktop: 1.5rem
  margin: 1rem
  margin-mobile: 0.75rem
  margin-desktop: 2rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1.25rem
  space-xl: 2rem
---

## Brand & Style
The design system establishes a rugged, mission-critical field aesthetic built specifically for forestry rangers, wildland conservation officers, and wilderness response units. It balances utilitarian field readiness with modern operational clarity. The UI draws direct inspiration from military heads-up instrumentation, tactical topographical equipment, and ruggedized field computers. 

Key attributes:
- **Resolute & Utilitarian:** Stripped of non-essential decorative flourishes. Every border, label, and partition serves data density and operational speed.
- **Field Legibility:** Optimized for harsh outdoor environments, direct sunlight glare, night patrols, and high-stress field conditions.
- **Tactical Precision:** Uses razor-sharp edges, monospaced indexing, technical registration marks, and calibrated borders reminiscent of military hardware and mil-spec instrument consoles.

## Colors
The color hierarchy is engineered around night-vision preservation, sunlight glare reduction, and military foliage tones:

- **Primary Canvas & Ground:** `#1A1D0D` serves as the absolute dark tactical base, overlaid with `#2E3316` (Deep Olive Drab) for primary container surfaces, and `#3B441E` for elevated card backgrounds and interactive field plates.
- **Primary Accent (`#708238` - Foliage Green):** Deployed for active state highlights, confirmed tactical status indicators, and primary action controls.
- **Secondary Accent (`#8F9779` - Weathered Sage):** Used for auxiliary interactive elements, secondary readouts, badges, and peripheral framing.
- **Tertiary Accent (`#E6E8DC` - Weathered Khaki / Tactical Bone):** Reserved for high-priority typography, telemetry data, active coordinates, and critical data values to maximize contrast against drab olive backdrops.
- **Operational Status Tokens:**
  - Critical/Hazard: `#C84630` (Tactical Crimson)
  - Warning/Caution: `#D99B26` (Field Amber)
  - Clear/Secure: `#556B2F` to `#708238` (Muted Camo Olive)
  - Tracking/Grid: `#4B5320` (Army Drab Rule)

## Typography
Typography is split into two distinct operational roles:
1. **Command & Narrative (`Chivo`):** A high-performance, sharp grotesque typeface engineered for immediate readability. It conveys authority and crisp mechanical construction across primary headings and field briefings.
2. **Telemetry & Data (`JetBrains Mono`):** Applied to all labels, GPS coordinates, timestamps, unit identifiers, hardware telemetry, and sensor feeds. Monospacing prevents numeric jitter during dynamic sensor updates and reinforces military-grade precision.

All labels (`label-lg`, `label-md`, `label-sm`) default to uppercase tracking to emulate military stencil and display standards.

## Layout & Spacing
The layout follows a rigid technical grid system engineered for high-density spatial awareness and modular component locking:

- **Grid Discipline:** 12-column responsive fluid grid on desktop/tablets, collapsing to 4 columns on handheld mobile devices.
- **Rhythm:** Driven by a base 4px metric system. Component internals utilize tight, condensed spacing (`space-xs` to `space-md`) to ensure critical telemetry remains visible above the fold without scrolling.
- **Section Margins:** Mobile canvases maintain an edge perimeter of `0.75rem` (`margin-mobile`), ensuring maximal map and spatial viewport coverage. Desktop control consoles expand to `2rem` (`margin-desktop`).
- **Gutter Distribution:** Consistent column separators preserve distinct separation between tactical feeds, map layers, and status panels without relying on heavy ambient margins.

## Elevation & Depth
In alignment with tactical military interfaces, this design system rejects blurry drop shadows and synthetic atmospheric blur. Depth is established strictly through **Tonal Layering** and **Calibrated Technical Borders**:

- **Ground (Level 0):** `#1A1D0D` — Base canvas, full-bleed map displays, camera viewports.
- **Surface Tier 1 (Level 1):** `#2E3316` bounded by 1px solid `#4B5320` — Toolbars, bottom operation bars, pinned status trays.
- **Surface Tier 2 (Level 2):** `#3B441E` bounded by 1px solid `#556B2F` — Overlaid telemetry cards, target inspectors, waypoint manifests.
- **Active / Raised (Level 3):** `#4B5320` bounded by 1px solid `#708238` — Modals, emergency alerts, active targeting overlays.
- **Optical Indexing:** Corner registration marks (L-shaped bracket marks) or 1px hairline inner borders are used to denote active or focused elements rather than shadow elevation.

## Shapes
The shape language is strictly **Sharp (`0`)**. Every element features clean 90-degree squared corners or deliberate 45-degree chamfered notches. 

- Radii are set to `0px` universally across cards, buttons, input fields, badges, and modals.
- Chamfered cutouts (4px or 8px clipped corners via CSS `clip-path`) are utilized on primary action triggers and modal headers to evoke fabricated aluminum field cases and rugged military equipment housings.

## Components

### Buttons & Operational Triggers
- **Primary:** Background in `#708238`, text in `#E6E8DC`, 0px border radius, sharp uppercase mono text (`label-md`). Hover/Active states invert with `#E6E8DC` background and `#1A1D0D` text. Optional 4px diagonal chamfer on top-right corner.
- **Secondary / Utility:** Background in `#2E3316`, border 1px solid `#556B2F`, text in `#8F9779`.
- **Destructive / Hazard:** Background in `#381A16`, border 1px solid `#C84630`, text in `#E6E8DC`.

### Chips & Tactical Badges
- Compact height (24px max), 0px radius, 1px solid border matching the tone of the status indicator.
- Background uses 20% opacity of the border color with high-contrast text in `#E6E8DC`. Monospaced uppercase with prepended classification prefix (e.g., `[SEC-4]`, `[GRID-N]`, `[ALT-1420M]`).

### Data Cards & Inspection Panels
- Background `#2E3316` with a 1px border of `#4B5320`.
- Card headers feature an integrated top accent bar (2px solid `#708238`) and a monospaced section coordinate or reference code in the top right.

### Input Fields & Search Shells
- Background `#1A1D0D` with inset 1px border `#4B5320`. Focus states transition the border to 1px solid `#708238` with an amber cursor. Text rendered in `#E6E8DC`.

### Checkboxes, Switches & Radio Controls
- Rigid geometric boxes (0px border radius). Checkboxes display an inset solid square `#708238` when checked.
- Toggle switches adopt a dual-state mechanical slider: a split rectangular block that slides between discrete labeled compartments (`OFF` / `ENGAGED`).

### Sector Lists & Coordinate Manifests
- Flush edge-to-edge row lists with 1px divider lines in `#3B441E`.
- Hover/active row state sets background to `#3B441E` and prepends an active tactical pip indicator `>` in `#E6E8DC`.

### Additional Specialized Components
- **HUD Reticle Viewport:** Framing brackets on screen viewports and camera overlays rendered in `#708238`.
- **Topographical Metric Bar:** Segmented bar gauges using block indicators rather than continuous smooth progress bars, indicating battery, signal telemetry, and fire hazard levels.