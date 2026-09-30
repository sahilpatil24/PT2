# WMC PT-II: 5 Mark Solutions (Based on Professor's PPTs)

**Syllabus:** Module 4, Module 5, Module 6 (6.1, 6.2, 6.3)

**PPT references used:** Module 4 (Signal Propagation, Noise and Interference), Module 5 (Cellular Network Component, 5.6 Packet Core Networks), Module 6 (Future Trends)

---

## Q1. Explain the three fundamental propagation mechanisms: Reflection, Diffraction and Scattering.
### (5 Marks)

*Source: Module 4, Signal Propagation PPT*

In free space, radio signals travel in a straight line like light (line-of-sight). In reality there is rarely a LOS path between sender and receiver, because mobile phones are used in big cities with skyscrapers, on mountains, inside buildings and while driving. Because of this, the signal undergoes reflection, diffraction and scattering, which are all strongly frequency dependent.

### 1. Reflection
- Occurs when the object is **large compared to the wavelength** of the signal, e.g. huge buildings, mountains or the surface of the earth.
- The reflected signal is **weaker than the original**, because objects absorb some of the signal power.
- Reflection helps transmission when no LOS exists. This is the standard case in cities and mountain areas.
- A signal may bounce off building walls several times before reaching the receiver. **The more often it is reflected, the weaker it becomes.**

### 2. Diffraction
- Radio waves are **deflected at an edge** of an obstacle and propagate in different directions.
- It allows the signal to reach the region behind an obstacle where there is no direct path.

### 3. Scattering
- Occurs when the size of the obstacle is **of the order of the wavelength or smaller**.
- An incoming signal is **scattered into several weaker outgoing signals**.
- GSM and AMPS wavelengths are of the order of some 10 cm, so many objects in the environment (lamp posts, trees, signs) cause scattering.

**Result:** Scattering and diffraction produce patterns of **varying signal strength depending on the location of the receiver**.

**Remember:** Reflection → Bounce, Diffraction → Bend, Scattering → Spread.

---

## Q2. Explain Multipath Propagation and Fading.
### (5 Marks)

*Source: Module 4, Signal Propagation PPT*

### Multipath Propagation
Multipath propagation occurs when the transmitted signal reaches the receiver through **multiple paths** because of reflection, diffraction and scattering from buildings, trees, vehicles, mountains and other objects. The receiver may receive:

- **Direct signal:** travels straight from transmitter to receiver
- **Reflected signals:** bounce off buildings, ground, vehicles
- **Diffracted signals:** bend around obstacles
- **Scattered signals:** interact with small objects such as foliage or rough surfaces

These copies arrive with **different amplitudes, phases and delays**.

### Fading (Why it occurs)
The received signal is the **combination of all the copies**.

- **In phase:** the copies reinforce each other, `Ar = A1 + A2`, giving a strong signal.
- **Out of phase:** the copies partially or completely cancel, `Ar ≈ A1 − A2`, giving a very weak signal called a **deep fade**.

As the mobile user moves even a small distance, the relative path lengths change, so the received signal fluctuates rapidly even though the transmitter power is constant.

### Parameters of Multipath Fading

| Parameter | Meaning |
|---|---|
| Amplitude variation | Received signal strength changes |
| Phase variation | Phase of received signal changes |
| Time delay | Different paths arrive at different times |
| Delay spread | Difference between arrival times of multipath components |
| Doppler spread | Frequency spreading caused by relative motion |

### Fast Fading and Slow Fading
- **Fast fading:** channel changes rapidly because of high user velocity or significant Doppler shift.
- **Slow fading:** channel changes relatively slowly, often linked to larger-scale changes in the environment.

### Effects of Multipath Fading
- Rapid fluctuations in received signal strength
- Increased Bit Error Rate (BER)
- Phase distortion and delay spread
- Inter-Symbol Interference (ISI)
- Reduced reliability, temporary loss of signal or deep fades (leading to call drops)

**In short:** Multipath = multiple copies of a signal arrive at the receiver. Fading = interference among those copies makes the received signal strength fluctuate.

---

## Q3. What is the difference between Path Loss and Shadowing?
### (5 Marks)

