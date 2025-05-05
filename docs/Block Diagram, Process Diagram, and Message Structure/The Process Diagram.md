[Process Diagram](https://app.diagrams.net/#G1YnGLDMCkIUuk0xOXI2Jxs83gCzxwHKuU#%7B%22pageId%22%3A%22pc2VwhXcHSOIUS0fXVyV%22%7D)

![Screenshot 2025-03-08 002553](https://github.com/user-attachments/assets/378fe910-acfc-4388-b1a4-41c9dcc8e059)

---
How the functionality of your communication sequence diagram satisfies user needs and product requirements 
---
The communication sequence diagram illustrates how user interactions and system components integrate to satisfy product requirements and ensure seamless data transmission. The system operates by processing temperature and humidity data collected from the sensor module, which communicates via **WiFi and UART** to the MQTT server. This data is then processed and displayed on the **HMI interface**, providing real-time environmental monitoring. Meanwhile, the **motor drive system** dynamically adjusts the water flow rate based on predefined temperature conditions.

The sequence begins when a **Web User** requests temperature and humidity readings. The sensor transmits the requested data via **WiFi and UART** to the **MQTT server**, which processes and updates the information. The **HMI system** displays these values, allowing users to track environmental conditions. If temperature levels exceed a threshold, the **motor actuator system** engages, adjusting the **flow of chilled water** to regulate temperature. Additionally, users can manually override motor settings through **Bluetooth or UART**, selecting different speed modes as needed.

The sequence diagram maintains alignment with the **block diagram**, ensuring that data flows systematically from the **MQTT system** to the **sensor processing module**, then to the **HMI display**, and finally to the **motor control system**. The structured message flow facilitates clear communication between components, with **event-driven interactions** triggering state changes and **recurring updates** maintaining system functionality. The diagram’s progression highlights the **real-world control capabilities** of the design, demonstrating how the system bridges the gap between **user requirements and automated responses**.

This approach ensures compliance with **class specifications**, including **I2C and UART integration**, while supporting the broader implementation of a **sensor-actuator-controlled cooling system**. The **well-defined communication hierarchy** and **efficient message handling** make this sequence diagram both accessible and directly applicable to the project's objectives.
