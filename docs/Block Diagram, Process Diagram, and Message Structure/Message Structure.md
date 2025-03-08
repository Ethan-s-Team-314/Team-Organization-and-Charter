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
