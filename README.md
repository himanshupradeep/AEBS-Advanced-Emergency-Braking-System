# Advanced Emergency Braking System (AEBS)

## Description  
A CAN-based ECU simulation demonstrating an **Advanced Emergency Braking System (AEBS)**. Integrates AEB ECU, Engine ECU, and HMI ECU. Covers simulation setup, DBC creation, user interface design, and CAPL scripting for safety-critical automation.

---

## What is AEBS?  

![image](https://github.com/user-attachments/assets/8be43040-388c-4c0d-9da7-f506fe5fe9ac)
Image Source : https://allautoexperts.com/understanding-emergency-braking-systems-how-they-work-and-save-lives-in-2023

**AEBS** stands for **Advanced Emergency Braking System**, a vehicle safety feature that autonomously initiates braking to prevent or mitigate collisions when the driver fails to react in time. It actively monitors for obstacles and engages warnings or braking based on proximity and speed.

---

## Purpose of AEBS  
- Reduce accidents through early intervention  
- Enhance safety for drivers and passengers  
- Support drivers during emergency braking scenarios  

### AEBS is useful in:  
- Urban driving with frequent stops  
- Highway cruising with unpredictable traffic  
- Parking environments with close-range obstacles  

---

## How AEBS Works

![image](https://github.com/user-attachments/assets/aa029927-35a5-41e2-926e-8be55cd6835e)

Image Source : https://fuso-singapore.com/solid-functional-design-super-great/advanced-emergency-braking-system-aebs/

1. **Obstacle Detection** – Radar or camera sensors detect obstacles in the host lane and calculate distance, closing speed, and stopping range.  
2. **Data Processing** – Sensor input is analyzed by ECUs to determine relevance and urgency.  
3. **Warning Phase** – HMI system provides audible/visual alerts for potential collisions.  
4. **Braking Assistance** – Partial braking if the driver doesn’t respond in time.  
5. **Full Emergency Braking** – Complete brake override if no driver reaction occurs.

---

![ScreenRecording2025-06-21183514-ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/0cc46674-9ca5-4812-9cd1-45c173e5fdef)


## Project Phases

### 1. Simulation  

![Screenshot 2025-06-21 181919](https://github.com/user-attachments/assets/777d1b2e-724e-4b10-8a96-7248260433a5)
![Screenshot 2025-06-21 181941](https://github.com/user-attachments/assets/ba88432a-2f5e-4fff-9027-d18bd7a6f061)


- Adds AEB, Engine, and HMI nodes into CANoe  
- Loads DBC for signal/message definitions  
- Simulates live environment for AEBS scenarios  

### 2. Database Creation  

![Screenshot 2025-06-21 182050](https://github.com/user-attachments/assets/be2af993-bdc1-4068-a90e-840b3bbbca15)

- Defines ECUs, signals, messages, and transmission logic  
- Assigns directionality to signals  
- Includes environment variables for simulation triggers  

### 3. Panel Creation  

![Screenshot 2025-06-21 182513](https://github.com/user-attachments/assets/e3c95b36-390c-423a-82ec-d7a5355686ca)


- Builds an interactive HMI for displaying AEBS states  
- Inputs simulate sensor data and object proximity  
- Live feedback showcases system transitions and warnings  

### 4. CAPL Script  

![Screenshot 2025-06-21 182640](https://github.com/user-attachments/assets/0d1114ca-06b4-415a-85c9-b084098a8dac)


- Implements threshold logic and system reactions  
- Reads inputs from environment variables  
- Sends appropriate outputs (warnings/braking) based on distance  
- Logs system states and ECU responses during simulation  

---

## AEBS Measurement Levels

- **Level 1** – Warning initiated at a distance of **6–7 meters**  
- **Level 2** – Urgent warning between **4–6 meters**  
- **Level 3** – Critical braking if the object is within **4 meters**  

---

## Activity Flow

1. Start  
2. Detect relevant objects  
3. Continuously monitor distance  
4. If object is 6–7 m away → trigger **Level 1 AEBS warning**  
5. If object is 4–6 m away → trigger **Level 2 AEBS warning**  
6. If object is <4 m → AEBS overrides and applies full braking  
7. End  

---

## Test Cases

1. AEBS ECU continuously listens on CAN bus  
2. Receives object distance from RADAR system  
3. Based on proximity, triggers appropriate AEBS level response  
4. HMI warning indicators are updated via CAN  

---

## ECU and Diagnostics Communication

### AEBS ECU  
1. Listens for obstacle data via CAN  
2. Sends warning signals to HMI  
3. Manages Level 1 & 2 warnings  
4. Reduces throttle and initiates braking  

### Tester ECU  
1. Sends periodic CAN messages  
2. Monitors real-time object proximity  
3. Sends updates to HMI  
4. Takes over controls when required  

---

## ECU Network Architecture

| Node       | Transmits                             | Receives        |
|------------|---------------------------------------|-----------------|
| **AEB**    | Emergency Braking, HMI Warning        | —               |
| **HMI**    | ACC, Brakes, Engine Indicators        | HMI Warning     |
| **Engine** | Engine Speed, Acceleration            | Brake           |

---



## License - Open Source
This project is open for educational use and learning purposes. Feel free to fork, modify, or contribute!


