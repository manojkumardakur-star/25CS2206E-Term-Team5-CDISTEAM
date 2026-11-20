# 💧 Water Tank Level Monitoring for Villages using IoT and AWS Cloud

## 📌 Project Overview

Water Tank Level Monitoring is an IoT-based project designed to monitor water levels in village water tanks and reduce water wastage caused by overflow and manual operation.

The system uses an **ESP32 microcontroller and an ultrasonic water level sensor** to measure the water level continuously. Sensor readings are transmitted to AWS Cloud using Wi-Fi and MQTT. AWS services process and store the data, while an automated pump control mechanism helps maintain the required water level.

The project aims to provide an affordable and efficient solution for smart water management in rural areas.

## 🎯 Objectives

- Monitor water levels in tanks automatically.
- Measure water level in percentage.
- Prevent water overflow and water shortage.
- Automate water pump ON/OFF operations.
- Send sensor readings to AWS Cloud.
- Store water level data for future analysis.
- Generate alerts when water levels are critically low or high.
- Develop a low-cost IoT-based water management solution.

## 🏗️ System Architecture

The prototype follows this architecture:

```text
  Ultrasonic Sensor (JSN-SR04T)
             |
             v
       ESP32 Controller
             |
       Water Level
        Calculation
             |
             v
        Wi-Fi / MQTT
             |
             v
       AWS IoT Core
             |
             v
        AWS IoT Rule
             |
             v
        AWS Lambda
          /     \
         v       v
    DynamoDB    Amazon SNS
         |       |
         v       v
    Data Storage  Email Alerts

  ESP32 ---> Relay Module ---> Water Pump
             (Local Control)

  AWS Cloud ---> Monitoring Dashboard
```

## 🔧 Hardware Requirements

| Component | Purpose |
|---|---|
| ESP32 Development Board | Main microcontroller |
| JSN-SR04T Ultrasonic Sensor | Measures water level |
| Relay Module | Controls water pump |
| Mini DC Water Pump | Demonstrates automatic water filling |
| Water Containers | Prototype water tanks |
| Jumper Wires | Circuit connections |
| Breadboard | Hardware connections |
| Power Supply | Provides electrical power |
| Water Pipes | Transfers water |

## 💻 Software Requirements

| Software / Technology | Purpose |
|---|---|
| Arduino IDE | ESP32 programming |
| Embedded C/C++ | Sensor and controller programming |
| AWS IoT Core | Cloud communication |
| MQTT Protocol | Data transmission |
| AWS IoT Rules | Message routing |
| AWS Lambda | Data processing |
| Amazon DynamoDB | Storing sensor readings |
| Amazon SNS | Email notifications |
| Amazon CloudWatch | Monitoring and logs |
| HTML, CSS, JavaScript | Dashboard development |

## ⚙️ Working Principle

1. The ultrasonic sensor is installed at the top of the water tank.
2. The sensor measures the distance between itself and the water surface.
3. ESP32 receives the sensor readings.
4. The water level is calculated using the tank height and measured distance.
5. The water level is converted into a percentage.
6. ESP32 controls the water pump using a relay module.
7. Sensor readings are transmitted to AWS IoT Core through Wi-Fi and MQTT.
8. AWS IoT Rules forward the incoming data to AWS Lambda.
9. AWS Lambda processes the readings and stores them in DynamoDB.
10. Amazon SNS sends email notifications when predefined water-level conditions occur.
11. The monitoring dashboard displays water level and pump status.

## 📐 Water Level Calculation

Water level is calculated using:

**Water Height = Tank Height - Measured Distance**

Water percentage:

```text
Water Level (%) =
(Water Height / Tank Height) × 100
```

Example:

- Tank Height = 100 cm
- Measured Distance = 20 cm
- Water Height = 80 cm

Therefore:

```text
Water Level = (80 / 100) × 100

Water Level = 80%
```

## 🔄 Automatic Pump Control

The prototype uses threshold-based pump automation.

| Water Level | Pump Action |
|---|---|
| Below 20% | Pump ON |
| 20%–79% | Maintain previous state |
| 80% or above | Pump OFF |

Sensor failure and invalid readings must be handled safely to avoid incorrect pump operation.

## ☁️ AWS Cloud Integration

The following AWS services are used in the project:

- **AWS IoT Core:** Receives sensor data through MQTT.
- **AWS IoT Rules:** Routes incoming sensor messages.
- **AWS Lambda:** Processes water-level readings and checks conditions.
- **Amazon DynamoDB:** Stores water-level readings and pump status.
- **Amazon SNS:** Sends email alerts.
- **Amazon CloudWatch:** Monitors system activity and errors.

## 📊 Sample Sensor Data

Example JSON message sent to AWS:

```json
{
  "tank_id": "TANK001",
  "distance": 20,
  "water_level": 80,
  "pump_status": "OFF"
}
```

## 💰 Estimated Project Budget

| Component | Estimated Price |
|---|---:|
| ESP32 Development Board | ₹400 |
| JSN-SR04T Sensor | ₹389 |
| Relay Module | ₹62 |
| Mini DC Water Pump | ₹150 |
| Breadboard | ₹100 |
| Power Supply | ₹350 |
| Water Containers | ₹250 |
| Water Pipes | ₹50 |
| Jumper Wires | ₹60 |
| Resistors | ₹20 |
| USB Cable | ₹100 |
| Project Stand | ₹150 |
| Miscellaneous | ₹100 |
| **Estimated Total** | **₹2,181** |

*Prices are approximate and may vary depending on the supplier.*

Recommended overall budget: **₹2,200–₹2,400**.

The estimate assumes an existing laptop, Wi-Fi connection and AWS account. It excludes a LoRaWAN gateway.

## 🚀 Expected Results

- Real-time water-level monitoring.
- Automatic water-level percentage calculation.
- Automatic pump operation.
- Cloud-based sensor data storage.
- Email notifications for critical water levels.
- Reduced water wastage.
- Improved water management.

## 🔮 Future Enhancements

- Integrate LoRaWAN communication using the SX1276 module.
- Use a compatible LoRaWAN gateway with AWS IoT Core for LoRaWAN.
- Extend the system to multiple village water tanks.
- Develop a mobile application for remote monitoring.
- Add historical water consumption analysis.
- Implement predictive water management.
- Add solar power support for remote village installations.

## 🌱 Applications

- Village water supply systems.
- Smart water tanks.
- Agricultural water management.
- Rural water distribution.
- Residential water storage.
- Smart city infrastructure.

## 👨‍💻 Project Information

**Project Title:** Water Tank Level Monitoring for Villages using LoRaWAN

**Domain:** Water Level, Hydrology and Flood Management

**Technologies:** IoT, ESP32, Ultrasonic Sensor, MQTT, AWS Cloud

**Prototype Communication:** Wi-Fi and MQTT

**Future Communication Enhancement:** LoRaWAN

---

**Note:** This repository documents the proposed low-cost working prototype. Actual LoRaWAN communication will require additional LoRaWAN hardware and configuration.
