# ZooCard AR Design Direction

## Product & Audience
- **Product:** ZooCard AR, an offline Android mobile AR educational app that brings 5 wildlife cards to life in 3D with audio narration, facts, interactive actions, and quizzes.
- **Audience:** Indonesian children and students (ages 6 to 14), parents, and teachers in classrooms or outdoors.
- **Core Job:** Point the phone at a physical card (or try the starter specimen), observe and interact with the 3D animal without HUD clutter, hear/read short facts, test knowledge, and track collection progress.

## Design Read & Liveliness
- **Visual Language:** Illustrated Wildlife Field Journal (Buku Lapangan Konservasi). Warm paper surfaces, deep rainforest ink, tactile specimen stamps, and calm camera framing.
- **Dial:** `ENERGY 2 / RHYTHM 2 / MOTION 2`
- **Focal Point per Screen:**
  - Scanner screen: The calm viewfinder frame over the live camera.
  - AR stage screen: The 3D animal in the unobstructed center of the viewport.
  - Sheet screens (Info & Kuis, Paspor Penjelajah, Preview Foto): The primary interactive card or learning action inside the sheet.
- **Identity Motif:** Wildlife Specimen Stamp (`ZC-01` to `ZC-05`) paired with custom geometric animal emblems and 3-stamp explorer tracking (`Scan`, `Fakta`, `Kuis`).

## Color Palette (WCAG AA Verified via contrast-check.py)
Three core colors plus one deliberate accent, with functional IUCN conservation tags:

| Role | Token | Hex | Verified Pairing & Ratio |
| :--- | :--- | :--- | :--- |
| Core Paper Surface | `--paper` | `#fffdf7` | Base for cards and sheets |
| Core Field Parchment | `--parchment` | `#f3efe6` | Secondary flat containers (`#16261e` ink: 13.76:1) |
| Core Rainforest Ink | `--ink` | `#16261e` | Primary text on `--paper` (15.52:1) |
| Core Muted Ink | `--ink-muted` | `#42594d` | Secondary text on `--paper` (7.46:1) and `--parchment` (6.61:1) |
| Core Conservation Green | `--forest` | `#0b6b4b` | Primary action fill (`#ffffff` text: 6.52:1) |
| Core Forest Soft | `--forest-soft` | `#e3f3ec` | Unlocked surface (`#085239` text: 8.04:1) |
| Deliberate Accent (Savanna Ochre) | `--ochre` | `#fbbf24` | Unlock celebration & active highlights (`#16261e` ink: 9.46:1) |
| Accent Soft & Ink | `--ochre-soft` / `--ochre-text` | `#fef3c7` / `#92400e` | Quiz and feeding accents (6.37:1) |
| IUCN Critical/Endangered | `--cr-bg` / `--cr-ink` | `#ffe4e6` / `#9f1239` | Functional status badge (6.68:1) |
| IUCN Near Threatened | `--nt-bg` / `--nt-ink` | `#e0f2fe` / `#075985` | Functional status badge (6.59:1) |
| Camera HUD Dark Scrim | `--hud-dark` | `rgba(20, 34, 27, 0.88)` | Floating controls over live video (`#fffdf7` text: 16.20:1) |
| Focus Indicator | `--focus` | `#b45309` | Visible `:focus-visible` ring on light surfaces (4.94:1) |

## Typography & Iconography
- **Typeface:** Clean system sans-serif stack (`'Plus Jakarta Sans', 'Segoe UI', Roboto, system-ui, sans-serif`) for instant zero-network legibility on Android WebView, using fluid sizing (`clamp()`) for key headings and generous `1.45` to `1.5` line height for young readers.
- **Iconography:** Custom inline SVG line icons (`20px`, `stroke-width="2"`) for all controls, plus 5 custom geometric SVG wildlife stamps for the 5 animals. No scattered decorative emojis on UI controls.

## Elevation, Radius & Motion Discipline
- **Radius hierarchy:** `24px` top-only on mobile bottom sheets, `18px` on main fact/passport cards, `14px` on dock buttons and quiz choices, `10px` on status tags and mini stamps, `999px` only for floating live-camera status pills.
- **Shadows:** Reserved strictly for HUD controls floating directly over live camera video. Surfaces inside sheets sit flat with warm hairline borders (`#d6cfc0`).
- **Glassmorphism:** Used only on floating live-camera tool pills and modal backdrops, never on solid paper surfaces.
- **Motion:** Functional transitions (180ms to 240ms ease-out) for sheet entry, toast notifications, and 3D tap/feed feedback. Zero decorative glow or endless pulsing dots. All non-essential motion pauses under `prefers-reduced-motion: reduce`, and 3D turntable rotation provides an explicit Pause/Play toggle.

## Identity & Logo
- **Logo Mark (Approved):** Layered two-card emblem (`#fbbf24` ochre back card + `#fffdf7` paper front card) on deep conservation green (`#0b6b4b`), featuring a bold geometric **Z** monogram, minimalist wildlife head silhouette on the ochre corner, and AR frame corner ticks.
- **Splash & First-Run Flow:** Fast native-to-WebView splash screen (~1 second, respects `prefers-reduced-motion`) showing the Z-Card logo while camera and 3D assets prepare, followed on first launch by an optional, skippable local **Nama Penjelajah** prompt (100% offline, zero Gmail/cloud login). The chosen name personalizes the Explorer Passport and saved AR Expedition Photo cards.

## Responsive & Touch Standards
- Minimum interactive target size: `44px x 44px` (`48px` on primary bottom dock actions) with at least `8px` spacing.
- Three responsive layout bands: narrow phones (`< 360px`), standard phones (`360px to 679px`), and tablets/landscape (`>= 680px`, centered HUD and multi-column passport grid).
- Respects safe-area insets and Android system Back navigation.
