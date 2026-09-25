# IoT-Based Air Pollution Monitoring System

An automated, cloud-connected Internet of Things (IoT) solution designed to monitor real-time atmospheric air quality, ambient temperature, and relative humidity. Utilizing an ESP8266 microchip, the system relays environmental sensor telemetry directly to an interactive cloud analytics dashboard for real-time surveillance and research data collection.

---

## 📌 Problem Statement
Rapid global urbanization, industrial expansions, population surges, and rising vehicular density have led to exponential growth in atmospheric pollution. This deterioration poses severe threats to human respiratory health and structural environmental stability. 

This project provides an automated, low-cost architectural solution capable of detecting trace amounts of harmful gases—including carbon dioxide ($\text{CO}_2$), smoke, alcohol, benzene, ammonia ($\text{NH}_3$), and nitrogen oxides ($\text{NO}_x$)—over a remote cloud server using web-based visualization widgets.

---

## 📊 System Architecture & Component Mapping

### High-Level Data Flow

### 🔌 Circuit Diagram
To reconstruct this physical system, refer to the wiring specification illustrated below:

| Sensor Component | NodeMCU ESP8266 Pin | Description |
| :--- | :--- | :--- |
| **MQ135** `VCC` | `Vin` | 5V Power Input |
| **MQ135** `GND` | `GND` | Common Ground |
| **MQ135** `AOUT` | `A0` | Analog Air Quality Telemetry |
| **DHT11** `VCC` | `3V3` | 3.3V Power Input |
| **DHT11** `GND` | `GND` | Common Ground |
| **DHT11** `DATA` | `D4` | Digital Temperature/Humidity Signal |

*(Place your hardware schematic illustration inside an `images/` directory at the repository root and reference it below)*
```markdown
![Circuit Schematic Placeholder](images/circuit_diagram.png)
```

---

## ⚙️ Core Technical Implementation

### 1. Atmospheric Metrics & Sensor Modalities
* **Temperature & Humidity Tracking (DHT11):** Employs a capacitive humidity sensor element combined with a Negative Temperature Coefficient (NTC) thermistor. It converts precise ambient analog measurements into an structured digital signal outputted on its data pin. 
* **Gas & Pollution Profiling (MQ135):** Utilizes an internal tin dioxide (SnO₂) semiconductor layer with variable internal conductivity. Upon pre-heating, the onboard potentiometer sets digital alerting thresholds. The analog variation maps directly onto integer PPM metrics transmitted to the microprocessor.

### 2. Cloud Configuration & Microcontroller Firmware
The firmware instantiates on a **NodeMCU 1.0 (ESP-12E Module)** architecture. The program assigns physical device readings onto properties hosted on **Arduino IoT Cloud**:
1. **Instantiation:** Opens communication ports to sync with connected peripherals.
2. **Network Handshake:** Authenticates using specified local Wi-Fi credentials and an encrypted network secret key.
3. **Execution Loop:** Continuously samples physical sensor pins, computes floating metrics, and routinely runs the cloud synchronization library task to maintain low-latency dashboard state alignment.

---

## 🚀 Setup, Testing & Deployment

### Hardware Prerequisites
* NodeMCU ESP8266 (ESP-12E Module)
* MQ135 Gas Sensor Module
* DHT11 Temperature & Humidity Sensor
* Micro-USB Data Cable

### Software Installation Sequence
1. Download and run the [Arduino Create Agent](https://arduino.cc) to enable local browser-to-hardware communication bridges.
2. Log into the **Arduino IoT Cloud Console**.
3. Under the **Things** section, construct a configuration mapping these cloud properties:
   * `humidity` (`CloudRelativeHumidity`)
   * `temperature` (`CloudTemperatureSensor`)
   * `sensorValue` (`int` PPM Meter)
   * `msg` (`String`)
4. Copy the repository firmware codebase into your cloud web editor workspace, assign local network Wi-Fi configuration properties, and compile/flash the software onto your connected NodeMCU over your active `COM` port.

---

## 📈 Live Cloud Analytics Dashboard

The platform processes telemetry data into structured graphical arrays, enabling real-time environmental insights:

```markdown
![Telemetry Analytics Dashboard UI](images/dashboard_screenshot.png)
```

### Key Technical Advantages
* **Optimized Operational Cost:** Achieves extensive multispectral gas analysis utilizing only two fundamental sensor frameworks.
* **Low Deployment Latency:** Highly structured, plug-and-play architecture facilitates straightforward end-point deployments.
* **Remote Survey Ingestion:** Consolidated time-series historical data can be immediately parsed into analytics formats for research surveys.

---

## 🔮 Future Enhancements
* **Advanced Particulate Arrays:** Integrate an optical **PMS5003** sensor to accurately profile microscopic $\text{PM}_{2.5}$ particles.
* **Expanded Gas Profiling:** Implement dedicated **MP503** and **MQ-131** sensor arrays for precise volatile organic compounds (VOCs) and Ozone tracking.
* **Edge Field Diagnostics:** Interface dedicated physical LCD/OLED screens along with audio buzzers to sound localized panic metrics.

---

## 👥 Contributors & Team Members
* **Masood Ahmed Mohiuddin** (Seat No: 1604-19-737-043)

---

## 📖 Academic References
1. Shah, H. N., Khan, Z., Merchant, A. A., Moghal, M., Shaikh, A., & Rane, P. (2018). *IoT Based Air Pollution Monitoring System*. International Journal of Scientific & Engineering Research, Volume 9, Issue 2.
2. Anand Jayakumar, A., Praviss Yesyand, T. K., Venkatesh Prashanth, K. K., & Ramkumar, K. (2021). *IoT Based Air Pollution Monitoring System*. International Research Journal of Engineering and Technology (IRJET), Volume 08, Issue 03.
