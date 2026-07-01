# 🚗 Smart Parking System using Verilog HDL

A **4-Slot Smart Parking System** designed using **Verilog HDL** and simulated on **EDA Playground**. The project demonstrates digital system design concepts such as Finite State Machines (FSM), slot allocation, occupancy management, parking time tracking, and parking fee calculation.

---

## 📖 Overview

This project automates the operation of a small parking lot with four parking slots. It detects vehicle entry and exit, allocates available parking slots, tracks parking duration, calculates parking fees, and controls entry and exit gates.

The entire design follows a **modular architecture**, making it easy to understand, test, and extend.

The project was developed and simulated using **EDA Playground** with **Icarus Verilog** and **EPWave**.

---

## ✨ Features

- Supports **4 parking slots**
- Automatic slot allocation
- Vehicle entry and exit management
- Parking occupancy tracking
- Parking full indication
- Individual timer for each parking slot
- Parking fee calculation
- Payment verification before vehicle exit
- Modular Verilog design
- Multiple testbenches covering different scenarios

---

# 📂 Project Structure

```
Smart-Parking-System/
│
├── top_parking_system_4slot.v      # Top-level module
├── fsm_parking.v                   # Finite State Machine
├── slot_manager_4slot.v            # Slot allocation logic
├── time_billing_4slot.v            # Timer and billing logic
│
├── testbench/
│   ├── tb_parking.v
│   ├── tb_entry_when_full.v
│   ├── tb_fallback_exit.v
│   ├── tb_parking_full_cycle.v
│   └── tb_parking_timer_restart.v
│
└── README.md
```

---

# 🏗 System Architecture

```
                   +---------------------+
                   | Vehicle Entry/Exit  |
                   +----------+----------+
                              |
                              v
                    +------------------+
                    |   FSM Controller |
                    +------------------+
                       |      |      |
          +------------+      |      +-------------+
          |                   |                    |
          v                   v                    v
+----------------+   +----------------+   +----------------+
| Slot Manager   |   | Time & Billing |   | Gate Control   |
+----------------+   +----------------+   +----------------+
          |                   |
          +---------+---------+
                    |
                    v
           Parking Slot Status
```

---

# 📁 Module Description

## 1. top_parking_system_4slot.v

This is the **top-level module**.

It integrates:

- FSM Controller
- Slot Manager
- Time Billing Module

Responsibilities:

- Connects all modules
- Handles system inputs and outputs
- Coordinates complete parking operation

---

## 2. fsm_parking.v

Implements the **Finite State Machine (FSM)** that controls parking operations.

Functions:

- Vehicle entry
- Slot allocation request
- Entry gate control
- Exit request handling
- Payment verification
- Exit gate control
- Parking full detection

Typical FSM States:

- IDLE
- Allocate Slot
- Entry Gate Open
- Parking
- Exit Request
- Wait for Payment
- Exit Gate Open

---

## 3. slot_manager_4slot.v

Responsible for managing parking slots.

Functions:

- Detects available parking slot
- Allocates first free slot
- Frees slot after vehicle exit
- Updates occupancy information
- Calculates number of free slots

---

## 4. time_billing_4slot.v

Tracks parking duration for every occupied slot.

Functions:

- Starts timer when vehicle enters
- Stops timer on exit
- Resets timer after slot becomes free
- Calculates parking fee

Formula used:

```
Parking Fee = Parking Time × Rate
```

(Default rate can be modified inside the module.)

---

# 🔌 Inputs

| Signal | Description |
|---------|-------------|
| clk | System clock |
| rst | System reset |
| entry_pulse | Vehicle entry request |
| exit_pulse_for_system | Vehicle exit request |
| payment_received | Payment confirmation |
| exit_car_select | Slot selected for exit |

---

# 📤 Outputs

| Signal | Description |
|---------|-------------|
| entry_gate | Opens entry gate |
| exit_gate | Opens exit gate |
| occupancy | Parking occupancy status |
| free_count | Number of free parking slots |
| full_led | Parking full indicator |
| fee_ready | Fee calculation completed |
| fee | Parking fee |
| e0, e1, e2, e3 | Parking time of each slot |

---

# ▶ Simulation

The project was developed and tested using **EDA Playground**.

### Simulator

- Icarus Verilog

### Waveform Viewer

- EPWave

### Simulation Steps

1. Upload all source files.
2. Upload the desired testbench.
3. Select **Icarus Verilog** as the simulator.
4. Run the simulation.
5. Open **EPWave** to observe waveforms.

---

# 🧪 Testbenches

The project contains dedicated testbenches for different scenarios.

### tb_parking.v

- Basic functionality verification
- Entry and exit operation

---

### tb_entry_when_full.v

- Parking full condition
- Rejects additional vehicles

---

### tb_fallback_exit.v

- Vehicle exit
- Slot release verification

---

### tb_parking_full_cycle.v

Complete parking cycle:

- Entry
- Slot allocation
- Parking timer
- Fee generation
- Payment
- Exit

---

### tb_parking_timer_restart.v

Checks:

- Timer reset
- Timer restart
- Accurate parking duration

---

# ⚙ Working Flow

```
Reset
   │
   ▼
Vehicle Entry
   │
   ▼
Check Free Slot
   │
   ├── No
   │      │
   │      ▼
   │   FULL LED ON
   │
   └── Yes
          │
          ▼
Allocate Slot
          │
          ▼
Open Entry Gate
          │
          ▼
Start Timer
          │
          ▼
Vehicle Exit Request
          │
          ▼
Calculate Fee
          │
          ▼
Payment Received
          │
          ▼
Open Exit Gate
          │
          ▼
Free Slot
          │
          ▼
Return to IDLE
```

---

# 💻 Technologies Used

- Verilog HDL
- EDA Playground
- Icarus Verilog
- EPWave

---

# 🚀 Future Enhancements

- Support for more parking slots
- RFID-based vehicle identification
- FPGA implementation
- LCD/OLED display
- Dynamic pricing
- Mobile application integration
- Real-time parking monitoring

---

# 🎯 Learning Outcomes

This project demonstrates:

- Finite State Machine (FSM) design
- Modular Verilog programming
- Digital system design
- Timer implementation
- Resource allocation
- Testbench development
- Simulation and waveform analysis using EDA Playground

---

# 👩‍💻 Author

**Shreya Revanakar**

Electronics and Communication Engineering Student

---

# 📜 License

This project is intended for **educational and academic purposes**.

Feel free to use and modify it for learning.
