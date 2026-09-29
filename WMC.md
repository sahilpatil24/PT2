# WMC PT-II — 5 Mark Solutions

**Syllabus:** Module 4, Module 5, Module 6 (6.1, 6.2, 6.3)

---

## Q1. Explain the three fundamental propagation mechanisms: Reflection, Diffraction and Scattering.
### (5 Marks)

Radio waves travel from transmitter to receiver through different propagation mechanisms. The three fundamental mechanisms are **reflection, diffraction and scattering**.

### 1. Reflection
Reflection occurs when a radio wave strikes a **large surface** whose dimensions are much larger than the wavelength.

**Examples:** Buildings, walls, ground and large vehicles.

The wave is reflected back after hitting the surface. Reflected waves can combine with the direct signal and cause **multipath propagation and fading**.

### 2. Diffraction
Diffraction occurs when a radio wave encounters an **obstacle or sharp edge** and bends around it.

It allows the signal to reach areas where there is no direct line of sight.

**Example:** A signal bending around the edge of a building.

### 3. Scattering
Scattering occurs when radio waves encounter **small objects or rough surfaces** and are redirected in many directions.

**Examples:** Trees, lamp posts and street signs.

Scattering creates multiple signal paths and can cause **fading and distortion**.

**Remember:** Reflection → Bounce, Diffraction → Bend, Scattering → Spread.

---

## Q2. Explain Multipath Propagation and Fading.
### (5 Marks)

### Multipath Propagation
Multipath propagation occurs when a transmitted radio signal reaches the receiver through **multiple different paths**.

It occurs due to:
- Reflection
- Diffraction
- Scattering

Therefore, the receiver receives multiple copies of the same signal with different **strengths and arrival times**.

### Fading
Fading is the **variation in received signal strength** caused by multipath propagation.

- **Constructive interference:** Signals add together → stronger signal.
- **Destructive interference:** Signals cancel each other → weaker signal.

### Effects of Fading
- Signal strength fluctuates
- Data errors increase
- Voice quality decreases
- Calls may drop
- Communication reliability decreases

### Types
1. **Small-scale fading** – rapid variation over a short distance/time.
2. **Large-scale fading** – slower variation mainly associated with path loss and shadowing.

---

## Q3. What is the difference between Path Loss and Shadowing?
### (5 Marks)

### Path Loss
Path loss is the **decrease in received signal power as the distance between transmitter and receiver increases**.

It mainly depends on:
- Distance
- Frequency
- Propagation environment

### Shadowing
Shadowing occurs when **obstacles block or weaken the radio signal** between transmitter and receiver.

**Examples:** Buildings, trees, hills and large structures.

### Difference

| Path Loss | Shadowing |
|---|---|
| Mainly caused by increasing distance | Mainly caused by obstacles |
| Generally predictable | Random/slowly varying |
| Signal decreases with distance | Signal is weakened by blockage |
| Example: moving farther from a tower | Building blocks the signal |

**Conclusion:** Path loss represents signal-power reduction due to distance, while shadowing represents additional signal variation caused by obstacles.

---

## Q4. Explain Noise in Wireless Systems. Discuss Thermal Noise and External Noise, their Sources and Impact on Communication Quality.
### (5 Marks)

**Noise** is an unwanted electrical signal that interferes with the desired communication signal. It reduces the **Signal-to-Noise Ratio (SNR)** and affects communication quality.

### 1. Thermal Noise
Thermal noise is produced due to the **random movement of electrons** in electronic components.

**Sources:**
- Resistors
- Electronic circuits
- Receivers
- Communication equipment

### 2. External Noise
External noise originates **outside the communication equipment**.

**Sources:**
- **Atmospheric noise:** Lightning and thunderstorms
- **Man-made noise:** Electrical machines, vehicles and power lines
- **Cosmic noise:** Radiation from space

### Impact on Communication Quality
Noise can cause:
- Reduced SNR
- Increased data errors
- Poor voice quality
- Reduced transmission quality
- Reduced communication reliability
- Reduced communication range

**Conclusion:** Noise interferes with the desired wireless signal and reduces the quality and reliability of communication.

---

## Q5. What is Co-channel Interference and Adjacent Channel Interference? Explain their Causes and Effects.
### (5 Marks)

### 1. Co-channel Interference (CCI)
Co-channel interference occurs when **two or more cells use the same frequency channel** and their signals interfere with each other.

**Cause:** Frequency reuse.

