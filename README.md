# Temperature Controlled Fan Using Op-Amp Comparator

Automatic DC fan control circuit using an op-amp configured as a comparator and a 10 kΩ NTC thermistor (β = 3950). The fan switches at a designed threshold of approximately 38°C for efficient thermal management.

---

## 📌 Overview

This project demonstrates a temperature-controlled fan circuit where the fan automatically turns ON when the ambient temperature exceeds a preset threshold and turns OFF when it falls below it. The circuit is modeled and verified using LTspice to study analog temperature sensing, comparison, and switching behavior.

---

## 🎯 Objectives

- Sense ambient temperature using an NTC thermistor in a voltage divider configuration.  
- Generate a stable reference voltage using a resistor divider network.  
- Compare the sensed temperature voltage with the reference using an op-amp comparator.  
- Drive a 12 V DC fan using a transistor switch controlled by the comparator output.  
- Validate threshold behavior and switching point through LTspice simulation.

---

## 🧩 Components

- **Operational Amplifier (U1):** Used as a voltage comparator with single 12 V supply.  
- **NTC Thermistor (10 kΩ, β = 3950):** Temperature sensor forming a divider with R1 = 4.7 kΩ to produce a temperature-dependent voltage.  
- **Reference Network:** R2 = 8 kΩ, R3 = 10 kΩ creating a fixed reference voltage of about 6.67 V for the comparator input.  
- **NPN Transistor (2N2222, Q1):** Low-side switch that drives the 12 V DC fan when driven into saturation.  
- **Flyback Diode (1N4007, D1):** Connected across the fan to clamp inductive voltage spikes when the transistor turns OFF.  
- **12 V DC Fan and Supply:** Fan modeled as a resistive/inductive load powered from a 12 V source.

---

## ⚙️ Working Principle

1. The thermistor and resistor R1 form a voltage divider whose output voltage V_temp varies with temperature.  
2. The R2–R3 divider generates a constant reference voltage V_ref ≈ 6.67 V applied to the other comparator input.  
3. At lower temperatures, V_temp remains below V_ref, so the op-amp output is LOW, the 2N2222 is OFF, and the fan does not run.  
4. As temperature rises, the thermistor resistance changes so that V_temp crosses V_ref near the design threshold of about 38°C, forcing the op-amp output HIGH.  
5. The HIGH output drives base current through R4, saturating Q1 and powering the fan; the 1N4007 diode protects the transistor from back‑EMF.  

---

## 🧪 Simulation Details

- Tool: LTspice for schematic capture and simulation.  
- Supply Voltage: 12 V DC.  
- Temperature Range: Simulated over approximately 20°C–80°C using a parameter sweep on the thermistor model.  
- Analysis Type: DC sweep or stepped temperature analysis to observe comparator output versus temperature.  
- Key Observation: The op-amp output exhibits a sharp transition from 0 V to 12 V near the 38°C point, confirming correct comparator action and clean switching.

---

## 📊 Results and Discussion

- The fan remains OFF for temperatures below the design threshold, minimizing unnecessary power consumption.  
- Above the threshold, the fan turns ON quickly, providing immediate cooling and preventing overheating of connected equipment.  
- Demand-based operation improves energy efficiency, with significant reduction in average power compared to a continuously running fan in typical ambient conditions.

---

## ✅ Features

- Purely analog control; no microcontroller is required.  
- Simple, low-cost component set using standard devices.  
- Fast response due to direct comparator-to-transistor drive.  
- Scalable concept that can be adapted to different threshold temperatures by adjusting divider values or thermistor parameters.

---

## 🔧 Future Improvements

- Introduce hysteresis via positive feedback around the comparator to avoid rapid ON/OFF toggling near the threshold.  
- Add PWM-based fan speed control using a microcontroller while retaining the thermistor sensing front-end.  
- Build and test a hardware prototype, including PCB design and real-world thermal measurements.

---

## 📚 References

- Sedra & Smith, *Microelectronic Circuits*.  
- LTspice official documentation.  
- Datasheets for 2N2222 transistor, 1N4007 diode, and 10 kΩ NTC thermistor (β = 3950).
