# 🥤 Drink Dispensing Machine – VHDL Project

A digital system design project implemented on the BASYS 3 FPGA board, simulating an automated drink dispenser with programmable recipes, resource validation, and timed execution.

## 📋 Project Overview

This system models a drink vending machine with:
- **5 liquid compartments** (measured in ml)
- **1 ice compartment** and **1 sugar compartment** (measured in cubes)
- **2 programmable actions**: mixing and heating (measured in seconds)

The machine supports:
- **1 hardcoded recipe**
- **7 user-defined recipes**, entered via switches and buttons
- **Real-time validation** of available resources
- **LED and 7-segment display feedback** for status, errors, and countdowns

## 🧠 Architecture

### 🔲 Top-Level Design
The system is modular, with a clear separation between control logic and execution logic.

### 🕹️ Control Unit (CU)
Handles:
- User input (buttons, switches)
- Program selection
- Validation logic
- LED signaling

### ⚙️ Execution Unit (EU)
Manages:
- Dispensing liquids, sugar, and ice
- Executing mixing/heating actions
- Countdown timers and display updates

## 🧱 Hardware Modules

| Module            | Function                                                                 |
|-------------------|--------------------------------------------------------------------------|
| `RAM_PROG`        | Stores desired quantities per program and component                      |
| `RAM_CAP`         | Stores current available stock of each ingredient                        |
| `TIME_CALC`       | Converts quantities to execution time (10ml → 500ms, 1 cube → 1s)        |
| `PREPARE_TIMER`   | Countdown timer for total execution time                                 |
| `CLOCK_DIVIDER`   | Generates 100ms and display clocks from 100MHz board clock               |
| `COUNTER_COMP`    | Iterates through components/actions during recipe setup                  |
| `COUNTER_PG`      | Tracks selected program                                                  |
| `SSD`, `CAT`, `AN`| Drives 7-segment display for time and status                             |

## 🧪 Example Recipe: Cappuccino

| Component      | Quantity       |
|----------------|----------------|
| Water          | 0 ml           |
| Coffee         | 100 ml         |
| Milk           | 100 ml         |
| Vegan Milk     | 0 ml           |
| Matcha         | 0 ml           |
| Ice            | 0 cubes        |
| Sugar          | 2 cubes        |
| Heating        | 8 seconds      |
| Mixing         | 5 seconds      |

## 🖥️ Interaction via BASYS 3

### 🔧 Setup
- Use switches to input quantities per compartment
- Press central button to confirm and move to next component
- LEDs indicate current program, selected compartment, and errors

### 🧃 Execution
- Select a recipe using switches
- System checks resource availability
- Countdown begins on 7-segment display
- Drink is prepared step-by-step with visual feedback

## 🚀 Future Improvements
- Add increment/decrement buttons for easier quantity input
- Replace 7-segment display with LCD for full-text feedback
- Integrate sensors to monitor real-time liquid levels


