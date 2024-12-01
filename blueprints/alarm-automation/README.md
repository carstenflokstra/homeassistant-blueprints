# Home Assistant Alarm Blueprint

This blueprint provides a flexible and dynamic alarm automation for Home Assistant. It triggers notifications, lighting effects, and media playback when motion is detected. It supports multiple motion sensors, dynamic media URLs, and custom volume settings.

---

## Features

- **Multi-Sensor Support**: Trigger the alarm using one or more motion sensors.
- **Dynamic Media Playback**: Play a Spotify playlist, song, or local file during the alarm.
- **Custom Volume Control**: Set different volume levels for daytime and nighttime.
- **Integrated Notifications**: Send push notifications to a mobile device.
- **Lighting Effects**: Turn on and flash selected lights during the alarm.

---

## Prerequisites

1. **Input Boolean for Arming the Alarm**:
   - Create an `input_boolean` to control when the alarm is armed.
   - Example configuration in `configuration.yaml`:
     ```yaml
     input_boolean:
       arm_intruder_alarm:
         name: Arm Intruder Alarm
         initial: off
         icon: mdi:shield-lock
     ```
   - For more details, refer to the [Home Assistant Input Boolean documentation](https://www.home-assistant.io/integrations/input_boolean/).

2. **Supported Media URLs**:
   - The `media_url` input accepts:
     - A Spotify playlist or song URL (e.g., `https://open.spotify.com/playlist/...`).
     - A local file path (e.g., `/media/alarmsound.mp3`).
     - A direct URL to a media file (e.g., `http://example.com/sound.mp3`).

---
## How to Use

1. **Import the Blueprint**:
   - Go to **Settings** > **Automations & Scenes** > **Blueprints**.
   - Click **Import Blueprint** and paste the raw URL:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/main/alarm_lights_dynamic.yaml
     ```

2. **Create an Automation**:
   - Navigate to **Settings** > **Automations & Scenes**.
   - Click **Create Automation** > **From Blueprint**.
   - Select the imported blueprint and configure:
     - Motion sensors
     - Lights
     - Media players
     - Notification device
     - Media URL
     - Volume settings

3. **Arm the Alarm**:
   - Use the custom input boolean to toggle the alarm on or off.

---

## Example Configuration

```yaml
automation:
  - alias: Intruder Alarm
    use_blueprint:
      path: carstenflokstra/alarm_lights_dynamic
      input:
        motion_sensors:
          - binary_sensor.hallway_motion
          - binary_sensor.kitchen_motion
        alarm_condition: input_boolean.arm_intruder_alarm
        media_players:
          - media_player.living_room
          - media_player.bedroom
        notification_device: mobile_app_carsten_phone
        alert_lights:
          - light.kitchen
          - light.hallway
        media_url: https://open.spotify.com/playlist/exampleplaylist
        day_volume: 0.5
        night_volume: 0.2
```

---

## License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Support

If you encounter any issues, open an issue in this repository or refer to the [Home Assistant documentation](https://www.home-assistant.io/).

---

