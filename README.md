# ESP32-IoT-Industrial-Automation-dashboard
An IoT-based industrial monitoring and automation system that uses an ESP32, temperature sensor, and gas sensor to monitor environmental conditions in real time. Sensor readings are uploaded to Firebase Realtime Database and displayed on a web dashboard to support industrial safety and monitoring.

##  Project Overview

Industrial environments may experience high temperatures and gas leakage, which can create unsafe working conditions. Manual monitoring may not always identify these conditions quickly.

This project uses IoT technology to monitor temperature and gas levels continuously. When sensor readings cross predefined thresholds, the system provides alerts and demonstrates machine-status control. The dashboard displays sensor readings and system status, while Firebase stores current and historical data.

##  Objectives

- Monitor industrial temperature and gas levels in real time.
- Use ESP32 to collect and process sensor readings.
- Send sensor data to Firebase Realtime Database.
- Display live sensor readings and alerts on a web dashboard.
- Demonstrate automated responses to abnormal conditions.
- Maintain historical readings for monitoring and analysis.

##  Technologies Used

| Technology | Purpose |
|---|---|
| ESP32 | Reads sensors and controls output devices |
| DHT22 | Measures temperature and humidity |
| MQ-2 Gas Sensor | Detects combustible gases and smoke |
| Firebase Realtime Database | Stores sensor readings |
| HTML, CSS and JavaScript | Builds the web dashboard |
| Arduino IDE / ESP32 code | Programs the microcontroller |
| Wokwi | Simulates the hardware circuit |
| GitHub | Stores project files and documentation |
| GitHub Pages | Hosts the dashboard website |

##  Key Features

### 1. Real-Time Temperature Monitoring
The DHT22 sensor measures the surrounding temperature. The ESP32 reads the sensor data and sends it to Firebase for display on the dashboard.

### 2. Gas and Smoke Monitoring
The MQ-2 sensor provides readings that indicate changes in gas or smoke levels. Predefined thresholds are used to identify warning and critical conditions.

### 3. Firebase Data Storage
Firebase Realtime Database stores the latest sensor values under the `/current` path and historical records under the `/history` path.

### 4. Web Dashboard
The dashboard is designed to display temperature, gas readings, system status, and available historical information.

### 5. Alert and Automation Logic
When the readings cross configured thresholds, the ESP32 can activate indicators and a buzzer. A machine-status LED demonstrates the automation response in the simulation.

##  System Architecture

```text
DHT22 Temperature Sensor ──┐
                           │
MQ-2 Gas Sensor ───────────┤
                           ▼
                         ESP32
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
       LEDs and Buzzer           Wi-Fi Connection
                                         │
                                         ▼
                               Firebase Realtime DB
                                         │
                                         ▼
                                  Web Dashboard
```

##  Hardware Components

- ESP32 development board
- DHT22 temperature and humidity sensor
- MQ-2 gas sensor
- Green LED
- Yellow LED
- Red LED
- Buzzer
- Connecting wires
- Breadboard, if required

**Note:** The project can be tested in Wokwi before building the physical circuit.

##  Software Requirements

- A web browser
- A Wokwi account for simulation
- An Arduino-compatible ESP32 development environment
- A Firebase project with Realtime Database enabled
- A GitHub account for source code and website hosting

##  Working Principle

1. The ESP32 connects to the Wi-Fi network.
2. The DHT22 measures the ambient temperature.
3. The MQ-2 sensor provides a gas-related analog reading.
4. The ESP32 compares sensor readings against predefined thresholds.
5. LEDs and a buzzer indicate normal, warning, or critical conditions according to the programmed logic.
6. The latest readings are uploaded to Firebase under `/current`.
7. Historical readings are added under `/history`.
8. The web dashboard retrieves available Firebase data and displays it to the user.

##  Example Alert Thresholds

The following values are example settings used in the current prototype firmware. They should be calibrated and validated before practical use.

