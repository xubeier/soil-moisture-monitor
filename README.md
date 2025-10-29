# Smart Plant Soil Moisture Monitor (micro:bit Project)

This project is a simple prototype that detects soil moisture using a BBC micro:bit and two metal nails as improvised soil probes. It displays a happy face when the soil is wet and a sad face when the soil is dry. The prototype is designed as a low-cost solution to help beginner programmers and plant owners monitor soil moisture.

## Project Description

This project is a simple soil moisture monitoring system built using a BBC micro:bit. It was designed to solve a real problem: my grandmother often forgot to water her plants, and some of them dried out. To help her, I built a low-cost moisture reminder system.

Instead of using an expensive moisture sensor, two iron nails are used as simple soil probes. The moisture level is measured using analog voltage changes on pin P0. When the soil becomes dry, the micro:bit shows a 😢 icon to remind that watering is needed. When the soil is wet, a 😊 icon is displayed.

The system runs on two AAA batteries, so it is easy to place in small indoor flower pots. It is affordable, simple to assemble, and suitable for beginner-level physical computing.

## Features
- Detects soil moisture using analog input
- Simple visual feedback using micro:bit LED icons
- Low-cost design using iron nails as probes
- Portable: powered by 2 × AAA battery pack
- Customizable moisture threshold
- Improved power efficiency using low-frequency sampling
  
## Materials

| Item | Quantity | Description |
|------|----------|-------------|
| BBC micro:bit V2 | 1 | Main microcontroller board |
| Battery pack (2 × AAA) | 1 | Power supply |
| USB cable | 1 | Used for programming |
| Iron nails (12 cm) | 2 | Used as soil probes |
| Crocodile clip wires | 2 | Connection wires |
| Pot with dry soil | 1 | For testing dry condition |
| Pot with wet soil | 1 | For testing wet condition |

## Wiring

Two iron nails are used as soil probes. They are inserted into the soil with a small distance between them . Crocodile clips are used to connect the nails to the micro:bit.

| micro:bit Pin | Connection |
|---------------|------------|
| P0 | Nail probe 1 |
| 3V | Nail probe 2 |
| GND | Not used |
| P1/P2 | Not used |

This setup measures how well electricity passes through the soil. Wet soil conducts better than dry soil, so the voltage detected on P0 changes with moisture.

---
## How It Works

This project estimates soil moisture using the electrical conductivity method. Two iron nails are used as probes and inserted into the soil with a small gap between them. When the soil contains water, it also contains dissolved ions that allow electricity to pass through it. Wet soil therefore conducts electricity better than dry soil, which has higher resistance.

In this prototype, the 3V pin provides a small voltage** to the soil and pin P0 measures the voltage that returns through the soil. The moisture level is detected as an analog value between 0 and 1023. A lower reading means low conductivity (dry soil), while a higher reading indicates high conductivity (wet soil).

The analog reading from pin `P0` ranges from **0 to 1023**. A threshold of **500** was chosen as an initial midpoint reference to separate dry and wet soil conditions during prototyping. This value can be adjusted later through calibration.

## Program Logic

The program continuously measures the moisture level from pin P0 and compares it to a threshold. The logic is:

1. Read the moisture value using `analog read pin P0`
2. Compare the value with a threshold of 500
3. If the value is lower or equal to 500 → the soil is dry → show 😭
4. If the value is higher than 500 → the soil is wet → show 😊
5. Wait before the next measurement to save battery power

The value from P0 is stored in a variable called `moisture`. A delay is added using `pause(7200000)` so the device checks the soil every 2 hours instead of constantly. This reduces battery use.

Start
  ↓
Read P0 moisture
  ↓
Is value ≤ 500?
       ↙        ↘
   Yes           No
 (Sad face)   (Happy face)
  ↓              ↓
 Wait 2 hours → loop




