# Experiment 18: Quadrature Phase Shift Keying (QPSK)

## I. Objectives

The objectives of this experiment are:

- To understand the fundamental concept of **Quadrature Phase Shift Keying (QPSK)** as a digital modulation technique.
- To observe how a serial digital data stream can be divided into **two parallel bit streams** for transmission.
- To generate two **Binary Phase Shift Keying (BPSK)** signals and combine them to form a **QPSK-modulated signal**.
- To examine the characteristics of the QPSK waveform using an **oscilloscope**.
- To explore how **phase discrimination techniques** can be used to recover one of the component BPSK signals.
- To study the **phase relationship** between the local carrier signal and the transmitted carrier signals in a QPSK communication system.

Quadrature Phase Shift Keying (QPSK) is a digital modulation method that allows the transmission of **two bits of information per symbol** by shifting the phase of a carrier signal among **four distinct phase states: 0°, 90°, 180°, and 270°**.

---

## II. Materials and Components Used

The following equipment and components were used in this experiment:

- **Emona Telecoms-Trainer 101** with power supply
- **Dual-channel 20 MHz Oscilloscope**
- **Three Emona Telecoms-Trainer 101 oscilloscope probes**
- **Assorted Emona Telecoms-Trainer 101 patch leads**

These devices were used to generate, monitor, and analyze the **QPSK signal and its individual components**.

---

## III. Procedure

