---
name: Kindred Motion
colors:
  surface: '#f7f9fe'
  surface-dim: '#d7dadf'
  surface-bright: '#f7f9fe'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f1f4f9'
  surface-container: '#ebeef3'
  surface-container-high: '#e5e8ed'
  surface-container-highest: '#e0e3e7'
  on-surface: '#181c20'
  on-surface-variant: '#55433b'
  inverse-surface: '#2d3135'
  inverse-on-surface: '#eef1f6'
  outline: '#88726a'
  outline-variant: '#dbc1b7'
  surface-tint: '#9a451e'
  primary: '#9a451e'
  on-primary: '#ffffff'
  primary-container: '#ff9466'
  on-primary-container: '#762b04'
  inverse-primary: '#ffb597'
  secondary: '#006a66'
  on-secondary: '#ffffff'
  secondary-container: '#8ef4ee'
  on-secondary-container: '#00716d'
  tertiary: '#615e5b'
  on-tertiary: '#ffffff'
  tertiary-container: '#b4afac'
  on-tertiary-container: '#454240'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#ffdbcd'
  primary-fixed-dim: '#ffb597'
  on-primary-fixed: '#360f00'
  on-primary-fixed-variant: '#7b2f07'
  secondary-fixed: '#8ef4ee'
  secondary-fixed-dim: '#71d7d1'
  on-secondary-fixed: '#00201f'
  on-secondary-fixed-variant: '#00504d'
  tertiary-fixed: '#e7e1de'
  tertiary-fixed-dim: '#cbc5c2'
  on-tertiary-fixed: '#1d1b19'
  on-tertiary-fixed-variant: '#494644'
  background: '#f7f9fe'
  on-background: '#181c20'
  surface-variant: '#e0e3e7'
typography:
  display:
    fontFamily: Quicksand
    fontSize: 48px
    fontWeight: '700'
    lineHeight: 56px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Quicksand
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
  headline-lg-mobile:
    fontFamily: Quicksand
    fontSize: 28px
    fontWeight: '600'
    lineHeight: 36px
  headline-md:
    fontFamily: Quicksand
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  headline-sm:
    fontFamily: Quicksand
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  label-lg:
    fontFamily: Quicksand
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 20px
  label-md:
    fontFamily: Quicksand
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 18px
  label-sm:
    fontFamily: Quicksand
    fontSize: 12px
    fontWeight: '700'
    lineHeight: 16px
rounded:
  sm: 0.5rem
  DEFAULT: 1rem
  md: 1.5rem
  lg: 2rem
  xl: 3rem
  full: 9999px
spacing:
  base: 8px
  xs: 4px
  sm: 12px
  md: 24px
  lg: 48px
  xl: 80px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 64px
---

## Brand & Style

The brand personality is designed to be an "invitation, not a challenge." It moves away from the aggressive, high-performance aesthetics of traditional athletics toward a philosophy of communal wellness and sustainable energy. The visual style centers on **Soft Modernism**, blending high-clarity layouts with organic, rounded forms that feel approachable to all fitness levels.

The target audience is the "everyday neighbor"—individuals looking for health and connection rather than just a leaderboard. The emotional response should be one of optimism and safety. This is achieved through a high-key lighting approach (lots of whitespace), soft tactile elements, and a complete absence of sharp corners or intimidating dark palettes.

## Colors

The palette is anchored by "Energetic Amber" (Primary), a soft, sun-kissed orange that stimulates movement without being jarring. This is balanced by "Harbor Teal" (Secondary), which introduces a sense of calm, recovery, and stability.

- **Primary:** Use for main calls to action, active states, and motivational highlights.
- **Secondary:** Use for secondary actions, information icons, and health/wellness indicators.
- **Surface/Tertiary:** A warm, off-white cream serves as the background to avoid the clinical feel of pure white, making the UI feel "lit from within."
- **Neutral:** A soft charcoal-grey is used for text to ensure high legibility while maintaining a softer contrast than pure black.

## Typography

This design system utilizes **Quicksand** for all display and label roles. Its naturally rounded terminals directly reflect the inclusive nature of the brand. For long-form text and body content, **Plus Jakarta Sans** is used to maintain a modern, clean look that is highly legible but shares the same friendly, geometric DNA as the headline font.

Headlines should be set with generous leading to prevent the text from feeling cramped. For mobile, display sizes are scaled down to ensure they don't overwhelm the smaller screen real estate while maintaining their friendly impact.

## Layout & Spacing

The layout philosophy is built on an **Airy Fluid Grid**. We use a 12-column system for desktop and a 4-column system for mobile. A core principle of this design system is "Wide Breathing Room"—margins and gutters are intentionally larger than standard utility apps to reduce visual noise and lower user stress.

- **Desktop:** 64px outer margins with 24px gutters.
- **Mobile:** 16px outer margins with 16px gutters.
- **Spacing Rhythm:** Use the `lg` (48px) and `xl` (80px) units to separate major content sections (e.g., separating "Class Schedule" from "Trainer Profiles"). Small increments (`base`, `sm`) should be reserved for internal component padding.

## Elevation & Depth

To maintain the welcoming atmosphere, we avoid harsh, black shadows. Instead, we use **Ambient Tinted Shadows**.

Depth is created through:
- **Soft Shadows:** Using the Primary or Neutral color at very low opacity (5-8%) with a large blur radius (20px+) to make cards appear as if they are floating gently above the surface.
- **Tonal Layering:** Using the Tertiary color (Warm Cream) for the background and pure white for foreground cards to create a subtle, "soft-stack" hierarchy.
- **Micro-interactions:** When hovered, elements should lift slightly (increasing shadow spread) rather than changing color dramatically, mimicking a physical, "squishy" response.

## Shapes

The shape language is defined by **Pill-shaped (Level 3)** roundedness. Every interactive element—from buttons to input fields—should utilize high corner radii to eliminate any "sharpness" in the interface.

- **Primary Buttons:** Full pill-shape (radius of 100px or similar).
- **Cards/Containers:** Rounded-xl (3rem/48px) for large containers to give them a soft, bubbly appearance.
- **Images:** Should always feature a minimum of `rounded-lg` (2rem/32px) to ensure photography blends into the soft UI.

## Components

### Buttons
Buttons are the primary drivers of energy. They should be pill-shaped, using a subtle vertical gradient of the Primary color to add a "soft-touch" feel. Text within buttons should use `label-lg`.

### Cards
Cards are the "homes" for content. Use a pure white background on the Tertiary surface. Padding inside cards should be generous (minimum `md` spacing) to ensure content never feels crowded.

### Inputs & Forms
Input fields should use a soft 2px border in a lightened Neutral shade. When focused, the border should transition to the Secondary (Teal) color with a soft outer glow (shadow) to provide a supportive, clear focus state.

### Chips & Tags
Use chips for class categories (e.g., "Yoga," "HIIT"). These should use the Secondary color at 10% opacity for the background and 100% opacity for the text, creating a colorful but accessible label.

### Progress Indicators
Fitness tracking should be visual and encouraging. Use thick, rounded progress bars (minimum 12px height) with rounded caps, utilizing the Primary-to-Secondary gradient to represent "journey and balance."