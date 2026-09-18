# Bedside Display Master Prompt

Use the prompt below with any AI coding assistant (such as Antigravity, Claude, ChatGPT, etc.) to automatically generate the full-screen Bedside Clock & Smart Display dashboard in Home Assistant:

```markdown
Create a modern, full-screen Bedside Clock & Smart Display dashboard for Home Assistant at URL path `bedside-display` using `type: panel` with 3 views:

1. Requirements & HACS Dependencies:
   - `button-card` (custom:button-card)
   - `lovelace-card-mod` (card-mod)
   - `kiosk-mode` (kiosk-mode)

2. Kiosk Mode & Full-Screen Layout:
   - Hide header, sidebar, menu buttons, notifications, and account (`hide_header: true`, `hide_sidebar: true`, `hide_overflow: true`, `hide_account: true`).
   - Remove header offsets with card-mod (`--header-height: 0px !important`).

3. View 1: Main StandBy Clock (`path: bedside`)
   - Dark radial gradient background (`#0f172a` to `#030712`).
   - Centered flexbox stack filling `100vh` without scrollbars.
   - Giant glowing 12-hour digits with AM/PM indicator and date (triggered by `sensor.time`).
   - Floating glassmorphic environmental capsule pill with easy top-level configuration variables:
     * Outdoor Weather condition & temperature (`weather.your_weather_entity`)
     * Indoor Bedroom temperature (`sensor.bedroom_temperature`)
     * Indoor Bedroom humidity (`sensor.bedroom_humidity`)
     * Built-in fallback demo values if entities are not yet configured.
   - Bottom row with 3 pill buttons (140px width, frosted glass blur, icon + label):
     * [Night Mode] -> Navigates to `/bedside-display/night`
     * [Controls] -> Navigates to `/bedside-display/controls`
     * [Overview] -> Navigates to `/home-overview/overview` (or `/lovelace`)
   - Disable card tap actions (`tap_action: none`) on the clock to prevent entity history popups.

4. View 2: Deep Night Mode (`path: night`)
   - Pure OLED black background (`#000000`).
   - Low-glare glowing crimson/red digits and dark red date.
   - Minimal bottom pill button: [Normal Clock] -> Navigates back to `/bedside-display/bedside`.

5. View 3: Bedside Controls (`path: controls`)
   - Centered frosted-glass card grid (max width 600px).
   - Top navigation row: [Back to Clock] and [Overview].
   - 2-column tile grid with placeholder bedroom entities:
     * `light.bedroom_lamp` (Bedside Lamp)
     * `fan.bedroom_fan` (Ceiling Fan)
     * `light.bedroom_ceiling_light` (Ceiling Light)
     * `input_boolean.sleep_mode` (Sleep Mode)
```