| Parameter | Example threshold |
|---|---:|
| Temperature warning | 35°C |
| Temperature critical | 45°C |
| Gas warning | 1800 |
| Gas critical | 2800 |

**Important:** MQ-2 readings are not automatically equivalent to gas concentration in ppm. Reliable concentration measurements require suitable calibration. The thresholds above are prototype values, not certified industrial safety limits.

##  Firebase Database Structure

The database is designed to use the following paths:

```text
/
├── current/
│   ├── temperature
│   ├── humidity
│   ├── gas
│   └── status
│
└── history/
    └── record_id/
        ├── temperature
        ├── humidity
        ├── gas
        └── status
```

The exact field names depend on the firmware and dashboard implementation. Keep them consistent between both.

**Firebase Database URL:**

https://iot-industial-automation-default-rtdb.asia-southeast1.firebasedatabase.app

Security recommendation: Configure appropriate Firebase Realtime Database rules. Do not leave public write access enabled in a deployed project.

##  Project Links

- **Live Dashboard:** Add your published GitHub Pages URL here after deployment.
- **AI Studio App:** (https://ais-pre-3obj5sthkek7y4a22vrch4-686394919506.asia-southeast1.run.app/)
- **GitHub Repository:** Add your repository URL here.
- **Wokwi Simulation:** Add your simulation URL here if you have saved and shared the circuit.

##  How to Run the Project

### Step 1: Open the Simulation
Open your Wokwi ESP32 project and check that the ESP32, DHT22, MQ-2 sensor, LEDs, and buzzer are connected correctly.

### Step 2: Configure the Firmware
Add the required Wi-Fi and Firebase configuration to your ESP32 code. For Wokwi simulation, the usual network settings are:

```cpp
const char* WIFI_NAME = "Wokwi-GUEST";
const char* WIFI_PASSWORD = "";
```

Use the correct Firebase database URL and configure the HTTP requests as required by your firmware.

### Step 3: Start the Simulation
Run the simulation and check the serial monitor for Wi-Fi connection messages, sensor readings, and Firebase upload responses.

### Step 4: Verify Firebase Data
Open the Firebase Realtime Database console and check whether the `/current` values are updated and `/history` records are being added.

### Step 5: Open the Dashboard
Open your deployed dashboard website. Confirm that it can access the required Firebase data and displays the readings correctly.

##  Expected Results

- Temperature and humidity readings are obtained from the DHT22.
- Gas-related readings are obtained from the MQ-2 sensor.
- The ESP32 evaluates readings against programmed thresholds.
- Indicators and the buzzer respond according to the alert logic.
- Sensor data is sent to Firebase when the connection and database configuration are working.
- The dashboard presents available sensor readings and system status.

Actual results depend on sensor behaviour, Wi-Fi connectivity, Firebase permissions, and dashboard configuration.

##  Future Enhancements

- Add SMS, email, or mobile notifications for critical alerts.
- Introduce sensor calibration and more reliable gas-concentration measurement.
- Add graphs and downloadable historical reports.
- Add user authentication and role-based dashboard access.
- Add multiple sensor nodes for monitoring different industrial areas.
- Integrate a properly rated industrial relay and fail-safe shutdown mechanism where appropriate.
- Improve connectivity recovery and error logging.

##  Safety Disclaimer

This project is an educational prototype for IoT monitoring and automation. A simulated machine-status LED does not physically shut down industrial equipment. Do not use this prototype as the sole safety system for real machinery or gas-leak protection. Practical deployment requires calibrated sensors, appropriate certified safety equipment, secure database configuration, and professional validation.

##  Project Summary

The IoT-Based Industrial Automation System demonstrates how ESP32, environmental sensors, Wi-Fi, Firebase Realtime Database, and a web dashboard can be combined to monitor industrial conditions remotely. The prototype provides sensor monitoring, threshold-based alerts, data storage, and a foundation for future industrial automation improvements.

---

**Project Status:** Prototype / Educational Project

**License:** Add a license if you want others to reuse or modify the source code.