*Source: Module 4, Signal Propagation PPT*

### Path Loss
- Even with a LOS path, or a vacuum with nothing between sender and receiver, the signal still experiences **free space loss**.
- The received power `Pr` is proportional to `1/d²`, where `d` is the distance between sender and receiver. This is the **inverse square law**.
- Cause: the transmitted energy spreads over a larger area as distance increases.

### Shadowing (Blocking)
- An **extreme form of attenuation** caused by **large obstacles** blocking the radio signal.
- The higher the frequency, the more the signal behaves like light, so even small obstacles such as a wall, a truck on the street or trees can block it.
- When there is no LOS, the signal must reach the receiver through indirect paths (NLOS) and suffers higher attenuation and distortion.

### Difference

| Path Loss | Shadowing |
|---|---|
| Loss of signal power with distance | Loss of signal due to blocking by obstacles |
| Follows inverse square law (`Pr ∝ 1/d²`) | Depends on obstacle size, location and frequency |
| Occurs even in free space or vacuum | Occurs only when obstacles block the path |
| Example: moving away from a tower | Example: a building or truck blocks the signal |

**Conclusion:** Path loss is the attenuation due to distance, while shadowing is the extra attenuation caused by obstacles in the path.

---

## Q4. Explain Noise in Wireless Systems. Discuss Thermal Noise and External Noise, their Sources and Impact on Communication Quality.
### (5 Marks)

*Source: Module 4, Noise and Interference PPT*

**Noise** is an unwanted electrical or electromagnetic disturbance that affects the transmitted signal. It reduces communication quality, increases the **Bit Error Rate (BER)** and limits system capacity.

**Noise power:** `N = kTB`

where `N` = noise power (W), `k` = Boltzmann constant (1.38 × 10⁻²³ J/K), `T` = absolute temperature (K), `B` = bandwidth (Hz).

### Classification
- **Internal noise:** thermal, shot, flicker, burst noise
- **External noise:** atmospheric and man-made noise

### 1. Thermal Noise
- Random noise produced by the **thermal motion of electrons** in resistors, amplifiers, antennas and receivers.
- Also called **Johnson or Johnson–Nyquist noise**.
- Power `N = kTB`, so it **increases with temperature and bandwidth**.
- Approximately uniform over a wide frequency range.
- Present **even when no signal is present**.
- Higher temperature → more electron movement → more thermal noise.

### 2. External Noise
Originates outside the equipment.
- **Atmospheric noise:** lightning and storms (natural source)
- **Man-made noise:** electrical equipment such as motors, power lines and vehicle ignition
- **Impulse noise:** short, high-amplitude pulses caused by switching, lightning, etc.
- **Cosmic noise:** radiation from space

### Impact on Communication Quality
At the receiver: **Received signal + Noise**. Thermal noise is especially important in wireless receivers because the received signal can be very weak.

**Noise → signal degradation → lower SNR → higher BER → poorer communication quality.**

Noise makes it difficult for the receiver to distinguish the desired signal from random fluctuations. Higher noise means lower SNR, more errors and poor voice and data quality.

---

## Q5. What is Co-channel Interference and Adjacent Channel Interference? Explain their Causes and Effects.
### (5 Marks)

*Source: Module 4, Noise and Interference PPT*

### 1. Co-channel Interference (CCI)
CCI occurs when **two or more cells use the same frequency channel** and the signals from those cells interfere with each other. It is a major type of interference in cellular systems.

**Cause:** Frequency reuse. The spectrum is divided among cells, and the same frequency is reused in cells that are sufficiently far apart.

**Example:** Cell A uses F1, Cell B uses F2, Cell C uses F1. A mobile near the boundary of Cell A may receive the unwanted F1 signal from Cell C along with its desired F1 signal from Cell A. Since both have the same frequency, the receiver cannot completely separate them.

**Effects:** The interfering signal degrades the desired signal, which reduces call quality and network capacity and increases errors. Signal quality is measured as `S/I = signal power / interfering signal power`.

### 2. Adjacent Channel Interference (ACI)
ACI occurs when a signal from a **nearby frequency channel** interferes with the desired signal, because practical systems cannot completely isolate adjacent channels.

