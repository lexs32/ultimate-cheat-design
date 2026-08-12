# 🌌 MASTER DESIGN SYSTEM & ARCHITECTURE SPECIFICATION (DESIGN.md)

> **PROJECT MANDATE**: This document defines the design directions, design system tokens, motion physics, and craft engineering rules for the storefront.
> 
> 🛑 **MANDATORY GATEWAY**: Follow the 2-phase protocol below. **DO NOT write code until Phase 1 (Design Selection) and the Logo Color Extraction step are explicitly completed.**

---

## 🚦 PHASE 1: 3 BESPOKE DESIGN ARCHETYPES (AWAITING USER SELECTION)

Select **ONE** of the three custom, non-cliché design directions below. Each offers a unique visual rhythm, layout architecture, and personality tailored for digital gaming software & utility suites.

```
┌───────────────────────────────────────────────────────────────────────────────────┐
│                                                                                   │
│  [ OPTION 1: KINETIC TACTICAL BENTO ]   ──   Modular, High-Density, Glass HUD    │
│  [ OPTION 2: CYBER-MINIMALIST MONO  ]   ──   Ultra-Clean, Telemetry Terminal     │
│  [ OPTION 3: HOLOGRAPHIC SHOWCASE   ]   ──   3D Spatial Depth & Cinematic Motion │
│                                                                                   │
└───────────────────────────────────────────────────────────────────────────────────┘
```

---

### 🔲 Option 1: "Kinetic Tactical Bento" (Modular Glass HUD)
* **Visual Identity**: High-precision asymmetric Bento-grid architecture. Every section feels like an advanced cockpit telemetry panel.
* **Hero Experience**: Left-aligned bold typography with live interactive simulation HUD (interactive FOV circle, mannequin bone targeting, real-time telemetry badge).
* **Card Rhythms**: Bento cards with variable spans (`col-span-2`, `col-span-1`), subtle gradient perimeter borders, and internal feature chips.
* **Best For**: High feature-count software where demonstrating aimbot tuning, ESP visuals, and system compatibility in one interactive viewport drives maximum conversion.

---

### 🔲 Option 2: "Cyber-Minimalist Mono" (Precision Telemetry Terminal)
* **Visual Identity**: Monochromatic titanium base with razor-sharp micro-borders, dense data typography, and extreme minimalism. Zero decorative fluff.
* **Hero Experience**: Clean product stream with instant interactive duration chips (1 Day / 1 Week / 1 Month) right on the hero banner with real-time stock counters.
* **Card Rhythms**: Clean horizontal row drawers that expand smoothly upon click using custom spring curves, revealing feature matrices and instant checkout triggers.
* **Best For**: Tech-savvy buyers who prioritize speed, transparent specs, and frictionless 2-click checkouts.

---

### 🔲 Option 3: "Holographic Showcase" (3D Spatial Depth & Cinematic Motion)
* **Visual Identity**: Deep spatial layering with 3D perspective tilts, floating holographic product boxes, dynamic light reflection sheens, and ambient depth blur blobs.
* **Hero Experience**: Central 3D Perspective Card Carousel that responds to mouse-wheel scrolling and horizontal drag gestures with realistic spring physics.
* **Card Rhythms**: 3D tilted game box art cards with dynamic specular hover highlights and animated status rings.
* **Best For**: Creating maximum visual "WOW" factor, brand authority, and premium luxury feel.

---

> ✋ **USER CONFIRMATION REQUIRED BEFORE PROCEEDING**
> 
> 1. Which design archetype do you want to build? (**Option 1, Option 2, or Option 3**)
> 2. Please provide the **Logo image / file** so the color palette tokens below can be extracted dynamically from your exact branding.

---

## 🎨 2. Dynamic Brand Color Extraction Architecture

> ⚠️ **COLOR LOCK RULE**: Exact color values are intentionally not hardcoded. The token slots below will be dynamically mapped once the user provides their logo:

