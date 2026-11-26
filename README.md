# Real-Time Gait Pattern Analysis and Abnormality Detection Using IoT Sensors and AWS IoT Core

## 1. Project Overview

This project is an IoT-based wearable gait monitoring system that captures and analyses a person's walking patterns in real time. It uses wearable sensors to collect movement and foot-pressure data and sends the collected information to AWS IoT Core for cloud processing and monitoring.

The system measures important gait parameters such as step count, stride length, walking speed, and body movement. It analyses these parameters to identify unusual walking patterns and provides useful insights for mobility assessment and rehabilitation monitoring.

The project integrates IoT sensors, an ESP32 microcontroller, and AWS cloud services to provide a connected gait monitoring solution.

## 2. Objectives

- Capture walking patterns using wearable IoT sensors.
- Measure step count, stride length, and walking speed.
- Monitor body movement using accelerometer and gyroscope sensors.
- Transmit sensor data securely to AWS IoT Core.
- Process and analyse gait data in real time.
- Detect unusual walking patterns using predefined thresholds.
- Store gait information for future analysis and monitoring.

## 3. Components Required

### Hardware Components

| Component | Purpose |
|---|---|
| ESP32 Microcontroller | Collects sensor data and connects to Wi-Fi |
| MPU6050 Sensor | Measures acceleration and angular movement |
| FSR Pressure Sensors | Detects foot pressure and contact |
| Jumper Wires | Establishes electrical connections |
| Breadboard | Supports circuit connections |
| Battery | Provides power supply |
| Wearable Straps | Attach sensors to the user's body or footwear |

### Software Components

- Arduino IDE
- Embedded C/C++
- Python
- MQTT Protocol
- AWS Management Console
- HTML, CSS and JavaScript for dashboard development

## 4. AWS Services Used

| AWS Service | Purpose |
|---|---|
| AWS IoT Core | Connects wearable devices and receives sensor data |
| AWS IoT Rules | Routes incoming sensor messages |
| AWS Lambda | Processes and analyses gait information |
| Amazon DynamoDB | Stores processed gait records |
| Amazon S3 | Stores datasets and reports |
| Amazon CloudWatch | Monitors logs and system performance |
| AWS IAM | Manages permissions and security |

## 5. System Architecture

The system follows the architecture below:

1. Wearable sensors collect walking-related data.
2. ESP32 reads the sensor values.
3. Sensor data is transmitted through Wi-Fi using MQTT.
4. AWS IoT Core receives the incoming data.
5. AWS IoT Rules trigger AWS Lambda.
6. Lambda processes the sensor readings and calculates gait parameters.
7. Processed information is stored in Amazon DynamoDB.
8. A dashboard displays gait measurements and abnormality alerts.

### Architecture Diagram

```text
       MPU6050 Sensor
              |
       FSR Pressure Sensors
              |
              v
       ESP32 Microcontroller
              |
         Wi-Fi / MQTT
              |
              v
         AWS IoT Core
              |
          IoT Rules
              |
              v
         AWS Lambda
              |
       +------+------+
       |      |      |
       v      v      v
   DynamoDB   S3   CloudWatch
       |
       v
   Dashboard
       |
       v
 Gait Analysis
       |
       v
Abnormality Alerts
```

## 6. Parameters Measured

### Step Count
Counts the number of steps taken during walking.

### Stride Length
Estimates the distance between two successive contacts of the same foot.

### Walking Speed
Calculates walking speed using estimated distance and time.

### Body Movement
Measures acceleration and angular movement using the MPU6050 sensor.

### Abnormality Detection
Identifies unusual walking patterns based on configured thresholds and comparison with baseline measurements.

## 7. Working Methodology

**Step 1: Sensor Data Collection**

Wearable sensors collect acceleration, gyroscope, and foot-pressure readings.

**Step 2: Microcontroller Processing**

ESP32 reads the sensor values and prepares the data for transmission.

**Step 3: Cloud Communication**

ESP32 sends sensor information to AWS IoT Core using MQTT over a secure connection.

**Step 4: Real-Time Processing**

AWS IoT Rules trigger Lambda functions to process incoming sensor data.

**Step 5: Gait Analysis**

The system calculates step count, stride length, walking speed, and movement characteristics.

**Step 6: Abnormality Detection**

The processed values are compared with configured thresholds or the user's baseline to identify unusual patterns.