**Example:** Channels at 900, 905 and 910 MHz. A user on 905 MHz can be disturbed by a strong signal on 900 or 910 MHz.

**Causes:**
- Imperfect transmitter and receiver filters
- Strong nearby transmitter on an adjacent channel
- Nonlinearities in transmitters and receivers
- Improper frequency planning (adjacent frequencies without enough separation)

**Effects:** Leakage from neighbouring channels degrades the desired signal, reducing quality and increasing errors.

### Difference

| CCI | ACI |
|---|---|
| Same frequency is used | Nearby frequencies are used |
| Caused by frequency reuse | Caused mainly by imperfect filtering and frequency leakage |
| Depends strongly on cell spacing | Depends on frequency separation and receiver filtering |
| Reduced by increasing reuse distance | Reduced by better filters and proper channel allocation |

---

## Q6. State and Explain the Interference Mitigation Techniques Used in Wireless Communication.
### (5 Marks)

*Source: Module 4, Noise and Interference PPT*

### A. Reducing Co-channel Interference (CCI)

**1. Increase the frequency reuse distance**
Keep co-channel cells far apart, since a larger reuse distance reduces the interfering signal strength. The co-channel reuse ratio is `Q = D/R = √(3N)`, where `D` = reuse distance, `R` = cell radius, `N` = cluster size.

**2. Choose a suitable cluster size (N)**
Increasing `N` increases the distance between co-channel cells, so CCI decreases. The trade-off is fewer channels per cell and lower capacity.

**3. Proper frequency assignment**
Frequencies are allocated so that adjacent cells do not use the same or closely interfering channels, using a reuse pattern designed for the whole network.

**4. Sectoring (directional antennas)**
Directional antennas reduce interference received from other cells.

**5. Power control**
Transmit power is adjusted to the required coverage. Avoiding unnecessarily high power reduces interference to other cells.

**6. Dynamic frequency planning**
Frequencies are assigned dynamically according to traffic and interference conditions. This is useful when traffic varies a lot between cells.

**7. Interference cancellation techniques**

### B. Reducing Adjacent Channel Interference (ACI)

**1. High-quality filters:** sharp RF filters suppress signals outside the desired channel.
**2. Careful channel assignment:** avoid assigning adjacent channels to users who are geographically close.
**3. Guard bands:** a small unused band between channels reduces leakage.
**4. Proper frequency planning** and **5. Power control**, as above.

**In short:** Frequency planning → proper channel allocation → greater co-channel separation → lower interference → better call quality and capacity.

---

## Q7. Explain Mobile Originated Call with Proper Diagram.
### (5 Marks)

*Source: Module 5, Cellular Network Component PPT (GSM)*

A **Mobile Originated (MO) call** is a call initiated by the mobile subscriber.

### Flow Diagram

```text
                       (3,4) security check
                     +--------------------> VLR
                     |                       ^
 MS --(1)--> BSS --(2)--> MSC <--(5-8)-------+  check resources
                     |                          (free circuit)
                     | (9,10) set up call
                     v
                   GMSC ------> PSTN ------> Called party
```

- **1, 2:** connection request
- **3, 4:** security check
- **5 to 8:** check resources (free circuit)
- **9, 10:** set up call

### Steps
1. The MS sends a request to the **BSS** to create a radio channel. The BSS reserves a channel and assigns a frequency and time slot for the MS.
2. The MS confirms that the radio channel is established, and the BSS then creates a connection to the **MSC**.
3. The subscriber is **authenticated** by verifying the number stored in the SIM card, and the connection is set up between the MS and the MSC.
4. The MSC **encrypts** the messages sent to the BTS so that data cannot be read by hackers.
5. Before call setup, the MSC checks the subscriber information (location, preferences, allowed services) in the **VLR**.
6. The MSC requests a **voice channel** between the MSC and the BSS. The call is routed through the **GMSC** to the **PSTN**.
7. When the called party is alerted, the calling MS hears the ringing tone.
8. When the called party answers, the speech path is established.

---

## Q8. Explain Mobile Terminated Call with Proper Diagram.
### (5 Marks)

*Source: Module 5, Cellular Network Component PPT (GSM)*

