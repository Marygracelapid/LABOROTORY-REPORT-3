# Experiment 16: Frequency Shift Keying (FSK)

## I. Objectives

The primary goals of this experiment are:

- To understand the fundamental concept of **Frequency Shift Keying (FSK)** as a digital modulation method.
- To generate an **FSK-modulated signal** using a **Voltage Controlled Oscillator (VCO)** driven by a digital data source.
- To analyze the characteristics of the generated FSK waveform using an **oscilloscope**.
- To perform **FSK signal demodulation** using a **tunable low-pass filter and envelope detection technique**.
- To reconstruct the recovered digital signal through the use of a **comparator circuit**.

---

## II. Materials and Components Used

The following equipment and components were utilized during the experiment:

- **Emona Telecoms-Trainer 101** with power supply
- **Dual-channel 20 MHz Oscilloscope**
- **Three Emona Telecoms-Trainer 101 oscilloscope probes**
- **Assorted Emona Telecoms-Trainer 101 patch leads**

These instruments were used to generate, monitor, and analyze both the **FSK signal** and its **demodulated output**.

---

## III. Procedure

### Part A – Generation of an FSK Signal
<img width="749" height="512" alt="558967610-5d3add0a-be76-43cf-9a93-d94195615e3f" src="https://github.com/user-attachments/assets/cf308995-cd12-4059-b42b-6fb56d920203" />

1. Collect all required equipment listed in the materials section.
2. Configure the oscilloscope according to the setup procedure used in the previous experiment.
3. Set the oscilloscope **Trigger Source** to **External (EXT)**.
4. Adjust the **Trigger Source Coupling** to **HF Reject**.
5. Set the **input coupling** of Channel 1 and Channel 2 to **DC**.
6. Adjust the **timebase control** to the middle position.
7. Locate the **Voltage Controlled Oscillator (VCO)** module and set its **Gain control** to approximately the midpoint.
8. Adjust the **Frequency Adjust control** to about one-quarter of its range.
9. Set the **Range selector** of the VCO to the **LO position**.
10. Locate the **Sequence Generator module** and configure its **DIP switches to 00**.
11. Interconnect the modules according to the **FSK generation block diagram**.
12. Turn on the trainer and observe both the **digital input signal** and the **FSK-modulated output** using the oscilloscope.
13. Compare the waveform of the digital signal with the resulting **FSK waveform**.

---

### Part B – Demodulation of the FSK Signal Using Filtering and Envelope Detection
<img width="675" height="297" alt="558968098-847070e6-8308-41e3-8d01-7411cc3afbe2" src="https://github.com/user-attachments/assets/54578f79-1c52-4789-9690-7d7dedb7d17d" />

1. Modify the existing setup by adding a **Tunable Low-Pass Filter (LPF)** module.
2. Adjust the **Frequency Control** of the VCO to approximately position 2 on its scale.
3. Set the **Cut-off Frequency control** of the LPF fully clockwise.
4. Turn the **Gain control** of the LPF fully clockwise.
5. Connect the modules following the **FSK demodulation block diagram**.
6. Slowly adjust the **cut-off frequency** of the LPF until the higher frequency component of the FSK signal is significantly attenuated.
7. Observe the filtered output waveform on the oscilloscope.
8. Compare the signals displayed on **Channel 1 (digital input)** and **Channel 2 (filtered output)**.

---

### Part C – Restoration of the Recovered Digital Signal Using a Comparator
<img width="776" height="319" alt="558968627-efeacbbf-5701-48aa-9aa8-d506a498db5b" src="https://github.com/user-attachments/assets/906c253d-2956-4301-82c2-b14892b2ede1" />

1. Modify the circuit again by adding a **Comparator module**.
2. Connect the **output of the envelope detector** to the **input of the comparator**.
3. Adjust the **Variable DC reference voltage** to approximately the midpoint.
4. Observe the **comparator output waveform** on the oscilloscope.
5. Compare the restored signal with the original digital signal.
6. If necessary, slightly adjust the **reference voltage** to obtain a clean and stable digital output waveform.

---

## IV. Results and Discussion

### Part A – Generation of an FSK Signal

