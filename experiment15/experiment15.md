# Experiment 15: Amplitude Shift Keying (ASK)

## I. Objectives
The objectives of this experiment are:

- To generate an **Amplitude Shift Keying (ASK)** modulated signal.
- To examine the relationship between a **digital data signal** and the **ASK-modulated carrier**.
- To demodulate an ASK signal using an **envelope detector circuit**.
- To restore the recovered digital signal using a **comparator circuit**.
- To understand the operational principle of **On-Off Keying (OOK)** in digital communication systems.

---

## II. Materials and Components Used

| Item | Description |
|-----|-------------|
| Trainer | Emona Telecoms-Trainer 101 with power-pack |
| Oscilloscope | Dual-channel 20 MHz oscilloscope |
| Modules | Master Signals, Sequence Generator, Dual Analog Switch, VCO, Rectifier, Tuneable Low-pass Filter, Comparator (Utilities), Variable DCV |
| Leads | Three oscilloscope probes and assorted patch leads |

---

## III. Preliminary Discussion

In modern telecommunications systems, transmission media such as cables, fiber optics, and wireless channels are **limited resources** that must be efficiently shared among multiple users. Two commonly used techniques to enable this sharing are **Time Division Multiplexing (TDM)** and **Frequency Division Multiplexing (FDM)**.

In **TDM**, multiple signals share the same communication channel by transmitting at different time intervals. In contrast, **FDM** allows several signals to be transmitted simultaneously by assigning each signal a different carrier frequency within the channel bandwidth.

One important technique used in digital communication is **Amplitude Shift Keying (ASK)**. ASK is a digital modulation method where the **amplitude of a carrier signal is controlled by a digital data signal**. In this process, a carrier wave is switched **on or off** depending on the binary data being transmitted.

When the digital input is **logic high (1)**, the carrier signal is present. When the digital input is **logic low (0)**, the carrier signal is suppressed. Because the carrier either appears or disappears based on the data, this modulation technique is commonly referred to as **On-Off Keying (OOK)**.

This experiment demonstrates how an ASK signal can be **generated**, **demodulated using an envelope detector**, and **restored to its original digital form using a comparator**.

---

## IV. Procedure

### Part A: Generation of an ASK Signal

1. Gather all the required equipment listed in the materials section.
2. Configure the oscilloscope according to the setup instructions described in Experiment 1.
3. Set the oscilloscope **Trigger Source** control to **EXT**.
4. Adjust the **Trigger Source Coupling** control to **HF REJ**.
5. Set the **Input Coupling** of both Channel 1 and Channel 2 to **DC**.
6. Adjust the **Timebase** setting to **1 ms/div**.
7. Connect the system such that:
   - The **2 kHz Digital output** from the **Master Signals module** drives the **Sequence Generator clock input**.
   - The **2 kHz Sine output** is connected to the **Dual Analog Switch module** as the carrier signal.
8. Observe the output waveform.

