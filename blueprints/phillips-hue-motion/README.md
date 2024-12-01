 # Motion Triggered Automation Blueprint

This blueprint allows you to automate your Phillips Hue (or other compatible) lights or scenes based on motion detection. It includes options for delay, dimming before turning off, and conditional triggering based on the current state of the lights.

---

## Features

- **Motion Detection**: Trigger a light or scene when motion is detected.
- **Dimming Before Turn-Off**: Optionally dim the lights before turning them off.
- **Delay Duration**: Set a delay after motion stops before turning off the lights.
- **State Awareness**: Prevent the automation from triggering if the lights are already on.

---

## Prerequisites

### Compatible Devices
- A motion sensor entity (e.g., Hue Motion Sensor or other `binary_sensor` devices).
- A target entity to control:
  - A light (e.g., `light.kitchen_light`).
  - A scene (e.g., `scene.relax`).

---

## Installation

1. **Import the Blueprint**:
   - Open Home Assistant and navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
   - Click **Import Blueprint** and paste the raw URL:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/main/phillips-hue-automation-blueprint.yml
     ```

2. **Create an Automation**:
   - Go to **Settings** > **Automations & Scenes** > **Create Automation** > **From Blueprint**.
   - Select **Motion Triggered Automation** from the list.

---

## Configuration Options

When creating an automation using this blueprint, you can customize the following inputs:

### Inputs

| Name                  | Description                                                                                | Default      |
|-----------------------|--------------------------------------------------------------------------------------------|--------------|
| **Motion Sensor**     | The motion sensor entity to monitor.                                                      | _Required_   |
| **Target Entity**     | The entity to control (light or scene).                                                    | _Required_   |
| **Delay Duration**    | Time in seconds to wait after motion stops before dimming or turning off the lights.       | `120`        |
| **Dimming Percentage**| Brightness percentage to set before turning off (if applicable).                          | `30`         |
| **Ignore if Lights On** | Prevent the automation from triggering if the lights are already on.                     | `false`      |

---

## Example Configuration

Here’s an example of how you might configure the automation:

```yaml
automation:
  - alias: Motion Triggered Kitchen Light
    use_blueprint:
      path: carstenflokstra/phillips-hue-automation-blueprint
      input:
        motion_sensor: binary_sensor.kitchen_motion
        target_entity: light.kitchen_light
        delay_duration: 180
        dimming_percentage: 50
        ignore_if_lights_on: true
```

### Explanation

- The kitchen light turns on when motion is detected.
- If no motion is detected for 180 seconds, the light dims to 50% brightness.
- After 10 seconds at 50% brightness, the light turns off completely.
- If the light is already on, the automation will not trigger.

---

## Tips

1. **Scenes**:
   - Use `scene.turn_on` to activate scenes when motion is detected.
   - Example: `scene.relax`.

2. **Conditional Triggering**:
   - Use the `Ignore if Lights Are On` option to avoid redundant triggers.

3. **Customizing Timings**:
   - Adjust the `Delay Duration` and `Dimming Percentage` inputs to suit your needs.

---

## License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Support

If you encounter any issues, open an issue in this repository or refer to the [Home Assistant documentation](https://www.home-assistant.io/).

---