In the first stage of the experiment, the **Sequence Generator** produced a digital data stream consisting of binary values (logic 1 and logic 0). This digital signal controlled the **Voltage Controlled Oscillator (VCO)**, which generated a sinusoidal waveform whose **frequency varied depending on the logic level of the input signal**.

When the digital input was **logic 1**, the VCO generated a sinusoidal signal at a specific frequency known as the **Mark Frequency**. Conversely, when the digital input switched to **logic 0**, the oscillator produced a different frequency called the **Space Frequency**.

The alternating output between these two frequencies represents the **Frequency Shift Keying (FSK)** modulation process. Unlike amplitude modulation, where the amplitude of the carrier varies, FSK transmits information by **switching between two distinct carrier frequencies**.

#### Answers

**1. What is the name for the VCO output frequency that corresponds with logic-1 in the digital data?**  
The frequency associated with logic-1 is called the **Mark Frequency**.

**2. What is the name for the VCO output frequency that corresponds with logic-0 in the digital data?**  
The frequency corresponding to logic-0 is called the **Space Frequency**.

**3. Which of the two frequencies is higher? Explain.**  
Typically, the **Mark Frequency** is higher than the **Space Frequency** because the control voltage corresponding to logic-1 increases the oscillation frequency of the VCO.

---

### Part B – Demodulation of the FSK Signal

During this stage, the FSK waveform was applied to a **tunable low-pass filter** in order to isolate one of the two frequencies present in the signal.

Because an FSK waveform contains **two alternating sinusoidal frequencies**, the filter can be adjusted to allow only one frequency component to pass while attenuating the other. In this experiment, the filter was tuned to select the **higher frequency component (Mark frequency)**.

As a result, the output waveform appeared as **bursts of sinusoidal signals** whenever the selected frequency was present. When the other frequency occurred, the output amplitude was significantly reduced.

This filtered signal resembles an **amplitude-modulated waveform**, where the presence of the selected frequency corresponds to a particular digital logic state.

#### Answers

**1. Which of the FSK signal’s two sinewaves does the filter select?**  
The filter selects the **higher frequency sinewave**, which corresponds to the **Mark frequency**.

**2. What does the filtered FSK signal look like?**  
The filtered signal appears as **bursts of sinusoidal waves** when the selected frequency is present. When the alternate frequency occurs, the signal amplitude becomes very small.

**3. What component can be used to clean up the recovered digital signal?**  
A **Comparator circuit** can be used to restore and clean the recovered digital signal.

---

### Part C – Restoration of the Recovered Digital Signal

After the filtering and envelope detection stages, the recovered signal still contained **gradual rising and falling edges**. This occurs because the filtering process smooths the waveform, which prevents the formation of sharp digital transitions.

To restore the waveform into a clean digital signal, a **Comparator module** was implemented. The comparator compares the recovered analog signal with a **reference voltage**.

If the input signal exceeds the reference voltage, the comparator produces a **logic-high output**. If the input falls below the threshold, the comparator outputs a **logic-low signal**.

Through this process, the comparator converts the distorted analog waveform into a **clean square-wave digital signal**, closely matching the original input data.

#### Answer

**How does the comparator convert slow-rising voltages into sharp transitions?**

The comparator continuously compares the input signal to a **reference threshold voltage**. When the signal crosses this threshold, the comparator rapidly switches between high and low output states, producing **sharp transitions that recreate the original digital waveform**.

---

## V. Reflection / Learning Summary

This experiment demonstrated the practical implementation of **Frequency Shift Keying (FSK)** as a digital modulation technique. Unlike amplitude modulation methods, FSK conveys digital information by **switching between two different carrier frequencies**.

Several key concepts were reinforced during the experiment:

- Digital information can be transmitted by varying the **frequency of a carrier signal**.
- The two frequencies used in FSK are known as the **Mark Frequency** and **Space Frequency**.
- **Tunable filters** can isolate specific frequency components of a signal during demodulation.
- **Envelope detection** assists in extracting the embedded information from the modulated signal.
- **Comparator circuits** are essential for restoring distorted analog signals into clean digital outputs.

Overall, the experiment enhanced understanding of **digital communication systems**, particularly how digital signals are **modulated, transmitted, demodulated, and reconstructed** using electronic circuits.
