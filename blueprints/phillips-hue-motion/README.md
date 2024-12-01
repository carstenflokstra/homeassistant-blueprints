# 🌟 Motion Triggered Automation Blueprints

This repository contains two blueprints to automate your lights or scenes based on motion detection. You can either control lights with brightness and color options or activate scenes directly. 💡✨

---

## ✨ Features

### Motion Triggered Lights
- **Motion Detection**: Trigger one or more lights when motion is detected. 👀
- **Dimming Before Turn-Off**: Optionally dim the lights before turning them off. 🌙
- **Customizable Brightness and Color**: Set brightness and RGB color for your lights. 🎨
- **Delay Duration**: Set a delay after motion stops before turning off the lights. ⏳

### Motion Triggered Scenes
- **Motion Detection**: Trigger one or more scenes when motion is detected. 👀
- **Scene Activation**: Directly activate scenes without additional configuration. ✨
- **Delay Duration**: Set a delay after motion stops before deactivating the scenes. ⏳

---

## ⚙️ Prerequisites

### Compatible Devices
- A motion sensor entity (e.g., Hue Motion Sensor or other `binary_sensor` devices). 👾
- A target entity to control:
  - A light (e.g., `light.kitchen_light`). 💡
  - A scene (e.g., `scene.relax`). ✨

---

## 📥 Installation

### Motion Triggered Lights
1. **Import the Blueprint**:
   - Open Home Assistant and navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
   - Click **Import Blueprint** and paste the raw URL:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/refs/heads/main/blueprints/phillips-hue-motion/motion-triggered-lights.yaml
     ```

2. **Create an Automation**:
   - Go to **Settings** > **Automations & Scenes** > **Create Automation** > **From Blueprint**.
   - Select **Motion Triggered Lights** from the list. 🎉

---

### Motion Triggered Scenes
1. **Import the Blueprint**:
   - Open Home Assistant and navigate to **Settings** > **Automations & Scenes** > **Blueprints**.
   - Click **Import Blueprint** and paste the raw URL:
     ```
     https://raw.githubusercontent.com/carstenflokstra/homeassistant-blueprints/refs/heads/main/blueprints/phillips-hue-motion/motion-triggered-scenes.yaml
     ```

2. **Create an Automation**:
   - Go to **Settings** > **Automations & Scenes** > **Create Automation** > **From Blueprint**.
   - Select **Motion Triggered Scenes** from the list. 🎉

---

## 🔧 Configuration Options

### Motion Triggered Lights

| Name                  | Description                                                 | Default      |
|-----------------------|-------------------------------------------------------------|--------------|
| **Motion Sensor**     | The motion sensor entity to monitor.                        | _Required_   |
| **Lights**            | The lights to control.                                      | _Required_   |
| **Light Color**       | RGB color for lights when motion is detected.               | `[255,255,255]` |
| **Brightness**        | Brightness percentage for lights when motion is detected.   | `100`        |
| **Delay Duration**    | Time in seconds to wait after motion stops before dimming or turning off the lights. | `120` |

---

### Motion Triggered Scenes

| Name                  | Description                                                 | Default      |
|-----------------------|-------------------------------------------------------------|--------------|
| **Motion Sensor**     | The motion sensor entity to monitor.                        | _Required_   |
| **Scenes**            | The scenes to activate when motion is detected.             | _Required_   |
| **Delay Duration**    | Time in seconds to wait after motion stops before deactivating the scenes. | `120` |

---

## 📝 Example Configurations

### Motion Triggered Lights

```yaml
automation:
  - alias: Motion Triggered Kitchen Lights
    use_blueprint:
      path: carstenflokstra/motion-triggered-lights
      input:
        motion_sensor: binary_sensor.kitchen_motion
        lights:
          - light.kitchen_light
        light_color: [255, 200, 100]
        brightness: 80
        delay_duration: 180
```

### 💡 Tips
1.  Scenes: Use scene.turn_on to activate scenes when motion is detected. Example: scene.relax. 🛋️✨
Customizing Timings:

2. Adjust the Delay Duration to suit your needs. ⏰
Brightness and Color:

3. Fine-tune the Brightness and Light Color for the perfect ambiance. 🎨

### 📜 License
This repository is licensed under the MIT License. See the LICENSE file for details.

### 💬 Support
If you encounter any issues, open an issue in this repository or refer to the Home Assistant documentation. 💡

