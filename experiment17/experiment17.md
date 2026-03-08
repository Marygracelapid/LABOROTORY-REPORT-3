# Experiment 17: Binary Phase Shift Keying (BPSK)

## I. Objectives

The objectives of this experiment are as follows:

- To generate a **Binary Phase Shift Keying (BPSK)** modulated signal.
- To observe the **180° phase reversal** that occurs during transitions of the digital data signal.
- To demodulate a BPSK signal using a **product detector**.
- To recover and restore the digital signal using a **comparator circuit**.
- To examine the relationship between **BPSK modulation** and **Double-Sideband Suppressed Carrier (DSBSC)** modulation.

---

## II. Materials and Components Used

| Item | Description |
|-----|-------------|
| Trainer | Emona Telecoms-Trainer 101 with power supply |
| Oscilloscope | Dual-channel 20 MHz Oscilloscope |
| Modules | Master Signals Module, Sequence Generator, Multiplier (Product Modulator), Tunable Low-pass Filter, Comparator (Utilities), Variable DC Voltage Module |
| Leads | Three oscilloscope probes and assorted patch leads |

---

## III. Introduction / Preliminary Discussion

**Binary Phase Shift Keying (BPSK)** is a digital modulation technique in which binary data is transmitted by altering the **phase of a carrier signal**. Unlike **Amplitude Shift Keying (ASK)** and **Frequency Shift Keying (FSK)**, which modify the amplitude and frequency of the carrier respectively, BPSK encodes information by changing the **phase angle** of the carrier waveform.

In BPSK modulation, a change in the digital input signal causes the carrier signal to undergo a **180° phase shift**. This means that when the digital signal changes state, the sinusoidal carrier waveform effectively **inverts its polarity**. For instance, a logic 1 may correspond to a carrier wave starting at a positive peak, while a logic 0 corresponds to the same carrier starting at a negative peak.

From a mathematical perspective, BPSK can be considered equivalent to **Double-Sideband Suppressed Carrier (DSBSC)** modulation in which the message signal is a **bipolar digital waveform**. Since the amplitude of the carrier remains constant and only the phase changes, BPSK provides **improved resistance to noise and better error performance** compared to other modulation methods such as ASK and FSK.

---

## IV. Procedure

