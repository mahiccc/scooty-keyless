# Scooty Keyless System

A smart keyless ignition system for your scooter using the **Seeed Studio XIAO ESP32-S3**. This project features a Captive WiFi Portal, Deep Sleep power saving, and Bluetooth Proximity Auto-Unlock.

## Hardware & Wiring

| Component | XIAO ESP32-S3 Pin | Description |
|-----------|-------------------|-------------|
| **Ignition Relay** | `D0` | Triggers the main ignition circuit |
| **Starter Relay**  | `D1` | Triggers the self-start motor |
| **Buzzer**         | `D2` | Used for locate bike and feedback sounds |
| **Green LED**      | `D3` | Unlocked status indicator |
| **Red LED**        | `D4` | Locked status indicator |
| **Vibration Sensor**| `D5` (GPIO 6) | Hardware interrupt to wake from deep sleep |
| **GND**            | `GND` | Common ground for all components |
| **VCC**            | `5V` | Power supply input |

## Features

- **Captive WiFi Portal:** When you connect to the `"MyScooty-Keyless"` WiFi network, a login page pops up automatically. You can turn the ignition on/off, trigger the starter, or ring the buzzer directly from your browser.
- **True Deep Sleep:** When inactive for 5 minutes, the ESP32 completely shuts down its WiFi and Bluetooth radios, drawing negligible power to save your battery.
- **Vibration Wake-Up:** The scooter rests in deep sleep until the vibration sensor is triggered. 
- **BLE Proximity Auto-Unlock:** You can pair your phone with the scooter securely via the portal. When the scooter wakes up from a bump, it turns on its Bluetooth scanner. If your phone is in your pocket nearby, it automatically turns the ignition ON!
- **Adjustable Sensitivity:** You can dynamically change both the vibration sensor sensitivity and the Bluetooth auto-unlock range via the web portal.

## How to Pair your Phone for Auto-Unlock

1. Connect to the **"MyScooty-Keyless"** WiFi.
2. In the portal, scroll down and click **"Enable Bluetooth Discovery"**. 
3. The portal will display a secure **6-digit PIN**.
4. Go to your phone's Bluetooth settings and tap **"Scooty_Pair"**.
5. When prompted, enter the PIN.
6. The ESP32 will automatically save your phone's Bluetooth MAC address, add it to the whitelist, and disable pairing mode. 
7. Enable the **"Auto Unlock on Vibration"** toggle. You're good to go!