```css
:root {
  /* ── Deep Obsidian Void (Universal Base) ── */
  --bg-void: #030712;
  --bg-surface-subtle: #070a14;
  --bg-surface-card: #0c0f1d;
  --bg-surface-elevated: #131728;
  --bg-glass-backdrop: rgba(12, 16, 28, 0.78);

  /* ── DYNAMIC BRAND SLOTS (Extracted directly from user's Logo) ── */
  --brand-primary: [EXTRACT_DOMINANT_FROM_LOGO];       /* e.g., Electric Blue / Crimson / Neon Cyan */
  --brand-secondary: [EXTRACT_SECONDARY_FROM_LOGO];   /* Secondary logo tint */
  --brand-accent-glow: [EXTRACT_ACCENT_GLOW];         /* High-luminescence specular glow */
  --brand-gradient: linear-gradient(135deg, var(--brand-primary), var(--brand-secondary));

  /* ── Universal Tactical Status Tokens ── */
  --status-undetected-bg: #031d16;
  --status-undetected-border: rgba(16, 185, 129, 0.45);
  --status-undetected-text: #6ee7b7;
  --status-undetected-glow: rgba(16, 185, 129, 0.35);

  --status-updating-bg: #261604;
  --status-updating-border: rgba(245, 158, 11, 0.45);
  --status-updating-text: #fcd34d;

  --status-out-of-stock-bg: #22080a;
  --status-out-of-stock-border: rgba(239, 68, 68, 0.4);
  --status-out-of-stock-text: #fca5a5;

  /* ── Surface Borders ── */
  --border-subtle: rgba(255, 255, 255, 0.08);
  --border-medium: rgba(255, 255, 255, 0.16);
  --border-highlight: rgba(255, 255, 255, 0.28);
}
```

---

## ⚡ 3. Emil Kowalski Craft & Interaction Standards

### 1. The 4 Non-Negotiable Craft Principles
1. **Taste is Trained**: Good taste is precision. Study top interfaces, reverse engineer motion physics, and eliminate friction.
2. **Unseen Details Compound**: High-frequency elements (buttons, inputs) must feel completely natural.
3. **No Sluggish Transitions**: Never use `transition: all 300ms`. Target explicit GPU properties (`transform`, `opacity`) with durations under `200ms`.
4. **Tactile Feedback**: Every pressable element MUST scale down on click:
   ```css
   .tactile-button {
     transition: transform 160ms cubic-bezier(0.23, 1, 0.32, 1), background-color 150ms ease, border-color 150ms ease;
   }
   .tactile-button:active {
     transform: scale(0.97);
   }
   ```

### 2. Craft Review Rules (Before vs. After)

| Before (AI Slop / Cliché) | After (Elite Craft) | Rationale |
| :--- | :--- | :--- |
| `transition: all 300ms` | `transition: transform 180ms ease-out, opacity 180ms ease-out` | Avoid layout thrashing and sluggish repaints. |
| `transform: scale(0)` | `transform: scale(0.95); opacity: 0` | Natural objects never enter from literal zero geometry. |
| Generic `ease-in` curves | `cubic-bezier(0.16, 1, 0.3, 1)` | `ease-in` feels delayed; custom `ease-out` feels instant. |
| Static button without press state | `:active { transform: scale(0.97); }` | Provides immediate physical confirmation of click. |
| Washed-out status badges | Translucent pill with glowing pulsing dot (`● UNDETECTED`) | High contrast against any game box art or thumbnail background. |
| Centered popover zoom | `transform-origin: top right` (trigger origin) | Popovers must scale from the button that spawned them. |

---

## 🍏 4. Apple WWDC Fluid Interface & Motion Physics

### Fluid Pillars
1. **Kill Latency**: Provide immediate feedback on `pointerdown`, not after release.
2. **Interruptibility**: Animations must never lock input. Gestures can grab and redirect objects mid-flight.
3. **Spring Physics**:
   * **Default UI Settle**: `damping: 1.0`, `response: 0.32s` (Zero overshoot, instant settle).
   * **Tactile Card Snap / Momentum**: `damping: 0.82`, `stiffness: 220` (Natural physical settle).

---

## 🎬 5. Anime.js & Kokonut UI Component Standards

### Bento Grid Cards (Kokonut UI Aesthetic)
* Translucent dark panels (`bg-[#0c0f1d]/80`, `backdrop-blur-xl`, `border border-white/10`).
* Internal gradient sheen overlays that catch mouse coordinates.
* High-contrast typography hierarchy (Display headings in `Orbitron` / `Inter`, body in `Plus Jakarta Sans`, technical specs in `JetBrains Mono`).

### Anime.js Motion Timelines
* **Staggered Catalog Reveal**: Stagger card entrances by `50ms` using `cubic-bezier(0.16, 1, 0.3, 1)` with `translateY: [35, 0]` and `scale: [0.96, 1]`.
* **Telemetry HUD Pulse**: Continuous smooth pulse rings on radar scans and aimbot reticles.

---

## 🛡️ 6. Universal Anti-Cliché & Anti-AI-Slop Code

* ❌ **NO generic purple gradients** plastered randomly over cards.
* ❌ **NO fake generic stock reviews** with broken avatars.
* ❌ **NO sluggish 500ms fade-ins** that delay customer navigation.
* ❌ **NO non-functional placeholder buttons**. Every button triggers checkout, guides, or modal drawers.
* ✅ **ONLY custom layouts, crisp high-contrast status pills, tactile press feedback, and real-time store sync.**