A **Mobile Terminated (MT) call** is a call received on a mobile device. The network must first locate the network to which the called subscriber is connected and then route the call to the destination MS.

### Flow Diagram

```text
Calling station --(1)--> PSTN --(2)--> GMSC --(3)--> HLR
                                         ^            |  (4,5) request MSRN from VLR
                                         | (6)        v
                                         +---------- VLR
                                         |
                                        (7) forward call
                                         v
                                        MSC <--(8,9)--> VLR   (MS status)
                                         |
                                        (10) paging
                                         v
                                        BSS --(11)--> BTS ==> MS
                                         ^                     |
                                         +-------(12,13)-------+  MS answers
                          (14,15) security checks, (16,17) set up connection
```

### Steps
1. A user dials the phone number of a GSM subscriber.
2. The PSTN forwards the call to the **Gateway MSC (GMSC)**.
3. The GMSC identifies the **HLR** of the subscriber and signals call setup to it.
4. The HLR checks that the number exists and the services subscribed, and requests the **MSRN** from the VLR.
5. The VLR replies to the HLR with the MSRN.
6. The HLR determines the MSC for the MS and forwards this to the GMSC.
7. The GMSC forwards the call setup request to the **current MSC**.
8. and 9. The MSC gets the current status of the MS from the VLR.
10. and 11. The MSC initiates **paging** in all cells, and the BTSs transmit the paging to the MS.
12. and 13. The MS answers.
14. and 15. The VLR performs security checks and signals the MSC to set up the connection.
16. and 17. The MSC sets up the connection, the phone rings and the call is established.

**MSRN** (Mobile Station Roaming Number) is a temporary address generated by the VLR that hides the identity and location of the subscriber and helps the HLR find the subscriber for an incoming call.

---

## Q9. Explain Handover with Types and Proper Flow Diagram.
### (5 Marks)

*Source: Module 5, Cellular Network Component PPT (Handover mechanism in GSM)*

**Handover** is the process of transferring an ongoing call from one cell or channel to another without disconnecting the user.

### Reasons for Handover
- The MS moves out of the range of the BTS, so the received signal level decreases.
- Traffic in one cell is too high, so some MSs are shifted to another cell if possible.

### Handover Decision
The handover is triggered when the receive level of the **BTS_new** becomes better than that of the **BTS_old** by a margin called **HO_MARGIN**. This margin prevents repeated back-and-forth handovers.

### Flow Diagram (Handover Procedure)

```text
MS measures signals and sends measurement report
        |
        v
BSC_old takes HO decision  -->  "HO required" sent to MSC
        |
        v
MSC sends HO request to BSC_new  -->  BTS_new
        |
        v
Resource allocation and channel activation at new BTS
(channel activation ack, HO request ack)
        |
        v
HO command sent (MSC -> BSC_old -> BTS_old -> MS)
        |
        v
MS sends HO access to BTS_new, link established
        |
        v
HO complete  -->  MSC sends clear command to old BSC/BTS
        |
        v
Old resources released (clear complete)
```

### Four Types of Handover in GSM

| Type | Change | Reason |
|---|---|---|
| **1. Intra-cell** | Channel (frequency) changes within the same cell (same BTS) | Narrow-band frequency interference |
| **2. Inter-cell** | BTS changes (same BSC) | Signal strength or traffic |
| **3. Inter-BSC** | BSC changes (same MSC) | Signal strength or traffic |
| **4. Inter-MSC** | MSC changes | Signal strength |

*(Handover is also classified as hard handover, break-before-make, and soft handover, make-before-break, from your notes.)*

---

## Q10. Explain Roaming Concept in Mobile Communication.
### (5 Marks)

*Source: Module 5, Cellular Network Component PPT (HLR, VLR, MSRN, IMSI, TMSI) and Module 5 notes*

**Roaming** allows a mobile subscriber to use mobile services (voice, SMS, data) when moving outside the coverage area of the home network, through a visited network.

### How Roaming Works in GSM (HLR and VLR)
- **HLR (Home Location Register):** database in the home network storing subscriber information, current location, services and authentication details. It supports call routing, roaming and handovers.
- **VLR (Visitor Location Register):** a **temporary database** that stores subscriber information while the subscriber roams outside the home network's coverage area. It works with the HLR to enable roaming and seamless service.

