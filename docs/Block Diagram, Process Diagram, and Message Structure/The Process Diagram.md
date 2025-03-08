[Process Diagram](https://drive.google.com/drive/u/1/folders/19I_488VRz9nsvQRNoa4jgeBesulI3tln)
![Screenshot 2025-02-14 at 10 56 16 PM](https://github.com/user-attachments/assets/52425764-7ec4-4a00-8f8a-8b84439fadad)


---
mermaid
  sequenceDiagram
    actor WebUser as Web User
    participant ESP32 as Sanjit: ESP-32
    participant PIC as Sanjit: PIC
    participant Ethan as Ethan
    participant Siddhant as Siddhant
    participant Kevin as Kevin
    actor InPerson as In-Person

    WebUser->>ESP32: Get me information for today's weather<br>Via WiFi
    ESP32->>PIC: Display message in LCD<br>Via UART
    PIC->>Ethan: Updates speed settings and prepares for sensor data calibration
    PIC->>Siddhant: "Temperature: 30°C<br>Humidity: 80%"<br>Via I2C
    Siddhant->>Kevin: "Water Flow Rate: 50 L/min"<br>Via I2C
    Kevin->>InPerson: Set Speed to 200 m/s

    ESP32->>PIC: Sends information of Temperature, Humidity, and Water Flow Rate<br>Via UART
    PIC->>PIC: Process information<br>Speed, Temperature, Humidity, and Water Flow Rate
    PIC->>Siddhant: "Speed: 200 m/s<br>Temperature: 30°C<br>Humidity: 80%<br>Water Rate: 50 L/min"<br>Via SPI
    Siddhant->>Kevin: LCD Displays weather information
    Kevin->>WebUser: Weather information is displayed
---
