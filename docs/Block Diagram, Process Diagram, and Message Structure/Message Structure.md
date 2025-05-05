
---
**Message Structure: Design and Decision-Making Process**
---
Our team's **message structure design** was carefully developed to ensure **clear data transmission**, **efficient routing**, and **precise subsystem interactions**. We structured each message using a **byte-based format**, including clearly defined **headers, source IDs, destination IDs, message data, and footers**, ensuring that all components correctly interpret and respond to data. The decision-making process involved analyzing how each team member’s subsystem contributes to the overall communication flow. **Ethan’s sensor system** collects **temperature and humidity readings** and transmits them via **UART and WiFi**, ensuring accurate environmental monitoring. **Sanjit’s web subsystem** processes and forwards sensor readings to the **MQTT server**, storing and publishing updated data. **Kevin’s HMI subsystem** receives and displays **temperature, humidity, and water flow rate** information, ensuring users have real-time system feedback. **Siddhant’s motor subsystem** uses sensor data to **adjust actuator states**, controlling cooling mechanisms based on temperature levels. The sequence diagram demonstrates how each component interacts, with messages structured to maintain **recurring updates** (automatic temperature readings) and **event-driven interactions** (manual motor adjustments via Bluetooth and UART). Our format also incorporates **system integrity mechanisms**, ensuring valid message transmission without corruption. By structuring our communication logic around a **fixed byte format**, we allow for **scalable, expandable control**, ensuring **seamless data processing across I2C, SPI, UART, and MQTT protocols**. This approach guarantees that our system functions reliably, meeting **user needs and project requirements**, while allowing **real-world implementation for sensor-actuator-controlled cooling systems**.


## Team Member Roles

| **Team Member** | **Role**           | **Character ID** |
|-----------------|--------------------|------------------|
| Siddhant        | Motor Subsystem    | S                |
| Ethan           | Sensor Subsystem   | E                |
| Kevin           | HMI Subsystem      | K                |
| Sanjit          | Web Subsystem      | T                |

---

## Message Table (Message Type Overview)

| **Message Type**              | **Message ID Type: uint8_t** | **Ethan Role: Sensor ID: E** | **Siddhant Role: Motor ID: S** | **Kevin Role: HMI ID: K** | **Sanjit Role: WebID: T** |
|-------------------------------|-------------------------------|-------------------------------|-------------------------------|----------------------------|----------------------------|
| sensor value                  | 0x40                          | Send: Turn motor on or off.  | Receive: Motor turns off or on due to temperature reading. | Receive: (displayed on HMI) | Receive: (mqtt topic: /EGR314/TEAMXYZ/SENSOR1) |

---

## Detailed Message Flow Table

| **Message Purpose**           | **Message ID (8 bytes)**     | **Sender**   | **Receivers**             | **Description**                                                                 |
|------------------------------|------------------------------|--------------|----------------------------|---------------------------------------------------------------------------------|
| Send Temperature Data        | `FSTE01FS`                   | Sanjit (T)   | Ethan (E)                  | Sanjit sends temperature sensor data to Ethan.                                 |
| Forward Temp to HMI + Web    | `FSET43FS`, `FSEK43FS`       | Ethan (E)    | Sanjit (T), Kevin (K)      | Ethan sends processed temperature (43) to Kevin (HMI) and Sanjit (Web).        |
| Motor Off Command            | `FSTS01FS`                   | Sanjit (T)   | Ethan (E)                  | Sanjit requests motor OFF; Ethan checks if it applies to him and acts if so.   |
| Motor OFF Status → Kevin & T | `FSST01FS`, `FSSK01FS`       | Ethan (E)    | Sanjit (T), Kevin (K)      | Ethan informs Kevin and Sanjit of updated motor status (motor OFF).            |
| Motor ON Command (example)   | `FSTS02FS`                   | Sanjit (T)   | Ethan (E)                  | Similar process for turning motor ON; `02` could represent ON.                 |
| Motor ON Status → Kevin & T  | `FSST02FS`, `FSSK02FS`       | Ethan (E)    | Sanjit (T), Kevin (K)      | Status update to others showing motor is ON.                                   |

## Siddhant Messages

| **Action**               | **Message ID** | **Recipient** | **Description**            |
|--------------------------|----------------|---------------|----------------------------|
| Motor OFF                | `FSST01FS`     | Sanjit        | Motor off status update    |
|                          | `FSSK01FS`     | Kevin         | Motor off status update    |
| Motor Reverse Status     | `FSST02FS`     | Sanjit        | Motor is reversing         |
|                          | `FSSK02FS`     | Kevin         | Motor is reversing         |
| Motor Forward Status     | `FSST03FS`     | Sanjit        | Motor is running forward   |
|                          | `FSSK02FS`     | Kevin         | Motor is running forward   |

---

## Ethan Messages

