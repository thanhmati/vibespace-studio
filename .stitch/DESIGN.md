# Design System: VibeSpace Studio
**Project ID:** 7794977049673136809

## 1. Visual Theme & Atmosphere
VibeSpace Studio is designed around a premium **Cyber-Zen Glassmorphism** aesthetic. The visual theme balances the quiet focus of a Zen temple with the futuristic energy of a cosmic cyber station. 
*   **Density:** Balanced Focus (5/10) — Interfaces are airy with generous padding to prevent cognitive overload.
*   **Variance:** Confident Asymmetric (7/10) — Avoids boring rigid symmetries in favor of offset content columns and dynamic widget placement.
*   **Motion:** Fluid Cinematic (6/10) — UI elements feel weightless, utilizing smooth backdrop-filter transitions and spring-based response curves.
*   **Atmosphere:** A quiet, dark sanctuary suspended in deep space. Content containers appear as floating glass panels, integrating seamlessly with ambient backgrounds.

## 2. Color Palette & Roles
The color palette is calibrated for dark environments (Dark Mode Only) to reduce eye strain during long focus sessions:
*   **Dark Space** (`#0B0F19`) — Primary canvas background. A deep cosmic blue-black that replaces harsh pure black.
*   **Glass Base** (`rgba(21, 29, 48, 0.7)` / `#151D30` at 70% opacity) — Surface fill for cards, widget containers, and interactive popups.
*   **Neon Indigo** (`#6366F1`) — Primary brand color. Used for active states, primary buttons, highlighted text, and main interactive anchors.
*   **Cyber Emerald** (`#10B981`) — Secondary color. Used for success states, active timer indicators, and secondary visual metrics.
*   **Hot Pink** (`#EC4899`) — Accent color. Reserved for notifications, attention-grabbing interactive elements, and hover highlights.
*   **Slate-50** (`#F8FAFC`) — Primary text. A crisp off-white ensuring maximum contrast against the dark space background.
*   **Slate-400** (`#94A3B8`) — Sub-text and icons. A muted slate-gray used for secondary descriptions, placeholders, and deactivated states.
*   **Glass Border** (`rgba(255, 255, 255, 0.1)` / `#FFFFFF1A`) — Outer stroke of glass panels, creating structural separation.

## 3. Typography Rules
Kiểu chữ được thiết kế tối giản, hiện đại để duy trì sự thanh thoát:
*   **Display & Headlines:** **Outfit** (Google Fonts) — Track-tight, controlled scaling. Visual hierarchy is achieved through weights (600, 700) rather than overwhelming size.
*   **Body Text:** **Outfit** — Light geometric sans-serif. Leading is relaxed (1.5–1.6), with a maximum line length of 65 characters (`65ch`) to enhance readability.
*   **Monospace / Numbers:** **Space Grotesk** or system monospace (e.g. `JetBrains Mono`) — Used exclusively for the Pomodoro timer numbers, clocks, and high-density productivity metrics.
*   **Typography Fallbacks:** `Inter`, `sans-serif`.
*   **Banned Typography:** Generic serif fonts (Times New Roman, Georgia) are strictly banned. `Inter` is banned from being the primary headline/display font.

## 4. Component Stylings
*   **Glass Cards (Thẻ Kính Mờ):**
    *   Background: `rgba(21, 29, 48, 0.7)` with `backdrop-filter: blur(16px)`.
    *   Border: `1px solid rgba(255, 255, 255, 0.1)` (`#FFFFFF1A`).
    *   Border-Radius: Exactly `16px`.
    *   Elevation: No heavy outer glows or high-contrast drop shadows. Use soft, highly diffused dark shadows (`rgba(0, 0, 0, 0.3)`).
*   **Buttons:**
    *   Shape: Rounded corners with a `16px` border-radius.
    *   Primary Button: Background is Neon Indigo (`#6366F1`), text is Slate-50 (`#F8FAFC`). Active state translates -1px vertically for tactile response.
    *   Secondary Button: Ghost outline style with Glass Border (`#FFFFFF1A`) and a subtle hover tint of Neon Indigo or Cyber Emerald.
    *   Accent Button: Hot Pink (`#EC4899`) background for high-priority actions.
*   **Inputs & Forms:**
    *   Label: Positioned cleanly above the input field.
    *   Input Box: Glass base background, 1px Glass Border, and `16px` border-radius.
    *   Focus State: Transition border color to Neon Indigo (`#6366F1`) or Cyber Emerald (`#10B981`) with a subtle 2px soft ring.
*   **Skeletal Loaders:**
    *   Structure: Shimmering placeholders matching the exact dimensions of glass cards. Spinning wheels and circular loaders are banned.

## 5. Layout & Spacing Principles
*   **Grid System:** Responsive CSS Grid layouts. Avoid percentage-based `calc()` calculations.
*   **Max Width:** The workspace container is capped at `1400px` and centered on the screen.
*   **Asymmetry:** The Hero header or primary workspace layout is left-aligned or split-screen to keep the UI visually engaging.
*   **Spacing:** Built on an 8px scale (padding/margins of 8px, 16px, 24px, 32px, 48px). Section gaps scale dynamically using `clamp()`.

## 6. Motion & Animation Philosophy
*   **Spring Physics:** Transitions use weighted spring physics (`stiffness: 100, damping: 20`) for a premium, tactile feel.
*   **Hover states:** Micro-transitions on backdrop filters, scale (1.02x on hover), and opacity.
*   **Performance:** All animations must target hardware-accelerated properties (`transform`, `opacity`, `backdrop-filter`). Avoid animating width, height, top, or left.

## 7. Design Anti-Patterns (Banned)
*   ❌ **No Pure Black** (`#000000`) for surfaces or background canvases.
*   ❌ **No Emojis** in the user interface controls or text headers.
*   ❌ **No Neon/Outer Glows** or saturated drop shadows around elements.
*   ❌ **No Centered Hero Sections** — layouts must remain asymmetric.
*   ❌ **No Fake/Fabricated Metrics** (e.g. "99.9% uptime", "154k users"). If data is missing, use placeholders like `[metric]`.
*   ❌ **No AI Copywriting Clichés** ("Elevate", "Next-Gen", "Seamless", "Unleash").