**Effects:**
- Reduced signal quality
- Increased errors
- Reduced capacity
- Poor voice/data communication

### 2. Adjacent Channel Interference (ACI)
Adjacent channel interference occurs when a signal from a **nearby frequency channel interferes with the desired channel**.

**Causes:**
- Imperfect filters
- Improper frequency planning
- Signals from nearby channels

**Effects:**
- Signal distortion
- Increased errors
- Reduced communication quality

### Difference

| CCI | ACI |
|---|---|
| Same frequency | Nearby/adjacent frequencies |
| Mainly due to frequency reuse | Mainly due to imperfect filtering/frequency planning |
| Interference from co-channel cells | Interference from neighboring channels |

---

## Q6. State and Explain the Interference Mitigation Techniques Used in Wireless Communication.
### (5 Marks)

Interference can be reduced using the following techniques:

### 1. Frequency Planning
Frequencies are properly assigned to cells so that interference between neighboring cells is minimized.

### 2. Power Control
Transmission power is controlled so that the required signal strength is maintained without unnecessarily creating interference.

### 3. Sectoring
A cell is divided into sectors using directional antennas. This reduces interference from other cells.

### 4. Cell Splitting
A large cell is divided into smaller cells. This reduces transmission distance and can increase network capacity.

### 5. Proper Channel Allocation
Channels are assigned carefully to minimize interference between users.

### 6. Filtering
High-quality filters reduce unwanted signals from adjacent channels.

### 7. Adaptive Antennas
Smart/adaptive antennas direct signals toward the desired user and reduce unwanted interference.

---

## Q7. Explain Mobile Originated Call with Proper Diagram.
### (5 Marks)

A **Mobile Originated (MO) call** is a call initiated by the mobile subscriber.

### Flow Diagram

```text
Mobile Station (MS)
        |
        | Call Request
        v
       BTS
        |
        v
       BSC
        |
        v
       MSC
        |
        v
Authentication
        |
        v
Call Setup / Routing
        |
        v
Destination Network
        |
        v
   Called Party
```

### Steps
1. The mobile user dials a number.
2. The MS sends a **call request** to the BTS.
3. BTS forwards the request to the BSC.
4. BSC forwards the request to the MSC.
5. MSC performs authentication and checks subscriber information.
6. MSC establishes the required connection.
7. The call is routed toward the destination.
8. A communication path is established between the two parties.

---

## Q8. Explain Mobile Terminated Call with Proper Diagram.
### (5 Marks)

A **Mobile Terminated (MT) call** is a call received by a mobile subscriber.

### Flow Diagram

```text
Calling Party
      |
      v
PSTN / Network
      |
      v
     MSC
      |
      v
  HLR / VLR
      |
      v
     MSC
      |
      v
     BSC
      |
      v
     BTS
      |
      v
Mobile Station
```

### Steps
1. A caller dials the mobile subscriber's number.
2. The network identifies the subscriber's home network.
3. The HLR provides information about the subscriber.
4. The call is routed toward the serving MSC.
5. The MSC determines the current location of the mobile.
6. Paging is performed in the relevant location area.
7. BTS sends the call information to the mobile.
8. The mobile responds and the call is established.

---

## Q9. Explain Handover with Types and Proper Flow Diagram.
### (5 Marks)

**Handover** is the process of transferring an ongoing call or data connection from one cell/base station to another without disconnecting the user.

### Flow Diagram

```text
Mobile connected to Cell A
          |
          v
Signal strength monitored
          |
          v
Cell A signal becomes weak
          |
          v
Search for target Cell B
          |
          v
Handover decision
          |
          v
Connection transferred
          |
          v
Mobile connected to Cell B
```

### Types of Handover

**1. Hard Handover**
- Old connection is released before the new connection is established.
- Called **break-before-make**.

**2. Soft Handover**
- New connection is established before the old connection is released.
- Called **make-before-break**.

**3. Intra-cell Handover**
- Handover occurs within the same cell, usually between different channels.

**4. Inter-cell Handover**
- Handover occurs from one cell to another.

---

## Q10. Explain Roaming Concept in Mobile Communication.
### (5 Marks)

**Roaming** allows a mobile subscriber to use communication services when they move outside their home network or geographical service area.

### Basic Concept

```text
Home Network
      |
      v
Subscriber travels
      |
      v
Visited Network
      |
      v
Services continue
```

During roaming, the visited network communicates with the subscriber's home network to obtain necessary subscriber and authentication information.

