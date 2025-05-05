# **Ideation and Concept Generation**

## **Team Members**

Ethan Peterson, Siddhant Kulkarni, Kevin Shah, Sanjit Selvakumar

---

## **Objective**
The purpose of this assignment is to generate innovative design features for our product and present alternative versions that align with the project requirements. This brainstorming process is aimed at ensuring that we develop a solution that is both effective and adaptable.

---

## **Project Description**
This project involves designing a modular system that utilizes UART communication between independently developed subsystems. Each team member is responsible for creating a surface-mount PCB, and the integrated system must function seamlessly for the Innovation Showcase. Key considerations include individual contributions, collaborative teamwork, and strict adherence to technical requirements such as microcontroller specifications, ECAD tool usage, and the daisy-chain communication protocol. Success will be defined by effective planning, thorough testing, and compliance with integration and documentation standards.

---

## **Science Exhibit Intentions**

### **1. Exhibit Goal**
The weather monitoring system is designed to illustrate meteorological data collection principles. It aims to teach students how environmental sensors work, highlight scientific measurement processes, and facilitate an understanding of cause-and-effect relationships in weather systems. Through interactive and hands-on experiences, students will gain insights into how atmospheric data is collected, analyzed, and visualized.

### **2. Target Audience**
The exhibit is intended for K-12 students, encompassing a wide age range (approximately 6-16 years) and diverse learning needs. The design must accommodate different learning styles, physical capabilities, and levels of scientific understanding. The system must be accessible for young learners while offering a more in-depth, engaging experience for high school students.

---

## **Key Design Considerations**

### **1. How will we make the device easy to use?**
We will incorporate visual cues as a primary guiding tool. A well-structured, visually appealing design will attract students and sustain their interest. Additionally, tactile cues will be included—such as textured buttons and handles—to enhance accessibility for younger users and those with visual impairments.

### **2. Designing Interactive Controls**
Controls will be designed for simplicity, ensuring intuitive interactions with minimal explanation. Large push buttons and a touchscreen interface featuring drag-and-drop functionalities will allow users to easily navigate through the system.

### **3. Durability, Safety, and Comfort**
Durability, safety, and comfort are crucial considerations. The product will be constructed using robust materials that can withstand frequent use and potential misuse. Safety features such as emergency stop buttons and well-insulated electrical components will be integrated to meet necessary safety standards.

### **4. Instructional Design**
We will provide concise, on-device instructions using diagrams and short phrases located next to control elements. Interactive tutorials will also be available to guide students through system operation and enhance learning.

### **5. Avoiding Common Pitfalls in Science Exhibits**
To ensure effectiveness, we will:
- Avoid information overload by presenting concise, digestible content.
- Actively collect feedback to refine usability.
- Gain insights into user needs to tailor functionality effectively.
- Maintain conceptual consistency across all design elements.
- Design an experience that captures and sustains interest through interactive engagement.

---

## **Brainstorming Process**

