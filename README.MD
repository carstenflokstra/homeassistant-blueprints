# 🚀 Home Assistant Blueprints by Carsten Flokstra

Welcome to my collection of Home Assistant blueprints for automating alarms, Phillips Hue lighting, and more. Each blueprint is self-contained with its own documentation and YAML file for easy setup. 🎉

---

## 📋 Blueprints Included

### 1. [🔔 Alarm Automation](blueprints/alarm-automation/README.md)
A comprehensive alarm automation system that:
- Detects motion using multiple sensors. 👀
- Triggers customizable lighting effects. 💡
- Plays media (e.g., Spotify playlists or local files). 🎶
- Sends notifications to mobile devices. 📱
- Includes a "Kill Alarm" utility for resetting the system. 🛑

### 2. [🌈 Phillips Hue Motion Automation](blueprints/phillips-hue-motion/README.md)
An automation for motion-triggered Phillips Hue lighting or scenes, featuring:
- Motion detection to turn on lights or activate scenes. ✨
- Customizable dimming and delays before turning off. ⏳
- Options to ignore the automation if the lights are already on. 🛋️



## 🛠️ Usage

1. Open Home Assistant and navigate to **Settings** > **Automations & Scenes** > **Blueprints**. 🏠
2. Import the desired blueprint using the raw URL:
   - **Alarm Automation**:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/main/blueprints/alarm-automation/alarm-automation.yaml
     ```
   - **Phillips Hue Motion Automation**:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/main/blueprints/phillips-hue-motion/phillips-hue-automation-blueprint.yml
     ```
3. Follow the instructions in the blueprint’s README to configure your automation.

---

## 🔔 Alarm Automation

### 🌟 Features
- Motion detection using multiple sensors. 👀
- Customizable lighting effects for alarm triggers. 💡
- Media playback (Spotify playlists, songs, or local files). 🎵
- Mobile notifications for alarm events. 📲
- "Kill Alarm" feature to reset the alarm system. 🛑

### 📝 Example Configuration

```yaml
automation:
  - alias: Intruder Alarm
    use_blueprint:
      path: carstenflokstra/alarm-automation
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

## 🌈 Phillips Hue Motion Automation

### 🌟 Features
- Motion detection to turn on lights or activate scenes. ✨
- Dimming lights before turning off. 🌙
- Delays after motion stops to turn off lights. ⏳
- Conditional execution to ignore the automation if lights are already on. 🛋️

### 📝 Example Configuration

```yaml
automation:
  - alias: Motion Triggered Kitchen Light
    use_blueprint:
      path: carstenflokstra/phillips-hue-motion
      input:
        motion_sensor: binary_sensor.kitchen_motion
        target_entity: light.kitchen_light
        delay_duration: 180
        dimming_percentage: 50
        ignore_if_lights_on: true
```

---

## 📜 License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 💬 Support

If you encounter any issues, open an issue in this repository or refer to the [Home Assistant documentation](https://www.home-assistant.io/). 💡