| **Message ID** | **Sender** | **Recipient** | **Description**                                |
|----------------|------------|----------------|------------------------------------------------|
| `FSEK00FS`     | Ethan      | Kevin          | Temperature message (`00` = temperature)       |
| `FSET00FS`     | Ethan      | Sanjit         | Temperature message (`00` = temperature)       |
| `FSES00FS`     | Ethan      | Siddhant       | Temperature message (`00` = temperature)       |

---

## Sanjit Messages to Ethan 

| **Message ID** | **Sender** | **Recipient** | **Description**     |
|----------------|------------|----------------|---------------------|
| `FSSE03FS`     | Sanjit     | Ethan          | Command to turn on  |

## Kevin Messages

| **Message ID** | **Sender** | **Recipient** | **Description**     |
|----------------|------------|----------------|---------------------|
| `FSEK00FS`     | Ethan     | Kevin          | Temperature to be sent  |
| `FSSK01FS`     | Siddhant  | Kevin          | Motor off  |
| `FSEK02FS`     | Siddhant     | Kevin        | Forward Motor  |
| `FSEK03FS`     | Siddhant     | Kevin          | Reverse Motor  |



# General Message Structure

| **Byte Range** | **Description**                                                                 |
|----------------|---------------------------------------------------------------------------------|
| 0 - 1          | **Header** (0x41 0x5A)                                                          |
| 2              | **Source ID** (uint8_t)                                                         |
| 3              | **Destination ID** (uint8_t)                                                    |
| 4 - 61         | **Message Data** (Variable Length < 58 Bytes)                                   |
| 62 - 63        | **Footer** (0x59 0x42)                                                          |

---

# Message Types

## 1. Set System Speed
Used when the In-person or Web-Person sets a command speed.  
Sent from ESP32 and PIC18F47Q10.

| **Byte** | **Description**                       | **Data Type** |
|----------|---------------------------------------|---------------|
| 1-2      | Message Type (1 = Set Speed)          | uint16_t      |
| 3-4      | Speed Value (e.g., 200m/s)            | uint16_t      |

---

## 2. Request Sensor Data
Used when ESP32 requests sensor data from PIC18F47Q10.  
PIC18F responds with temperature, humidity, and water flow rate.

| **Byte** | **Description**                         | **Data Type** |
|----------|-----------------------------------------|---------------|
| 1-2      | Message Type (2 = Request Sensor Data)  | uint16_t      |
| 3        | Sensor ID (1 = DHT11, 2 = SEN0229)     | uint8_t       |

---

## 3. Sensor Data Response
Used when PIC18F sends sensor data back to ESP32.  
Contains multiple sensor readings in a single message.

| **Byte** | **Description**                         | **Data Type** |
|----------|-----------------------------------------|---------------|
| 1-2      | Message Type (3 = Sensor Data Response) | uint16_t      |
| 3-4      | Temperature (°C × 100, e.g., 25.5°C = 2550) | uint16_t      |
| 5-6      | Humidity (% × 100, e.g., 50.1% = 5010)  | uint16_t      |
| 7-8      | Water Flow Rate (L/min × 100, e.g., 10.5 L/min = 1050) | uint16_t |

---

## 4. LCD Update Command
Sent from ESP32 to LCD (via SPI).

| **Byte** | **Description**                              | **Data Type** |
|----------|----------------------------------------------|---------------|
| 1-2      | Message Type (4 = LCD Update Command)        | uint16_t      |
| 3-58     | Text String (e.g., “Speed: 200 m/s, Temperature: 30°C, Water flow Rate = 50 L/min”) | char[55]      |

---

## 5. Cloud Update
Sent from ESP32 to cloud via Wi-Fi.

| **Byte** | **Description**                              | **Data Type** |
|----------|----------------------------------------------|---------------|
| 1-2      | Message Type (5 = Cloud Update)              | uint16_t      |
| 3-58     | JSON String (Sensor Data)                    | char[55]      |

---

## 6. Error Message
Network Failure, Signal Loss.

| **Byte** | **Description**                              | **Data Type** |
|----------|----------------------------------------------|---------------|
| 1-2      | Message Type (6 = Error Message)             | uint16_t      |
| 3        | Subsystem ID (1 = PIC18, 2 = ESP32, 3 = Temperature Sensor, 4 = Water Turbine, 5 = LCD) | uint8_t       |
| 4-58     | Error String                                 | char[55]      |

---

# Example Message Format

For a message requesting sensor data from PIC18F47Q10:

**Header**: 0x41 0x5A  
**Source ID**: 0x01 (ESP32)  
**Destination ID**: 0x02 (PIC18F47Q10)  
**Message Data**:  
- Message Type: 0x02 (Request Sensor Data)  
- Sensor ID: 0x01 (DHT11)  
**Footer**: 0x59 0x42
