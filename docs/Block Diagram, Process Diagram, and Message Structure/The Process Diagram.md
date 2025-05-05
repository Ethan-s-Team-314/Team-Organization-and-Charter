[Process Diagram](https://app.diagrams.net/#G1YnGLDMCkIUuk0xOXI2Jxs83gCzxwHKuU#%7B%22pageId%22%3A%22pc2VwhXcHSOIUS0fXVyV%22%7D)

![Screenshot 2025-03-08 002553](https://github.com/user-attachments/assets/378fe910-acfc-4388-b1a4-41c9dcc8e059)

---
How the functionality of your communication sequence diagram satisfies user needs and product requirements 
---
The communication sequence diagram illustrates how user interactions and system components integrate to satisfy product requirements and ensure seamless data transmission. The system operates by processing temperature and humidity data collected from the sensor module, which communicates via **WiFi and UART** to the MQTT server. This data is then processed and displayed on the **HMI interface**, providing real-time environmental monitoring. Meanwhile, the **motor drive system** dynamically adjusts the water flow rate based on predefined temperature conditions.

The sequence begins when a **Web User** requests temperature and humidity readings. The sensor transmits the requested data via **WiFi and UART** to the **MQTT server**, which processes and updates the information. The **HMI system** displays these values, allowing users to track environmental conditions. If temperature levels exceed a threshold, the **motor actuator system** engages, adjusting the **flow of chilled water** to regulate temperature. Additionally, users can manually override motor settings through **Bluetooth or UART**, selecting different speed modes as needed.

The sequence diagram maintains alignment with the **block diagram**, ensuring that data flows systematically from the **MQTT system** to the **sensor processing module**, then to the **HMI display**, and finally to the **motor control system**. The structured message flow facilitates clear communication between components, with **event-driven interactions** triggering state changes and **recurring updates** maintaining system functionality. The diagram’s progression highlights the **real-world control capabilities** of the design, demonstrating how the system bridges the gap between **user requirements and automated responses**.

This approach ensures compliance with **class specifications**, including **I2C and UART integration**, while supporting the broader implementation of a **sensor-actuator-controlled cooling system**. The **well-defined communication hierarchy** and **efficient message handling** make this sequence diagram both accessible and directly applicable to the project's objectives.

---
Top 5 changes to software desingn
---
### Top 5 Biggest Changes to Software Design Since the Software Proposal  

1. **Sensor Rework and Integration**  
   Initially, the team encountered issues with sensor selection, requiring multiple iterations to find a reliable temperature and humidity sensor. The previous sensors either failed due to voltage inconsistencies or were incompatible with the system’s communication protocol. The team ultimately selected the **AHT21**, which offered stable data transmission and was easy to integrate using **I2C communication**. This change ensured accurate environmental readings, improving system functionality and satisfying project requirements. The **UML sequence diagram** illustrates how sensor data is properly transmitted via **WiFi and UART**, ensuring reliable communication with the MQTT system and motor subsystem.  

2. **HMI Rework for User Interaction and Proper Display**  
   The initial HMI design lacked clarity in displaying temperature and humidity readings, creating difficulties for user interaction. The team reworked the HMI structure to properly visualize real-time environmental data, ensuring that users could access updates efficiently. The improvements included optimizing **SPI communication** and refining **display logic**, ensuring that sensor readings were correctly formatted. This refinement is reflected in the **sequence diagram**, where the **HMI now processes and displays information** received from the MQTT system and motor drive, ensuring proper user feedback.  

3. **Byte System Redesign for Data Transmission**  
   The initial approach to **byte-based communication** caused misinterpretations between subsystems, leading to incorrect actuator responses and inconsistent data flow. The team redefined the **8-byte structure**, ensuring each subsystem clearly understands its role and can process messages accurately. This involved assigning **specific bytes** to **source ID, destination ID, message data, and control flags**, ensuring seamless integration between the **sensor, motor drive, MQTT system, and HMI display**. The **UML diagram** highlights structured message transmission, demonstrating how systems now exchange properly formatted data without errors.  

4. **MPLAB Code Functionality and API Integration**  
   Initially, there were significant challenges in implementing **MPLAB code** for the **PIC microcontroller**, particularly in defining the API structure for subsystem communication. The team overcame this issue by carefully debugging the MPLAB code and structuring the API so that identification of users and devices followed a logical format. This update allowed **proper recognition of commands** from different components, ensuring seamless message routing. The **UML sequence diagram** now correctly represents this improved interaction, showing how messages flow from the sensor subsystem to the motor drive and MQTT system without data loss or misinterpretation.  

5. **Synchronization of Sensor Data Across Subsystems**  
   One of the biggest challenges was ensuring that sensor data was **properly translated** across all subsystems so that every component remained in sync. Early versions of the system had **timing mismatches**, causing incorrect actuator responses. The team resolved this by refining **data transmission timing**, adding **delays** where necessary, and ensuring that **each subsystem processes temperature readings in real time**. The **UML diagram** illustrates how information is processed correctly through structured communication delays, ensuring smooth synchronization across all components.  

These refinements ensure that the system meets **user needs, project specifications, and class requirements**, improving both **functionality and real-world applicability**. The **UML sequence diagram** validates these changes by accurately depicting **sensor communication, actuator responses, data transmission, and user interaction** throughout the system.