```text
Home Network                         Visited Network
+--------+                           +---------+
|  HLR   |<---- subscriber info ---->|   VLR   |
+--------+   location update / auth  +---------+
                                          |
                                         MSC --- BSS --- Roaming MS
```

### Steps
1. The MS enters a visited network and registers there (location update).
2. The visited **VLR** identifies the subscriber by **IMSI/TMSI** and obtains subscriber data and authentication information from the **HLR**.
3. The subscriber is authenticated and services are authorized.
4. The HLR stores the current VLR/MSC of the subscriber. For an incoming call the HLR asks the VLR for an **MSRN**, and the call is routed to the visited MSC.
5. The visited network provides service, records usage, and the home network bills the subscriber.

### Types
- **National roaming:** another operator's network within the same country.
- **International roaming:** a network in another country, e.g. an Indian subscriber abroad.

**Identities used:** IMSI (permanent identity), TMSI (temporary identity, valid within the VLR location area) and MSRN (temporary roaming number).

---

## Q11. Explain the Basic Architecture and Functions of the GPRS Packet Core Network with Reference to SGSN and GGSN.
### (5 Marks)

*Source: Module 5, 5.6 Packet Core Networks PPT*

**GPRS (General Packet Radio Service)** is a packet-switched data service (2.5G) that reuses the existing GSM infrastructure. It was introduced because standard GSM data rate (9.6 kbit/s) is not enough for web browsing, file download and e-mail. GPRS gives bit rates from about 9 to 150 kbps per user, and 1 to 8 time slots can be allocated to a user.

### Architecture

```text
            SGSN (to HLR/GR, MSC/VLR)
             |
MS --Um-- BSS(BTS+BSC+PCU) --Gb-- SGSN ==Gn== GGSN --Gi-- PDN (Internet)
                                     \___ IP-based GPRS backbone ___/
```

- The existing GSM **MS, BSS, MSC/VLR and HLR** are modified for GPRS.
- Each BSC needs a **Packet Control Unit (PCU)**. At the BSC output, voice goes to the MSC and data goes to the SGSN.
- **Two new nodes** (both are routers) are introduced: **SGSN** and **GGSN**.
- The **internal backbone** is an IP network between the GSNs. **Tunneling (GTP)** is used between SGSN and GGSN.

### SGSN (Serving GPRS Support Node)
The GPRS equivalent of the MSC. It delivers data packets to and from mobile stations in its service area.

**Functions:**
- Authentication of GPRS mobiles
- Registration of mobiles in the network
- Mobility management
- Collecting charging information for use of the air interface

### GGSN (Gateway GPRS Support Node)
The interworking unit between the GPRS network and external packet data networks (PDN).

**Functions:**
- Routing information for GPRS users
- Address conversion (PDP format to GSM packet and back)
- Stores the current SGSN address and profile of the user in its location register

### Difference

| SGSN | GGSN |
|---|---|
| Serving node, equivalent to MSC | Gateway node to external PDN |
| Authentication, registration, mobility management | Routing, address conversion, interworking |
| Delivers packets to and from MS in its area | Connects GPRS to Internet and other packet networks |
| Collects air interface charging information | Stores SGSN address and user profile |

**Key benefits of GPRS:** higher speed (packet switching), always-on connectivity, billing per megabyte instead of connection time, and it can be deployed with mostly software upgrades so voice and data work at the same time.

---

## Q12. Explain 5G Architecture and its Applications.
### (5 Marks)

*Source: Module 6, Future Trends PPT (6.1 and 6.2)*

The 5G core network is implemented as **software**, which removes dedicated hardware, improves performance and allows new functions and services to be introduced and upgraded quickly.

### Architecture

```text
                        +---------------- 5G Core Network ----------------+
                        |   UDM    AUSF    NRF    SEPP                    |
                        |                                                 |
 5G UEs --> gNB --N2--> |   AMF -----N11----- SMF                         |
              |         |                      |                          |
              |         |                     N4                          |
              +---N3--> |                     UPF ---N6---> Internet      |
                        +-------------------------------------------------+
```

