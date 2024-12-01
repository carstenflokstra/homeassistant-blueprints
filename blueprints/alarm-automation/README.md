# 🚨 Home Assistant Alarm Blueprints

This repository contains flexible and dynamic blueprints for Home Assistant to manage alarms, notifications, lighting effects, and media playback. 🎉

---

## ✨ Features

### 🔔 Alarm Automation
- **Multi-Sensor Support**: Trigger the alarm using one or more motion sensors. 👀
- **Dynamic Media Playback**: Play a Spotify playlist, song, or local file during the alarm. 🎵
- **Custom Volume Control**: Set different volume levels for daytime and nighttime. 🔊
- **Integrated Notifications**: Send push notifications to a mobile device. 📲
- **Lighting Effects**: Turn on and flash selected lights during the alarm. 💡

### 🛑 Kill Alarm
- **Reset Alarm System**: Disable and re-enable the alarm automation. 🔄
- **Stop Media Playback**: Stop and clear playlists on media players. 🎶❌
- **Turn Off Lights**: Automatically turn off lights after disabling the alarm. 🌙

---

## ⚙️ Prerequisites

### 🔐 Input Boolean for Arming the Alarm
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

### 🛎️ Input Button for Kill Alarm
- Create an `input_button` to trigger the Kill Alarm automation.
- Example configuration in `configuration.yaml`:

```yaml
  input_button:
    kill_alarm:
      name: Kill Alarm
```      

- For more details, refer to the [Home Assistant Input Button documentation](https://www.home-assistant.io/integrations/input_button/).

---

## 🛠️ How to Use

### 🔔 Alarm Automation

1. **Import the Blueprint**:
   - Go to **Settings** > **Automations & Scenes** > **Blueprints**.
   - Click **Import Blueprint** and paste the raw URL:
 https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/refs/heads/main/blueprints/alarm-automation/alarm-automation.yaml

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
- Use the custom input boolean to toggle the alarm on or off. 🛡️
---
### 🛑 Kill Alarm

1. **Import the Blueprint**:
- Go to **Settings** > **Automations & Scenes** > **Blueprints**.
- Click **Import Blueprint** and paste the raw URL:
https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/refs/heads/main/blueprints/alarm-automation/kill-alarm.yml

2. **Create an Automation**:
- Navigate to **Settings** > **Automations & Scenes**.
- Click **Create Automation** > **From Blueprint**.
- Select the imported blueprint and configure:
  - Kill button
  - Alarm automation
  - Media player areas
  - Light areas

---

## 📝 Example Configuration

### 🔔 Alarm Automation

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

### 🛑 Kill Alarm
```yaml
automation:
- alias: Kill Alarm System
 use_blueprint:
   path: carstenflokstra/kill_alarm_blueprint
   input:
     kill_button: input_button.kill_alarm
     alarm_automation: automation.intruder_alarm
     media_areas:
       - living_room
       - bedroom
     light_areas:
       - kitchen
       - hallway
```       

---

## 📜 License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 💬 Support

If you encounter any issues, open an issue in this repository or refer to the [Home Assistant documentation](https://www.home-assistant.io/). 💡