![FIGURE 3](https://github.com/user-attachments/assets/3913d44e-90ca-494a-bd8a-440b2a78d357)

9. Set the oscilloscope **Mode** to **DUAL** in order to simultaneously observe:
   - The **Sequence Generator digital output**
   - The **ASK signal** from the Dual Analog Switch module
10. Compare the digital signal with the ASK waveform.

11. Locate the **Voltage Controlled Oscillator (VCO)** module.
12. Adjust the **Frequency Control** to approximately the midpoint of its range.
13. Set the **Range switch** of the VCO to **HI**.
14. Replace the **2 kHz sine carrier** with the **high-frequency carrier produced by the VCO** (approximately 100 kHz).

![FIGURE 5](https://github.com/user-attachments/assets/173bfcf6-b8de-463f-bed0-822ebe511da4)


15. Observe and compare the signals.
16. Use the oscilloscope **Channel 1 Vertical Position** control to align the digital signal with the envelope of the ASK waveform to clearly visualize their relationship.

---

### Part B: Demodulation of the ASK Signal Using an Envelope Detector

1. Locate the **Tuneable Low-pass Filter module**.
2. Rotate the **Gain control** fully clockwise.
3. Adjust the **Cut-off Frequency control** fully clockwise.
4. Modify the existing circuit by inserting the **Rectifier module** followed by the **Low-pass Filter module**.

This configuration forms an **envelope detector**.

![FIGURE 7 (1)](https://github.com/user-attachments/assets/40ec7fe7-9d8f-4b70-a3be-17a1a80f1cd1)


5. Observe the waveform of the **recovered signal**.
6. Compare the **original digital signal** with the **demodulated output signal**.

---

### Part C: Restoration of the Digital Signal Using a Comparator

1. Modify the circuit by connecting the **filter output** to the **Comparator module**.
2. Adjust the **Variable DCV module** so that its **Variable DC control** is approximately at the midpoint.

![FIGURE 9](https://github.com/user-attachments/assets/cada43e2-2154-41b5-bec0-93cc962802e7)


3. Observe and compare the recovered digital signal with the original digital waveform.
4. If the signals do not match closely, slowly adjust the **Variable DC reference voltage** until the comparator output closely resembles the original digital signal.

---

## V. Results and Discussion

The experiment successfully demonstrated the process of generating and recovering a **digital signal transmitted using Amplitude Shift Keying (ASK)**.

During signal generation, the digital sequence controlled the **presence or absence of the carrier wave**, producing an ASK waveform. When the digital signal was high, the carrier was present, while when the digital signal was low, the carrier was suppressed. This behavior clearly illustrates the **On-Off Keying principle**.

After generating the ASK signal, demodulation was achieved using an **envelope detector composed of a rectifier and a low-pass filter**. The rectifier extracted the positive envelope of the modulated waveform, while the low-pass filter smoothed the signal to approximate the original digital data.

However, the recovered signal was not an exact replica of the original digital signal. The output showed **rounded transitions and slight distortion**, which occurred because the low-pass filter removed some of the higher frequency components that are necessary for preserving the sharp edges of a square wave.

To address this distortion, a **comparator circuit** was used. The comparator compared the recovered signal with a reference voltage and generated a digital output depending on whether the signal was above or below the threshold. This process effectively restored the signal by converting the smooth waveform into **sharp digital transitions**, closely matching the original data signal.

Overall, the experiment demonstrated the complete process of **ASK modulation, demodulation, and signal restoration**, which are fundamental operations in digital communication systems.

---

## VI. Questions and Answers

**1. What is the relationship between the digital signal and the presence of the carrier in the ASK signal?**  
The carrier signal is transmitted when the digital signal is at logic **1**, and it is suppressed when the digital signal is at logic **0**.

**2. What is the ASK signal’s voltage when the digital signal is logic 0?**  
When the digital signal is logic **0**, the ASK signal amplitude is approximately **0 V**, indicating that the carrier is absent.

**3. What feature of the ASK signal indicates that it is an AM signal?**  
The amplitude of the carrier changes in accordance with the digital data signal. The **envelope of the carrier waveform follows the pattern of the digital signal**, which is characteristic of amplitude modulation.

**4. Why is the recovered digital signal not an exact copy of the original signal?**  
The recovered signal contains distortions because the **low-pass filter attenuates some high-frequency components of the square wave**, resulting in smoother transitions instead of sharp edges.

**5. What component can be used to clean up the recovered digital signal?**  
A **comparator circuit** can be used to clean and restore the digital signal.

**6. How does the comparator convert the slow-rising voltages into sharp transitions?**  
The comparator compares the incoming signal with a **reference threshold voltage**. If the input exceeds the threshold, the output switches to a maximum voltage level; if it falls below the threshold, the output switches to a minimum voltage level. This switching action produces **clear and sharp digital transitions**.

---

## VII. Reflection / Learning Summary

This experiment provided a deeper understanding of how **digital data can be transmitted through analog communication channels** using Amplitude Shift Keying. The process demonstrated how binary information can be represented by controlling the amplitude of a carrier wave.

The experiment also illustrated the importance of **signal demodulation techniques**, particularly the use of an envelope detector for extracting the original signal from the modulated waveform. Although filtering introduces distortion, the use of a **comparator allows the signal to be reconstructed accurately**.

Through this activity, the fundamental concepts of **digital modulation, signal recovery, and noise tolerance in communication systems** were clearly demonstrated, highlighting the reliability and efficiency of digital transmission methods.
