# B2-Sensor-Based-Street-Light
Initial commit - B3 Sensor Based Street Light Diploma Project

# B-3 Sensor Based Street Lights

An embedded systems project that automatically controls street lighting based on ambient light conditions using an **AT89S52 microcontroller** and a **B-3/LDR-based sensor system**.

The project was developed as a Diploma academic project in the Department of Electronics & Communication Engineering at **Bomma Institute of Technology and Science, Allipuram, Khammam**.

---

## 📌 Project Overview

The **B-3 Sensor Based Street Light** system is designed to reduce unnecessary power consumption by automatically switching street lights according to environmental lighting conditions.

The system detects ambient light using a B-3/LDR-based sensor. When darkness is detected, the microcontroller activates the street light. When sufficient ambient light is available, the street light is switched OFF.

The project can be used as a prototype for smart and energy-efficient street-lighting systems.

---

## 🎯 Objectives

* Automatically control street lights based on ambient light.
* Reduce unnecessary electricity consumption.
* Eliminate the need for manual switching.
* Improve street-lighting efficiency.
* Demonstrate embedded-C programming with an 8051-family microcontroller.
* Design and simulate the system using electronic design software.

The project report highlights automatic operation, energy savings, cost reduction and sustainability as key benefits.

---

## ⚙️ Working Principle

The system continuously monitors the sensor connected to the microcontroller.

```text
             Ambient Light
                  │
                  ▼
          ┌───────────────┐
          │ B-3 / LDR     │
          │    Sensor     │
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │   AT89S52     │
          │ Microcontroller│
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │ Driver/Relay  │
          │   ULN2003     │
          └───────┬───────┘
                  │
                  ▼
          ┌───────────────┐
          │ LED Street    │
          │     Light     │
          └───────────────┘
```

### Control Logic

| Sensor Condition    | AT89S52 Input | Street Light |
| ------------------- | ------------: | ------------ |
| Darkness detected   |           LOW | ON           |
| Brightness detected |          HIGH | OFF          |

The B-3 sensor is connected to **P1.0**, while the street-light control output is connected to **P2.0**.

---

## 🔌 Hardware Components

The project uses the following major components:

* **AT89S52 Microcontroller**
* **B-3 Sensor / LDR**
* **PIR Sensor**
* **LCD Display**
* **ULN2003 Driver**
* **LED Street Lights**
* **Relay Module**
* **BC547 Transistor**
* **7805 Voltage Regulator**
* Resistors and capacitors
* Regulated power supply

The project report specifically covers the AT89S52, power supply, LCD, PIR sensor, LDR, ULN2003 and LED street lights.

---

## 🧠 Microcontroller

### AT89S52

The AT89S52 is an 8-bit 8051-family microcontroller used as the main controller of the project.

Important features include:

* 8 KB Flash memory
* 256 bytes internal RAM
* 32 programmable I/O lines
* Three 16-bit timer/counters
* UART serial communication
* Interrupt support
* Watchdog timer
* Power-saving modes

---

## 💡 Sensors

### LDR

The **Light Dependent Resistor (LDR)** changes its resistance according to the intensity of incident light.

* Bright light → lower resistance
* Darkness → higher resistance

This property allows the system to detect day/night conditions.

### PIR Sensor

The PIR sensor is used for detecting motion. It detects changes in infrared radiation caused by moving objects such as people or animals.

---

## 🔧 Circuit Operation

The microcontroller operates from a regulated **5 V supply**.

The sensor section provides a digital signal to **P1.0**. The AT89S52 processes this input and generates the control signal on **P2.0**.

The output can drive a transistor/relay arrangement for controlling the street light.

### Logic

```text
START
  │
  ▼
Power ON
  │
  ▼
Read Sensor at P1.0
  │
  ├── LOW ──► Darkness ──► P2.0 HIGH ──► Light ON
  │
  └── HIGH ─► Brightness ─► P2.0 LOW ──► Light OFF
  │
  ▼
Repeat Continuously
```

---

## 💻 Software

The controller program is written in **Embedded C** for the AT89S52 and compiled using the **Keil C51 compiler**.

### Basic Control Code

```c
#include <reg51.h>

sbit sensor = P1^0;
sbit light  = P2^0;

void delay(unsigned int time)
{
    unsigned int i, j;

    for (i = 0; i < time; i++)
        for (j = 0; j < 1275; j++);
}

void main()
{
    while (1)
    {
        if (sensor == 0)
        {
            light = 1;
        }
        else
        {
            light = 0;
        }

        delay(500);
    }
}
```

The source report specifies the same basic control logic: a LOW sensor signal represents darkness and turns the street light ON, while a HIGH signal turns it OFF.

---

## 🖥️ Development & Simulation Tools

### Keil µVision

Used for:

* Writing Embedded C code
* Compiling the AT89S52 program
* Generating the microcontroller program output
* Debugging/development

The project report describes the use of the **Keil C51 compiler** and µVision development environment.

### Proteus

Used for:

* Circuit design
* Microcontroller simulation
* Sensor testing
* LED/street-light simulation
* Observing system operation

The project report contains a dedicated section for **Proteus Design** and circuit simulation.

---


## 🧪 Expected Output

### Daytime

```text
Sensor = HIGH
       ↓
Brightness detected
       ↓
P2.0 = LOW
       ↓
Street Light = OFF
```

### Nighttime

```text
Sensor = LOW
       ↓
Darkness detected
       ↓
P2.0 = HIGH
       ↓
Street Light = ON
```

The report describes this automatic ON/OFF operation based on ambient light conditions.

---

## 🚀 Future Enhancements

The project can be further improved by adding:

* PWM-based brightness control
* Real-Time Clock (RTC)
* Solar-powered operation
* IoT-based remote monitoring
* Improved sensor calibration
* Automatic brightness adjustment
* Energy-consumption monitoring

PWM dimming, an RTC and improved sensing are specifically suggested as possible enhancements in the project report.

---

## 🌱 Applications

Potential applications include:

* Urban roads
* Rural roads
* Highways
* Pedestrian pathways
* Parks
* Parking areas
* Industrial areas
* Commercial areas
* Educational campuses

The report identifies these types of environments as applications for sensor-controlled LED street lighting.

---

## ⭐ Key Advantages

* Automatic operation
* Reduced power consumption
* Reduced manual intervention
* Low-cost implementation
* Energy-efficient lighting
* Expandable architecture
* Suitable for smart-lighting applications

---

## 👨‍💻 Project Team

**Diploma in Electronics & Communication Engineering**

* I. Narasimha — 22239-EC-041
* D. Mahendar — 22239-EC-021
* Y. Abhishek — 22239-EC-034
* B. Pavani — 22239-EC-048
* SK. Shahin — 22239-EC-013

**Guide:** Mr. C. Purnaprakash, M.Tech

**Institution:**
Bomma Institute of Technology and Science
Allipuram, Khammam, Telangana

The project report lists the above project team, guide and institution.

---

## 📜 Project Type

**Academic Diploma Major Project**

**Domain:** Embedded Systems / Electronics

**Controller:** AT89S52

**Programming Language:** Embedded C

**Simulation:** Proteus

**IDE/Compiler:** Keil µVision / C51

---

## 📌 Project Status

**Completed Academic Project**

This repository contains the source code, circuit/simulation files, documentation and output images related to the B-3 Sensor Based Street Light project.