**Step 7: Data Storage**

The processed information is stored in Amazon DynamoDB, with optional reports and datasets stored in Amazon S3.

**Step 8: Monitoring**

The dashboard displays gait measurements, walking patterns, and detected alerts.

## 8. Sample Sensor Data

Example JSON message transmitted to AWS IoT Core:

```json
{
  "deviceId": "gait-device-01",
  "timestamp": "2026-11-26T10:30:00Z",
  "accel": {
    "x": 0.12,
    "y": 0.08,
    "z": 9.71
  },
  "gyro": {
    "x": 0.02,
    "y": 0.01,
    "z": 0.04
  },
  "leftFootPressure": 420,
  "rightFootPressure": 395,
  "sessionId": "session-001"
}
```

## 9. Abnormality Detection

The system analyses gait parameters to identify possible irregularities.

The following conditions can be monitored:

- Unusual walking speed.
- Irregular step intervals.
- Differences in left and right foot timing.
- Unusual foot-pressure patterns.
- Changes in body movement.
- Deviations from previously recorded walking patterns.

These alerts are indicators for further review and are not medical diagnoses.

## 10. Implementation Steps

1. Connect MPU6050 and FSR sensors to ESP32.
2. Configure the Arduino IDE and required libraries.
3. Collect acceleration, gyroscope, and pressure readings.
4. Implement basic sensor filtering and step detection.
5. Create an AWS IoT Thing.
6. Configure device certificates and security policies.
7. Connect ESP32 to AWS IoT Core using MQTT.
8. Create an AWS IoT Rule.
9. Configure an AWS Lambda function for gait analysis.
10. Store processed information in Amazon DynamoDB.
11. Develop a dashboard to display the results.
12. Test the system using different walking patterns.

## 11. Testing and Evaluation

The system can be evaluated through the following tests:

- Sensor accuracy testing.
- Step-count comparison with manually counted steps.
- Walking speed estimation testing.
- Stride-length estimation testing.
- MQTT communication testing.
- AWS Lambda execution testing.
- Abnormality detection testing.
- Cloud data storage verification.

## 12. Expected Outcomes

- Real-time collection of walking-pattern data.
- Automatic step-count measurement.
- Stride-length and walking-speed estimation.
- Cloud-based gait data processing and storage.
- Detection of unusual walking patterns.
- Visual monitoring through a dashboard.
- Support for mobility assessment and rehabilitation monitoring.

## 13. Project Folder Structure

```text
gait-analysis-iot/
│
├── firmware/
│   ├── gait_sensor.ino
│   └── README.md
│
├── aws/
│   ├── iot-rule.sql
│   ├── lambda/
│   │   └── handler.py
│   └── dynamodb-schema.md
│
├── dashboard/
│   ├── src/
│   └── README.md
│
├── data/
│   └── sample_payload.json
│
├── docs/
│   ├── architecture.png
│   └── test-results.md
│
└── README.md
```

## 14. Security and Privacy

- Use secure MQTT communication with TLS certificates.
- Configure AWS IAM permissions.
- Protect device certificates and private keys.
- Do not upload credentials to GitHub.
- Use anonymised device identifiers.
- Restrict access to stored sensor data.

## 15. Future Enhancements

- Machine learning-based gait classification.
- Mobile application integration.
- Personalised gait monitoring.
- Advanced gait visualisation.
- Improved sensor calibration.
- Long-term walking-pattern analysis.

## 16. Conclusion

The Real-Time Gait Pattern Analysis and Abnormality Detection system combines wearable IoT sensors with AWS cloud services to monitor and analyse walking patterns. By measuring step count, stride length, walking speed, and body movement, the system can identify unusual gait variations and provide useful information for mobility monitoring and rehabilitation support.

The project demonstrates the integration of IoT hardware, cloud computing, real-time data processing, and sensor-based analysis.

---

## Team Details

- **Project Title:** Real-Time Gait Pattern Analysis and Abnormality Detection Using IoT Sensors and AWS IoT Core
- **Course:** Cloud Infrastructure and Services
- **Team Number:** 10
- **Section:** 3
- **Student Names:** Hima varshini , Siri Chandana , Sai Pranathi
- **Roll Numbers:** 2520030141 , 2520030142 , 2520030442
- **Project Guide:** Dr. Vinay Kumar
