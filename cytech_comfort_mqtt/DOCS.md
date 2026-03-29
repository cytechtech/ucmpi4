# Home Assistant Add-on: Cytech Comfort → MQTT Bridge

---

## Overview

This add-on connects a Cytech Comfort II / Comfort II ULTRA alarm system to Home Assistant using MQTT.

It provides:

- Real-time monitoring of alarm states and devices
- Full integration with Home Assistant via MQTT Discovery
- Automatic creation of entities (no YAML configuration required)

---

## Installation

1. In Home Assistant, go to:
   **Settings → Add-ons → Add-on Store**

2. Click the **⋮ (three dots)** in the top-right corner → **Repositories**

3. Add https://github.com/cytechtech/ucmpi4

4. Install:
   **Cytech Comfort MQTT Bridge**

5. Configure the add-on (see below)

6. Start the add-on

---

## Home Assistant Integration

### Automatic Entity Creation (MQTT Discovery)

This add-on uses MQTT Discovery.

➡️ **No manual YAML configuration is required**

Once running:

- Entities are automatically created
- Devices appear under:

Comfort

---

### Available Entities

The following are automatically created:

- Alarm Control Panel
- Zone Inputs (binary sensors)
- Outputs and Flags (switches)
- Counters, Sensors, Timers (number entities)
- Battery & Power sensors

---

## Comfort Configuration File (CCLX)

To enable meaningful names (zones, outputs, etc.):

1. Open the add-on Web UI (Ingress panel)
2. Upload your `.cclx` file
3. Click **Validate**
4. Click **Apply**

The add-on will reload and update all entities.

If no CCLX file is provided, default names will be used.

---

## Battery & Power Monitoring

The add-on provides:

- Battery voltage
- DC supply voltage

---

## Alarm Control

The alarm panel integrates directly with Home Assistant.

Supported modes:

- Arm Home
- Arm Away
- Arm Night
- Disarm

### Custom Bypass (`#` Key)

Comfort requires the `#` key to confirm/bypass zones.


Home Assistant does not include a `#` key.

Example button:
```yaml
type: custom:button-card
name: Comfort # Key
icon: mdi:pound
tap_action:
  action: call-service
  service: alarm_control_panel.alarm_arm_custom_bypass
  target:
```
---

## Support

- Comfort Forums: https://comfortforums.com/

---

## Credits

Based on original projects:

- https://github.com/koochyrat/comfort2
- https://github.com/djagerif/comfort2mqtt

---

## License

Apache 2.0  
https://www.apache.org/licenses/LICENSE-2.0