[**EGR 314 Ideation Slides**](https://docs.google.com/presentation/d/1-jR1jT5JZCxH_XFAIzBFzMHgu-b0iQvdZxi1QXmcdSc/edit)

1. Our team categorized ideas into **Physics & Engineering**, **Chemistry & Material Science**, **Biology & Life Sciences**, and **Earth & Space Science**.
2. Each idea was ranked as **High, Medium, or Low priority** based on feasibility and project alignment.
3. The refined selection of ideas was documented in **Figure 1.2: Remaining Brainstormed Ideas**.
4. The top concepts, grouped by category, are showcased in **Figure 1.7: Snapshot of all Categories**.

### **Brainstorming Figures**

![Group of All Ideas](https://github.com/user-attachments/assets/1e00de76-5686-465f-b138-50225f9b2257)
*Figure 1.1: Group of All Ideas*

![Remaining Brainstormed Ideas](https://github.com/user-attachments/assets/3b4b366b-1fe7-4888-9008-b8bff55f9f06)
*Figure 1.2: Remaining Brainstormed Ideas*

---

## **Categorizing Our Brainstormed Ideas**

To organize our 100 ideas effectively, we grouped them into four major categories:
- **Physics & Engineering**
- **Chemistry & Material Science**
- **Biology & Life Sciences**
- **Earth & Space Science**

Highly rated ideas are marked with ***
Moderately considered ideas are marked with **
Least prioritized ideas are marked with *

![Physics and Engineering](https://github.com/user-attachments/assets/5323e01a-194b-4e6a-bae6-79369f9c7c50)
*Figure 1.3: Physics & Engineering*

![Chemistry and Materials Science](https://github.com/user-attachments/assets/4efae097-51d8-4c32-afc8-e6fd8f5d637b)
*Figure 1.4: Chemistry & Materials Science*

![Biology and Life Sciences](https://github.com/user-attachments/assets/d05eb711-f997-4e66-866b-5d0b22dbb364)
*Figure 1.5: Biology & Life Sciences*

![Earth and Space Projects](https://github.com/user-attachments/assets/f15dccd1-fe54-4295-9df9-29adfab7508f)
*Figure 1.6: Earth & Space Science*

---

## **Concept Sketches**

### **Developing Visual Representations**

![Screenshot 2025-03-07 223601](https://github.com/user-attachments/assets/c6580f80-2849-43cd-b637-b025bacc0ccb)

*Figure 5.1 - AI-Generated Representation of Project*

![Screenshot 2025-03-07 223638](https://github.com/user-attachments/assets/e3a333c3-b451-4b26-abd6-c3ed7dca48a6)

*Figure 5.2 - Overview of Weather Data Collection System*

Page Description on how our device using the figures given behave in an science exhibit enviroment
---

The Weather Data Collection System (WDC) is an interactive exhibit designed to engage K-12 students in hands-on learning about meteorology. It incorporates a user-friendly interface, robust environmental protection, and clear instructional cues to enhance accessibility and usability. The system integrates ESP32 and PIC18F47Q10 microcontrollers, an I2C-based LCD display, and multiple sensors (DHT11 for temperature/humidity, BMP180 for atmospheric pressure) to provide real-time weather data collection and visualization.

The weather and humidity monitoring system, as depicted in Figure 5.1 and further detailed in Figure 5.2, addresses critical issues raised in the "Suggested Guidelines for Designing Interactive Exhibits" by incorporating robust functionality and thoughtful design. Figure 5.2 highlights the integration of key components such as the ESP32, PIC18F47Q10, I2C communication protocol, and specific sensors like the DHT11 for temperature and humidity. These components form a comprehensive and interactive Weather Data Collection System (WDC), ensuring both technical reliability and user accessibility.

One of the challenges highlighted in the guidelines is the need for devices to provide implicit cues for usage. The annotated Figure 5.2 demonstrates the inclusion of a clear, labeled LCD display that utilizes I2C communication for seamless data transmission, ensuring accurate and real-time updates of weather information such as temperature, humidity, and atmospheric pressure. This setup adheres to the principle of "visibility," as discussed in the guidelines, where devices are designed to make their operation intuitively clear. For instance, the ESP32 manages communication and processing while displaying updates, which eliminates ambiguity for users.

The inclusion of tactile buttons, as shown in Figure 5.2, ensures effective mapping, as each control corresponds directly to its functionality, such as toggling data views or resetting sensors. This design minimizes user errors and enhances interaction, aligning with the guideline that "mapping helps to minimize incorrect responses" (p. 8). Furthermore, the PIC18F47Q10 acts as an additional microcontroller, managing peripheral devices like the DHT11 and BMP180, which measure temperature, humidity, and pressure respectively. These components communicate effectively through the I2C protocol, enabling accurate data collection and display.

Durability and safety remain a core focus of this system. The detailed annotations in Figure 5.2 emphasize the use of robust materials for the device's enclosure, protecting sensitive electronics from environmental stressors like rain or heat. Safety measures such as insulated wiring and stable sensor mounts prevent hazards, supporting the recommendation that "interactive devices must be safe for visitors of all ages" (p. 8). Additionally, portability and ergonomic design ensure user comfort, making the WDC suitable for diverse audiences.

Instructions for using the WDC are minimal yet effective, as reflected in the system’s design. The combination of clear on-device labels, simplified text on the LCD, and the logical arrangement of controls ensures ease of use, particularly for first-time users. By placing instructions near relevant controls and avoiding overloading users with information, the system adheres to the principle that "instructions should be easily available, kept simple, and layered for accessibility" (p. 9).

Incorporating the features shown in Figure 5.2, including I2C communication, temperature and humidity sensors, the ESP32, and PIC18F47Q10, this weather monitoring system addresses user needs while tackling challenges in interactivity, durability, and safety. By adhering to the design principles outlined in the "Suggested Guidelines for Designing Interactive Exhibits," the system effectively bridges technical complexity and user-friendly interaction, making it an ideal educational tool for museum visitors.

---

## **Final Design Selection Process**
Our decision-making process involved evaluating the best ideas from our brainstorming session based on feasibility, impact, and modularity. After discussions with stakeholders and additional research, we refined our concept to incorporate:
- **A highly interactive weather monitoring system**
- **Intuitive control mechanisms for accessibility**
- **A visually engaging and scientifically informative experience**

If deviations from our initial concept occurred, they were driven by insights gained from testing, research, and expert recommendations.

---
How this process Affected the decision making process to create an AC system
---
After going through the design process, we encountered several challenges that required us to deviate from our initial ideas. We had to adapt our approach to ensure the system met all requirements, considering the new information that emerged along the way.

We incorporated strong ideas, such as implementing a temperature sensor, which is a versatile component that fulfills multiple class requirements and serves a wide range of purposes. Conversely, we eliminated ineffective elements, such as the sensor's voltage regulator and the decision to hand-solder components like the PIC and ESP, as these led to numerous complications.

Our goal was to develop a highly interactive system, which is why we integrated an MQTT server for data processing. This allowed us to track temperature and motor status, similar to how the HMI system functioned. Additionally, we pursued an ambitious approach by creating an app that enables remote motor control while providing real-time temperature feedback based on motor status.

The concept behind our project was to transition agricultural temperature and filtering systems into a sensor- and actuator-controlled traditional AC system. When the system detects a high temperature, the actuator reverses, permitting chilled water to flow past it and into the cooling system, effectively lowering the room’s temperature. In a real-world implementation, chilled water would need to be actively circulated, but our system focuses on controlling that process efficiently.

Video Presentation
---
<iframe class="responsive" width="560" height="315" src="https://www.youtube.com/embed/7UG-YCw4WZ8?si=zjqBop_FBaR4tDm3" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
---

## **Conclusion**
The brainstorming and ideation process was instrumental in developing our vision for the weather monitoring system. Our final selection combines accessibility with interactivity, ensuring a scientifically rich and engaging learning experience for K-12 students. The next steps will involve prototyping, user testing, and refining the system based on user feedback.

---