### Functions Involved
- Subscriber authentication
- Location updating
- Call routing
- Service authorization
- Billing information

### Example
An Indian mobile subscriber travelling to another country can use the visited country's network through international roaming if the service is supported.

---

## Q11. Explain the Basic Architecture and Functions of the GPRS Packet Core Network with Reference to SGSN and GGSN.
### (5 Marks)

**GPRS (General Packet Radio Service)** is a packet-switched mobile data service.

### Basic Architecture

```text
Mobile Station
      |
      v
     BTS
      |
      v
     BSC
      |
      v
    SGSN
      |
      v
    GGSN
      |
      v
Internet / External Network
```

### SGSN — Serving GPRS Support Node
The **SGSN** manages packet data services for mobile users within its serving area.

**Functions:**
- Mobility management
- User authentication
- Packet routing
- Session management
- Tracking the location of mobile users
- Delivering packets to and from the mobile device

### GGSN — Gateway GPRS Support Node
The **GGSN** connects the GPRS network to external packet networks such as the Internet.

**Functions:**
- Provides connection to external networks
- Routes packets between GPRS and external networks
- Maintains subscriber session information
- Handles IP address allocation
- Acts as a gateway between the mobile network and external networks

### Difference

| SGSN | GGSN |
|---|---|
| Serving node | Gateway node |
| Manages mobility | Connects to external networks |
| Handles packet routing within GPRS | Routes packets to/from external networks |
| Tracks mobile users | Maintains external network connection |

---

## Q12. Explain 5G Architecture and its Applications.
### (5 Marks)

5G architecture consists mainly of **User Equipment (UE), 5G Radio Access Network (gNB) and 5G Core Network**.

### Architecture

```text
        User Equipment
              |
              v
       5G Radio Access
          Network
            (gNB)
              |
              v
        5G Core Network
              |
       +------+------+
       |             |
       v             v
 Control Plane    User Plane
       |             |
       v             v
 AMF, SMF etc.      UPF
                     |
                     v
             Internet / Services
```

### Major Components

**1. User Equipment (UE)**  
Devices such as smartphones, IoT devices and industrial devices.

**2. gNB**  
The 5G base station that provides radio connectivity to users.

**3. 5G Core Network**  
Manages authentication, mobility, sessions and data forwarding.

Important functions include:
- **AMF:** Access and Mobility Management Function
- **SMF:** Session Management Function
- **UPF:** User Plane Function

### Applications
- High-speed mobile broadband
- Smart cities
- IoT
- Autonomous vehicles
- Remote healthcare
- Industrial automation
- AR and VR
- Smart factories
- Connected vehicles

---

## Q13. Explain IoT Ecosystem.
### (5 Marks)

**IoT (Internet of Things)** is a system in which physical devices are connected to the Internet to collect, exchange and process data.

### IoT Ecosystem

```text
Physical Devices
       |
       v
Sensors / Actuators
       |
       v
Connectivity
       |
       v
IoT Gateway / Network
       |
       v
Cloud / Edge Computing
       |
       v
Data Processing & Analytics
       |
       v
Applications
       |
       v
User
```

### Components

**1. Sensors and Devices**  
Collect data from the physical environment.

Examples: Temperature sensor, motion sensor, camera and GPS.

**2. Connectivity**  
Transfers data between devices and servers.

Examples: Wi-Fi, Bluetooth, 4G/5G, Zigbee and LoRaWAN.

**3. Gateway**  
Connects IoT devices to the network and can process or forward their data.

**4. Cloud / Edge Computing**  
Stores and processes collected data.

**5. Data Processing and Analytics**  
Analyzes collected data and generates useful information.

**6. Applications**  
Present information to users and can control connected devices.

### Applications of IoT
- Smart homes
- Smart cities
- Healthcare monitoring
- Industrial automation
- Smart agriculture
- Connected vehicles

---

# Quick Revision List

| Q.No. | Topic |
|---|---|
| 1 | Reflection, Diffraction and Scattering |
| 2 | Multipath Propagation and Fading |
| 3 | Path Loss vs Shadowing |
| 4 | Noise in Wireless Systems |
| 5 | Co-channel and Adjacent Channel Interference |
| 6 | Interference Mitigation Techniques |
| 7 | Mobile Originated Call |
| 8 | Mobile Terminated Call |
| 9 | Handover |
| 10 | Roaming |
| 11 | GPRS Packet Core — SGSN and GGSN |
| 12 | 5G Architecture and Applications |
| 13 | IoT Ecosystem |
