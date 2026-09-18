Create a modern, full-screen Bedside Clock & Smart Display dashboard for Home Assistant with URL path `bedside-display` using `type: panel` and 3 views:

1. Prerequisites / HACS Resources:
   - `button-card`
   - `lovelace-card-mod`
   - `kiosk-mode`

2. Global Configuration:
   - Kiosk mode enabled to hide header, sidebar, menu buttons, notifications, and account (`hide_header: true`, `hide_sidebar: true`, `hide_overflow: true`, `hide_account: true`).
   - Remove header offsets with card-mod (`--header-height: 0px !important`).

3. View 1: Main Clock (`path: bedside`)
   - Dark radial gradient background (`#0f172a` to `#030712`).
   - Centered flexbox vertical stack filling `100vh` without scrollbars.
   - Giant glowing clock digits with AM/PM indicator (`sensor.time` update trigger).
   - Date display (`Day of week, Month Day`).
   - Floating glassmorphism environmental capsule pill containing:
     * Outdoor Weather condition & temperature (`weather.home`)
     * Indoor Bedroom temperature (`sensor.apollo_msr_1_391f9c_bme280_temperature` or user sensor)
     * Indoor Bedroom humidity (`sensor.apollo_msr_1_391f9c_bme280_humidity` or user sensor)
   - Bottom row with 3 pill buttons (140px wide, frosted glass blur, icon + label):
     * [Night Mode] -> Navigates to `/bedside-display/night`
     * [Controls] -> Navigates to `/bedside-display/controls`
     * [Overview] -> Navigates to `/home-overview/overview`
   - Disable card tap actions (`tap_action: none`) on the clock to prevent entity history popups.

4. View 2: Deep Night Mode (`path: night`)
   - Pure OLED black background (`#000000`).
   - Low-glare glowing crimson/red giant clock digits and dark red date.
   - Minimal bottom pill button: [Normal Clock] -> Navigates back to `/bedside-display/bedside`.

5. View 3: Bedside Controls (`path: controls`)
   - Centered frosted-glass card grid (max width 600px).
   - Top navigation row: [Back to Clock] and [Overview].
   - 2-column tile grid for bedroom entities: Night Lamp, Ceiling Fan, Ceiling Light, Nap / Sleep Mode.
