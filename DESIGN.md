# Design System Document: The Kinetic Gallery

## 1. Overview & Creative North Star
**Creative North Star: "Cinematic Velocity"**

This design system is engineered to feel like a high-end digital film reel. It rejects the static, "boxed-in" nature of traditional web templates in favor of motion, depth, and editorial tension. The goal is to showcase graphic design and video editing work through a lens of premium innovation. 

We move beyond the grid by utilizing **intentional asymmetry**. Headlines should feel "anchored" to the edges of the screen, while media content floats with organic layering. By combining massive, technical typography with glassmorphic depth, we create an environment that feels both professional and high-energy—mimicking the interface of a high-end editing suite.

---

## 2. Colors
The palette is built on a foundation of deep midnight (`surface`) to allow vibrant neon accents to "pop" with maximum luminance.

*   **Primary (`#cc97ff`) & Secondary (`#00e3fd`):** These are our "Active Energy" colors. Use them for focus states, call-to-actions, and interactive highlights.
*   **Tertiary (`#f3ffca`):** Use this "Acid" accent sparingly for high-impact labels or critical "Stop/Go" indicators to create visual friction and interest.
*   **The "No-Line" Rule:** Explicitly prohibit the use of 1px solid borders for sectioning or containment. Boundaries must be defined solely through background color shifts. For example, a `surface_container_low` section sitting on a `surface` background provides all the separation the eye needs without the "cheapness" of a stroke.
*   **Surface Hierarchy & Nesting:** Treat the UI as a series of physical layers. Use the `surface_container` tiers to create depth:
    *   **Level 0:** `surface` (The base canvas).
    *   **Level 1:** `surface_container_low` (Secondary content zones).
    *   **Level 2:** `surface_container_high` (Interactive cards or floating panels).
*   **The "Glass & Gradient" Rule:** To achieve a premium look, use Glassmorphism for floating elements. Combine `surface_variant` at 60% opacity with a `backdrop-blur` of 20px. For CTAs, utilize a linear gradient from `primary` to `primary_dim` at a 135-degree angle to add "soul" and dimension.

---

## 3. Typography
Our typography is a study in contrast: the technical precision of **Space Grotesk** for headers against the clean readability of **Manrope** for data and body copy.

*   **Display & Headline (Space Grotesk):** Use `display-lg` and `headline-lg` for project titles. These should be set with tight letter-spacing (-0.02em) to create a bold, "locked-in" editorial feel. Don't be afraid of overlapping a headline with a piece of media to create depth.
*   **Body & Label (Manrope):** All functional text and descriptions use the Manrope scale. `body-lg` is your workhorse for descriptions. 
*   **The Hierarchy Strategy:** Use `label-md` in all caps with increased letter-spacing (0.1em) for category tags or metadata. This creates a "technical" aesthetic that balances the organic nature of the bold headlines.

---

## 4. Elevation & Depth
In this design system, elevation is conveyed through **Tonal Layering** and light, not shadows.

*   **The Layering Principle:** Avoid shadows on standard cards. Instead, place a `surface_container_highest` element onto a `surface_container_low` background. This creates a sophisticated "lift" that feels integrated into the dark theme.
*   **Ambient Shadows:** When a "floating" effect is required (e.g., a video playback modal), use an extra-diffused shadow.
    *   *Specs:* Blur: 40px, Spread: -10px, Color: `on_surface` at 6% opacity. This mimics ambient light rather than a harsh drop shadow.
*   **The "Ghost Border" Fallback:** If accessibility requires a container edge, use a "Ghost Border." Apply `outline_variant` at 15% opacity. Never use 100% opaque borders.
*   **Glassmorphism & Depth:** Floating navigation bars and playback controls must use `surface_bright` with a 70% alpha and a high blur. This allows the vibrant neon content to bleed through the UI, making the experience feel immersive.

---

## 5. Components

### Buttons
*   **Primary:** Solid `primary` background with `on_primary_fixed` text. Use `rounded-full` for a modern, sleek feel. On hover, apply a glow effect using a `primary` shadow at 30% opacity.
*   **Secondary (Glass):** `surface_variant` at 40% opacity with a `backdrop-blur`. Text color is `primary`.
*   **Tertiary:** No background. Text in `secondary` with a bottom-aligned 2px underline that expands from the center on hover.

### Cards & Project Tiles
*   **Structure:** No dividers or borders. Use `surface_container_low` as the base. 
*   **Interaction:** On hover, the card should transition to `surface_container_high` and scale slightly (1.02x). Media within the card should have a subtle zoom-in animation.
*   **Spacing:** Use the `xl` (1.5rem) roundedness scale for project thumbnails to soften the "High-Energy" typography.

### Input Fields
*   **Default:** `surface_container_lowest` background with an `outline_variant` ghost border (10% opacity).
*   **Focus State:** The border transitions to 100% `primary` opacity with a subtle `primary` outer glow. Label text (`label-md`) should shift to `primary`.

### Chips (Category Filters)
*   **Unselected:** `surface_container_high` with `on_surface_variant` text.
*   **Selected:** `secondary_container` background with `on_secondary_container` text. Use `rounded-md` (0.75rem) to differentiate from the "pill" style buttons.

### Video Playback Controls (Custom)
*   **Scrubber Bar:** `surface_variant` background (track) with a `secondary` (Electric Blue) fill for progress. The scrubber "knob" should only appear on hover to keep the UI clean and cinematic.

---

## 6. Do's and Don'ts

### Do:
*   **Use Whitespace as a Tool:** Give large typography room to breathe. High energy does not mean "crowded."
*   **Animate Transitions:** Use "Power4.out" easing for all element entries. Objects should feel like they have weight and momentum.
*   **Layer Media:** Allow video thumbnails to slightly overlap background text to create a 3D parallax effect.

### Don't:
*   **Don't Use Pure Black:** Always use `surface` (#060e20) as your darkest point. Pure #000000 kills the depth of the neon accents.
*   **Don't Use Dividers:** Never use a horizontal rule `<hr>` to separate content. Use a 120px vertical spacer or a surface color shift.
*   **Don't Over-Glow:** Neon accents should feel like "light sources." If everything glows, nothing is important. Reserve glows for active states and primary CTAs.