### Components of the 5G Core
- **AMF (Access and Mobility Management Function):** mobility management, signalling connection with the UE, UE registration, and authentication towards AUSF.
- **SMF (Session Management Function):** controls data sessions. AMF and SMF together are roughly equivalent to the 4G MME.
- **UPF (User Plane Function):** handles user plane data under SMF control, including traffic monitoring and charging. Roughly equivalent to 4G SGW and PGW.
- **UDM (Unified Data Management):** stores subscriber data and location.
- **AUSF (Authentication Server Function):** subscriber authentication, normally based on SIM.
- **NRF (Network Repository Function):** registration and discovery of other network functions.
- **SEPP (Security Edge Protection Proxy):** secures signalling between networks (roaming) over the N32 interface.

### Benefits of the 5G Core
Lower cost, easy development of new functions, software updates, improved network capability, more connections and more secure connectivity.

### Applications
**Smart cities:**
- Smart traffic management
- Smart parking
- Smart street lighting
- Smart surveillance
- Smart waste management
- Smart grids and energy
- Environmental monitoring
- Public safety
- Smart healthcare

**Autonomous systems:**
- Autonomous vehicles
- Connected vehicles (V2V, V2I, V2P)
- Autonomous drones
- Industrial robots
- Autonomous public transport
- Remote operations

| 5G Capability | Application Benefit |
|---|---|
| Low latency | Fast response for autonomous vehicles and critical systems |
| High data rate | Real-time video and sensor-data transmission |
| Massive connectivity | Connects thousands of IoT devices |
| High reliability | Safety-critical applications |
| Network slicing | Dedicated network resources for different services |
| Edge computing | Processes data close to devices for faster decisions |

---

## Q13. Explain IoT Ecosystem.
### (5 Marks)

*Source: Module 6, Future Trends PPT (6.3) and Module 5 PPT (IoT devices and gateway)*

The **Internet of Things (IoT)** is a network of physical objects equipped with sensors, communication technologies, processing capabilities and software that enable them to collect, exchange and process data over a network.

### IoT Ecosystem

```text
IoT Devices and Sensors
          |
          v
Connectivity Infrastructure
(4G/5G, LoRa, NB-IoT, Sigfox, Wi-Fi, Bluetooth, satellite)
          |
          v
IoT Connectivity Management Platform (CMP)
          |
          v
Cloud and Edge Processing
          |
          v
AI and Analytics Layer
          |
          v
Applications and Interfaces --> User
```

### Six Components
1. **IoT devices and sensors:** hardware endpoints with sensors, actuators and microcontrollers that collect and transmit data, e.g. smart meters, industrial machines, wearables, autonomous vehicles. An **IoT gateway** acts as a bridge between devices and the network (protocol translation, data aggregation and filtering, security, local processing).
2. **Connectivity infrastructure:** the network layer enabling device communication using cellular (4G/5G), LPWAN (LoRa, NB-IoT, Sigfox), Wi-Fi, Bluetooth or satellite.
3. **Connectivity Management Platform (CMP):** orchestrates connectivity, provisioning, diagnostics and security across millions of endpoints, often across multiple carriers.
4. **Cloud and edge processing:** data is processed in the cloud or at the edge to reduce latency and enable real-time analytics and automated responses.
5. **AI and analytics layer:** machine learning turns raw data into insights such as predictive maintenance, dynamic pricing and anomaly detection.
6. **Applications and interfaces:** dashboards, APIs and control systems to visualize data, manage assets and automate workflows.

### Features of a Well-Architected IoT Ecosystem
- **Scalability:** thousands to millions of devices
- **Interoperability:** integration across different devices, networks and platforms
- **Security and compliance:** secure onboarding, encryption and identity management
- **Automation and intelligence:** cost savings through AI-driven automation

### Applications
Smart homes, smart cities, healthcare monitoring (wearables), industrial automation, smart agriculture and connected vehicles.

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
| 11 | GPRS Packet Core: SGSN and GGSN |
| 12 | 5G Architecture and Applications |
| 13 | IoT Ecosystem |
