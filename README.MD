# Home Assistant Blueprints by Carsten Flokstra

Welcome to my collection of reusable Home Assistant blueprints! These blueprints simplify the creation of automations for alarms, lighting effects, notifications, and more. Whether you're looking to integrate motion sensors, dynamic lighting, or custom notifications, you'll find everything you need here.

---

## 📋 Table of Contents

- [Features](#features)
- [Blueprints Included](#blueprints-included)
- [Installation](#installation)
- [How to Use a Blueprint](#how-to-use-a-blueprint)
- [Example Configurations](#example-configurations)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

---

## 🚀 Features

- Simplify complex automations with pre-configured blueprints.
- Seamlessly control lighting with dynamic effects for Phillips Hue devices.
- Trigger alarms with customizable sounds, notifications, and lighting.

---

## 🧰 Blueprints Included

1. **Alarm Lights with Dynamic Speakers**  
   An enhanced version of the Alarm Lights blueprint with support for multiple media players.

3. **Phillips Hue Automation**  
   Automate and customize your Phillips Hue lights based on motion sensors, time of day, or other triggers.

---


## 🛠️ How to Use a Blueprint

1. Check the README.md on the different blueprints in the `blueprints` folder in this repository
2. Open Home Assistant and navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
3. Click on **Import Blueprint**.
4. Enter the raw URL of the blueprint file from this repository, for example:
   - For **Alarm Lights with Dynamic Speakers**:
     ```
      https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/main/blueprints/alarm-automation/alarm-automation.yaml    
     ```

   - For **Phillips Hue Automation Blueprint**:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/main/blueprints/phillips-hue-motion/phillips-hue-automation-blueprint.yml
     ```
4. Click **Preview** and then **Import Blueprint**.

---

## 🔧 Example Configurations

Here’s how you can use the blueprints:

```yaml
# Alarm Lights with Dynamic Speakers
automation:
  - alias: Dynamic Alarm Automation
    use_blueprint:
      path: carstenflokstra/alarm_lights_dynamic_speakers
      input:
        motion_sensor: binary_sensor.hallway_motion
        device_sensor: binary_sensor.door_sensor
        alarm_condition: input_boolean.arm_intruder_alarm
        media_players:
          - media_player.living_room
          - media_player.bedroom
        notification_device: mobile_app_iphone_van_carsten_flokstra
        alert_lights:
          - light.kitchen
          - light.hallway
        alert_playlist: https://open.spotify.com/playlist/exampleplaylistid
        flash_lights:
          - light.garden
          - light.front_door

# Phillips Hue Automation Blueprint
automation:
  - alias: Hue Motion-Based Lighting
    use_blueprint:
      path: carstenflokstra/phillips-hue-automation-blueprint
      input:
        motion_sensor: binary_sensor.kitchen_motion
        light_entity: light.kitchen_lights
        brightness_day: 100
        brightness_night: 20
        color_day: [255, 255, 255]
        color_night: [255, 128, 0]
        day_start: "07:00:00"
        night_start: "21:00:00"
```

---

## 🤝 Contributing

Contributions to this repository are welcome! If you have new blueprints, improvements, or bug fixes, feel free to open a pull request.

---

## 📜 License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

## 💬 Support

If you encounter any issues or have questions, open an issue in this repository or reach out via the Home Assistant Community Forum.

---

Happy Automating! 🚨✨
