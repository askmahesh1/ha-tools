# ha-tools
# 🌙 Bedside Display Dashboard for Home Assistant

A sleek, modern, full-screen digital bedside clock, environmental monitor, and smart bedroom control panel for Home Assistant. Designed specifically for wall-mounted tablets, smart displays, iPad StandBy mode, and desktop views.

---

## ✨ Features

- **Giant StandBy Typography**: Responsive 12-hour clock with glowing AM/PM indicator and date formatting that fills the viewport without scrollbars.
- **Glassmorphic Environment Capsule**: Real-time outdoor weather condition & temperature, indoor bedroom temperature, and humidity pill.
- **Deep OLED Night Mode**: Low-glare crimson red digits on pure `#000000` black for zero light pollution while sleeping.
- **Quick Bedside Controls**: Frosted glass tile cards for quick access to night lamps, ceiling fan speeds, lights, and sleep/nap automations.
- **Full Kiosk Experience**: Automatically hides the Home Assistant header, sidebar, and navigation elements.
- **Safe Fallback Previews**: Built-in fallback demo values ensure the dashboard renders even before you connect your specific sensors.

---

## 📁 Repository Files

| File | Description |
| :--- | :--- |
| [`bedside.prompt.md`](dashboards/bedside.prompt.md) | The universal Master AI Prompt to feed to an LLM / AI coding assistant to generate this dashboard. |
| [`bedside.yaml`](dashboards/bedside.yaml) | The complete, copy-pasteable Lovelace dashboard configuration in Raw YAML format. |

---

## 📦 Required HACS Frontend Cards

Before installing the dashboard, make sure you have installed these three frontend cards via **HACS** (Home Assistant Community Store):

1. **`button-card`** by *RomRider* (`custom:button-card`)
2. **`lovelace-card-mod`** by *thomasloven* (`card-mod`)
3. **`kiosk-mode`** by *NemesisRE* (`kiosk-mode`)

---

## 🚀 Quick Installation Guide

### Method A: Direct Paste (Recommended)

1. In Home Assistant, go to **Settings** → **Dashboards**.
2. Click **Add Dashboard** (Bottom Right):
   - **Title**: `Bedside Display`
   - **Icon**: `mdi:clock-outline`
   - **URL**: `bedside-display`
3. Open the newly created dashboard.
4. Click the **three dots (⋮)** in the top right corner → **Edit Dashboard**.
5. Click the **three dots (⋮)** again → **Raw configuration editor**.
6. Delete any default template text, copy the entire content of [`bedside.yaml`](dashboards/bedside.yaml), paste it into the editor, and click **Save**.

---

### Method B: Using an AI Coding Assistant

Copy the prompt from [`bedside.prompt.md`](dashboards/bedside.prompt.md) and send it to your AI coding assistant (such as Antigravity, Claude, or ChatGPT).

---

## ⚙️ Entity Customization Table

Open [`bedside.yaml`](dashboards/bedside.yaml) and replace the placeholder entity IDs with your own:

### 1. Clock & Environment Pill (`bedside` view)
At the top of the clock template in [`bedside.yaml`](dashboards/bedside.yaml#L95-L105):

```javascript
const ENTITY_WEATHER   = 'weather.your_weather_entity'; // e.g. weather.home
const ENTITY_ROOM_TEMP = 'sensor.bedroom_temperature';  // e.g. sensor.master_bedroom_temperature
const ENTITY_ROOM_HUM  = 'sensor.bedroom_humidity';     // e.g. sensor.master_bedroom_humidity
```

### 2. Controls Grid (`controls` view)
Replace the tile entities in [`bedside.yaml`](dashboards/bedside.yaml#L380-L420):

| Placeholder Entity | Description | Example Real Entity |
| :--- | :--- | :--- |
| `light.bedroom_lamp` | Bedside / Night Lamp | `light.master_bedroom_nightstand` |
| `fan.bedroom_fan` | Ceiling Fan | `fan.bedroom_smart_fan` |
| `light.bedroom_ceiling_light` | Main Room Light | `light.master_bedroom_ceiling` |
| `input_boolean.sleep_mode` | Sleep / Nap Automation Switch | `input_boolean.nap_time` |
| `/home-overview/overview` | Main dashboard navigation URL | `/lovelace/0` or `/home-overview/overview` |

---

## ⌨️ Useful Keyboard Shortcuts (When Kiosk Mode is Active)

Because Kiosk Mode hides the navigation menus:
- **`m`** — Toggle Home Assistant sidebar open/closed.
- **`c`** — Open Command Bar / Quick Search.
- **`e`** — Enter Dashboard Edit Mode.


## Snapshots
### Main View 
<img width="952" height="572" alt="image" src="https://github.com/user-attachments/assets/26888655-b82c-4809-ae92-c8b5f4a9ab9a" />

### Night Mode
<img width="736" height="412" alt="image" src="https://github.com/user-attachments/assets/1e442428-ee48-47e6-8530-5a44226a409c" />

### Controls
<img width="990" height="345" alt="image" src="https://github.com/user-attachments/assets/9a31090a-84d4-474c-9173-8ca798654ad0" />