### Part A – Generation of a BPSK Signal
![FIGURE 3 (2)](https://github.com/user-attachments/assets/7e73e93e-1c4b-451c-990c-3c4d144149f7)

1. Assemble all equipment listed in the materials section.
2. Configure the oscilloscope according to the setup instructions described in **Experiment 1**.
3. Set the oscilloscope **Trigger Source** to **External (EXT)**.
4. Adjust the **Trigger Source Coupling** to **HF Reject**.
5. Set the **Input Coupling** for both Channel 1 and Channel 2 to **DC**.
6. Adjust the **Timebase control** to **0.1 ms/div**.
7. Locate the **Sequence Generator module** and set its **DIP switches to 00**.
8. Establish the circuit connections as follows:

   - Sequence Generator **CLK** → Master Signals **8 kHz clock output**
   - Sequence Generator **SYNC** → Oscilloscope **EXT trigger input**
   - Sequence Generator **OUT** → Multiplier **X input**
   - Master Signals **100 kHz sine output** → Multiplier **Y input**

9. Observe the output signals on the oscilloscope.

10. Set the oscilloscope **Mode** to **DUAL** to simultaneously view the **digital data signal** and the **BPSK waveform**.

11. Activate the oscilloscope **Sweep Magnification** control to clearly observe the signal transitions.

12. Compare the signals and observe the **phase inversion occurring at digital transitions**.

13. Adjust the **Horizontal Position control** if necessary to clearly view the phase changes.

14. Disable the **Sweep Magnification** function after observation.

15. Use the **Channel 1 Vertical Position control** to overlay the digital waveform with the BPSK signal envelope for easier comparison.

---

### Part B – Demodulation of the BPSK Signal Using a Product Detector
![FIGURE 5 (2)](https://github.com/user-attachments/assets/47dbb46c-d433-46c3-a31b-d2a78c631f82)

1. Locate the **Tunable Low-pass Filter module**.
2. Rotate the **Cut-off Frequency control** fully clockwise.
3. Adjust the **Gain control** to approximately the midpoint.
4. Modify the existing setup by adding:

   - A **second Multiplier module**
   - The **Low-pass Filter module**

5. Configure these modules to form a **product detector**.
6. Observe the demodulated output signal on the oscilloscope.
7. Compare the **original digital signal** with the **recovered signal** obtained after demodulation.

---

### Part C – Restoration of the Digital Signal Using a Comparator
![FIGURE 7 (3)](https://github.com/user-attachments/assets/3a4d2dc4-3d65-45e2-b962-1147287c8146)

1. Modify the circuit by connecting the **Low-pass Filter output** to the **Comparator input**.
2. Connect the **Variable DC Voltage module** to the **Comparator reference (REF) input**.
3. Adjust the **Variable DC control** to approximately the midpoint.
4. Observe the comparator output on the oscilloscope.
5. Compare the **restored digital signal** with the **original digital signal**.
6. If necessary, adjust the **reference voltage** until the recovered waveform closely matches the original digital signal (ignoring phase shift).

---

## V. Results and Discussion

### Part A – Generation of a BPSK Signal

During the initial stage of the experiment, the **Sequence Generator module** produced a digital data stream consisting of alternating logic states. This digital signal was applied to a **multiplier module**, where it modulated a high-frequency sinusoidal carrier from the **Master Signals module**.

As the digital data changed between logic 1 and logic 0, the output waveform exhibited **phase reversals of 180°**. In other words, the sinusoidal carrier inverted its polarity whenever the digital signal transitioned from one state to another. This phase inversion is the defining characteristic of **Binary Phase Shift Keying (BPSK)**.

The oscilloscope clearly showed that the carrier signal maintained a constant amplitude while only its **phase orientation changed**, which is consistent with the theoretical behavior of BPSK modulation.

---

### Part B – Demodulation of the BPSK Signal

The demodulation process was carried out using a **product detector**, which consisted of a second multiplier followed by a **low-pass filter**. The product detector multiplied the received BPSK signal with a reference carrier signal, effectively recovering the baseband information.

After multiplication, the resulting signal contained both **high-frequency components** and the desired **baseband digital signal**. The **low-pass filter** removed the high-frequency components, leaving a waveform that resembled the original digital data.

However, the recovered signal was not a perfect replica of the original waveform because the filtering process removed some high-frequency components of the square wave. As a result, the edges of the waveform appeared **rounded rather than sharply defined**.

---

### Part C – Restoration of the Recovered Digital Signal

To reconstruct a clean digital waveform, the filtered signal was passed through a **comparator circuit**. The comparator compared the recovered analog signal with a **reference threshold voltage**.

Whenever the signal amplitude exceeded the reference voltage, the comparator produced a **logic-high output**. When the signal dropped below the threshold, the output switched to **logic-low**.

This process effectively converted the distorted analog waveform into a **clean square-wave digital signal**, restoring the original digital data.

---

## VI. Questions and Answers

**1. What happens to the BPSK signal when the data stream experiences a logic transition?**  
At each logic transition, the BPSK signal undergoes a **180° phase shift**, causing the sinusoidal carrier waveform to invert its polarity.

**2. What characteristic of the BPSK signal suggests that it behaves like a DSBSC signal?**  
The **signal envelope follows the digital data pattern** and crosses zero when polarity changes occur, which is typical behavior for a **Double-Sideband Suppressed Carrier (DSBSC)** signal.

**3. Why is the recovered digital signal not an exact replica of the original signal?**  
The **low-pass filter removes high-frequency components** of the square wave, which results in **rounded edges and minor waveform distortion**.

**4. What component can be used to clean up the recovered digital signal?**  
A **comparator circuit** or **Schmitt trigger** can be used to restore the signal into a clean digital waveform.

**5. Why does adjusting the DC reference voltage affect the shape of the output digital signal?**  
The DC reference voltage sets the **threshold level** of the comparator. Because the recovered signal contains gradual transitions, changing the threshold alters the switching point of the comparator, which affects the **pulse width and shape of the output waveform**.

---

## VII. Reflection / Learning Summary

This experiment demonstrated the practical implementation of **Binary Phase Shift Keying (BPSK)** as a digital modulation technique. The experiment showed how digital data can be transmitted by **changing the phase of a carrier signal while maintaining a constant amplitude**.

The relationship between **digital transitions and carrier phase inversion** was clearly observed through the oscilloscope waveforms. The experiment also illustrated the process of **BPSK demodulation using a product detector**, followed by signal recovery using a **low-pass filter and comparator**.

Although filtering introduced minor distortion in the recovered waveform, the comparator successfully restored the signal to a clean digital format. Overall, the experiment provided valuable insight into **phase modulation techniques** and demonstrated why BPSK is widely used in modern **digital communication systems due to its robustness against noise and interference**.