### Part A – Generation of a QPSK Signal
![FIGURE 4 (5)](https://github.com/user-attachments/assets/3cec754b-f6d3-45de-9e80-3279a23dc025)

1. Gather all required equipment listed in the materials section.
2. Configure the oscilloscope according to the standard setup used in previous experiments.
3. Use the **Sequence Generator module** to produce a digital data stream.
4. Connect the output of the Sequence Generator to the **Serial-to-Parallel (S/P) Converter module**.
5. The S/P converter separates the serial data into two parallel streams:
   - **Odd bits**
   - **Even bits**
6. Connect the outputs of the S/P converter to two separate **Multiplier modules**.
7. Use the **Master Signals module** to generate a **100 kHz sinewave carrier**.
8. Apply the carrier signal to both multiplier modules.
9. Each multiplier produces a **BPSK-modulated signal**, referred to as:
   - **PSK₁**
   - **PSK₂**
10. Observe the signals using the oscilloscope.

---

### Part B – Formation of the QPSK Signal
![FIGURE 6 (3)](https://github.com/user-attachments/assets/e874f967-c765-4ef4-8040-cc59adf73329)

1. Connect the outputs of the two multiplier modules to the **Adder module**.
2. Adjust the **Adder Gain control** until the output signal reaches approximately **4 V peak-to-peak**.
3. Observe the output of the Adder module on the oscilloscope.
4. Compare the resulting waveform with the individual BPSK signals.

The Adder module combines the two BPSK-modulated signals to produce the **QPSK signal**.

---

### Part C – Recovering One Component Using Phase Discrimination
![Uploading FIGURE 14.jpg…]()

1. Modify the circuit to include a **Phase Shifter module**.
2. Connect the phase shifter to the **local carrier signal**.
3. Adjust the **Phase Adjust control** while observing the demodulated signal.
4. Use a **Tunable Low-Pass Filter (LPF)** to filter the output of the product detector.
5. Monitor the output waveform on the oscilloscope while adjusting the phase.
6. Through proper phase alignment, the demodulator can recover **one of the BPSK signals** that form the QPSK signal.

---

## IV. Results and Discussion

### Part A – Digital Data Modeling

The **Sequence Generator module** produced a serial digital data stream that was converted into two parallel bit streams using the **Serial-to-Parallel converter**. One stream contained the **odd-numbered bits**, while the other carried the **even-numbered bits**.

#### Question 1  
**What is the relationship between the bit rate of the two digital signals and the bit rate of the Sequence Generator output?**

Each of the two parallel digital streams has **half the bit rate** of the original Sequence Generator output.  
This occurs because the serial data is divided into two channels, where each stream processes alternating bits from the original sequence.

---

### Part B – Observing the Multiplier Outputs

Each multiplier combines the digital input signal with the carrier waveform. This operation produces a **Binary Phase Shift Keying (BPSK) signal**.

#### Question 2  
**What feature of the Multiplier output indicates that it is a BPSK signal?**

The output waveform maintains a **constant amplitude sinusoidal shape**, but its **phase shifts by 180° whenever the digital data changes state**. This phase inversion is the defining characteristic of BPSK modulation.

---

### Part C – Signal Type at the Multiplier Output

#### Question 3  
**What type of signal is present at the Multiplier output?**

The signal produced at the multiplier output is a **Binary Phase Shift Keying (BPSK) modulated carrier**.  
This signal is mathematically equivalent to a **Double Sideband Suppressed Carrier (DSBSC)** waveform in which the phase of the carrier changes according to the digital data.

---

### Part D – Generation of the QPSK Signal

The outputs of the two BPSK modulators are combined through the **Adder module**. Because the carriers used in each path are **90° out of phase**, the resulting signal forms a **Quadrature Phase Shift Keying (QPSK) waveform**.

#### Question 4  
**According to theory, what type of digital transmission is present at the Adder output?**

The signal present at the Adder output is a **QPSK-modulated signal**, formed by combining two orthogonal BPSK signals.

#### Question 5  
**Why does the waveform appear as a single sinewave even though it consists of two BPSK signals?**

Although two BPSK signals are combined, they share the **same carrier frequency**. Because their carriers are **orthogonal (90° phase difference)**, the resulting signal still appears as a single sinusoidal waveform whose **phase shifts among four possible states** to represent the digital information.

---

### Part E – Phase Discrimination

#### Question 6  
**What causes the 3-level and 4-level signals observed at the LPF output during phase adjustment?**

These multi-level signals occur when the demodulator partially detects **both BPSK components simultaneously**. If the local carrier is not perfectly aligned with one component, the output becomes a mixture of both signals, producing intermediate amplitude levels.

#### Question 7  
**How many Phase Adjust positions produce a bipolar signal?**

There are **two phase positions** that produce a bipolar signal. These correspond to the correct phase alignments where the demodulator successfully detects one of the BPSK components.

#### Question 8  
**What is the phase relationship between the local carrier and the carriers used to generate PSK₁ and PSK₂?**

The **local carrier must be phase-aligned with one of the transmitted carriers** to correctly demodulate the corresponding BPSK signal. The carriers used for **PSK₁ and PSK₂ differ by 90°**.

#### Question 9  
**Why is the demodulator considered only half of a complete QPSK receiver?**

The demodulator extracts only **one of the two BPSK components**. A full QPSK receiver requires **two separate demodulators**—one for the **in-phase (I)** component and another for the **quadrature (Q)** component.

---

## V. Reflection / Learning Summary

This experiment demonstrated the practical operation of **Quadrature Phase Shift Keying (QPSK)**, a digital modulation method capable of transmitting **two bits per symbol** by utilizing four distinct carrier phase states.

Several key concepts were reinforced throughout the experiment:

- A serial digital bit stream can be divided into **two parallel data channels**.
- Each channel can independently modulate a carrier using **BPSK modulation**.
- Two BPSK signals that differ by **90° in phase** can be combined to produce a **QPSK signal**.
- QPSK increases **spectral efficiency** by transmitting more data within the same bandwidth.
- **Phase discrimination techniques** can be used to recover individual BPSK components from the QPSK signal.
- A complete QPSK receiver requires **two demodulation paths** to reconstruct both data streams.

Overall, this experiment provided deeper insight into **advanced digital modulation techniques** and their role in modern communication systems. It highlighted how QPSK improves data transmission efficiency while maintaining reliable signal detection and recovery.
