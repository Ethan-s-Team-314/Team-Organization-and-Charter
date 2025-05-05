[Process Diagram](https://app.diagrams.net/#G1YnGLDMCkIUuk0xOXI2Jxs83gCzxwHKuU#%7B%22pageId%22%3A%22pc2VwhXcHSOIUS0fXVyV%22%7D)

![Screenshot 2025-03-08 002553](https://github.com/user-attachments/assets/378fe910-acfc-4388-b1a4-41c9dcc8e059)

---
How the functionality of your communication sequence diagram satisfies user needs and product requirements 
---
The communication sequence diagram demonstrates how user interactions and system components work together to satisfy product requirements and ensure seamless data flow. The system operates by processing temperature and humidity data collected from Ethan’s sensor module, which communicates via WiFi and UART to Sanjit’s MQTT server. This data is then processed and displayed on Kevin’s HMI interface, providing users with real-time environmental monitoring. Meanwhile, Siddhant’s motor drive system dynamically adjusts the water flow rate, responding to temperature conditions based on predefined logic.

The user interaction sequence begins when a Web User requests temperature and humidity readings. The sensor transmits the data via WiFi and UART, sending it to the MQTT server, which processes and updates the information. The HMI system displays the temperature and humidity values, allowing users to monitor environmental conditions. If temperature thresholds indicate a need for cooling, Siddhant’s motor actuator system engages, adjusting the flow of chilled water to regulate the environment. Additionally, users can manually override motor settings through Bluetooth or UART, selecting various speed modes.

The sequence diagram aligns with the block diagram, ensuring that data moves efficiently from Sanjit to Ethan (sensor processing), then to Kevin (HMI display), and finally to Siddhant (actuation control). The structured message flow ensures clarity in communication between team members, with event-driven interactions triggering state changes and recurring updates maintaining system stability. The diagram’s logical progression highlights the real-world control capabilities of the design, bridging the gap between user needs and automated system responses.

This ensures that the system not only meets class specifications—such as I2C and UART integration—but also functions effectively within a sensor-actuator-controlled AC system model. The clear data flow between components, structured communication hierarchy, and well-defined message handling make this sequence diagram easy to understand and directly applicable to the project’s objectives.
