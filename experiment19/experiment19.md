# Experiment 19: Direct Sequence Spread Spectrum (DSSS) Modulation and Demodulation

## I. Objectives

The objectives of this experiment are:

- To generate a **Direct Sequence Spread Spectrum (DSSS)** signal.
- To understand how a **Pseudo-Noise (PN) sequence** spreads a message signal over a wider bandwidth.
- To observe the similarity between **DSSS modulation** and **Double Sideband Suppressed Carrier (DSBSC)** modulation.
- To recover the original message signal using a **synchronized product detector**.
- To examine the effect of **incorrect PN sequence synchronization** during signal recovery.
- To investigate the **interference rejection capability** of DSSS communication systems.

---

## II. Materials and Components Used

| Item | Description |
|-----|-------------|
| Trainer | Emona Telecoms-Trainer 101 with power supply |
| Oscilloscope | Dual-channel 20 MHz Oscilloscope |
| Modules | Master Signals Module, Sequence Generator, Multiplier (Product Modulator), Adder, Tunable Low-pass Filter, Speech Module, Voltage Controlled Oscillator (VCO) |
| Leads | Two oscilloscope probes and assorted patch leads |

These instruments were used to generate, observe, and analyze the DSSS signal, as well as its demodulation and interference characteristics.

---

## III. Introduction / Preliminary Discussion

**Direct Sequence Spread Spectrum (DSSS)** is a digital modulation technique in which the transmitted signal occupies a bandwidth much wider than that required by the original message signal. This spreading process is achieved by multiplying the message signal with a high-frequency **Pseudo-Noise (PN) sequence**.

The PN sequence acts as a rapidly changing digital carrier that continuously switches polarity. This process distributes the energy of the message signal across a broad frequency range, effectively **spreading the signal spectrum**.

Mathematically, DSSS is similar to **Double Sideband Suppressed Carrier (DSBSC)** modulation. However, instead of using a sinusoidal carrier, DSSS uses a fast digital code sequence as the spreading signal. Because the signal power is distributed over a wide bandwidth, the resulting transmitted waveform often appears **noise-like** and may fall below the noise floor in real communication environments.

At the receiver, the original message can be recovered by multiplying the received signal with an **identical PN sequence** that is perfectly synchronized in both frequency and phase. If the PN sequence used for despreading does not match the original sequence, the signal cannot be recovered and instead appears as random noise.

This property provides **security, interference resistance, and robustness**, making DSSS a fundamental technique used in modern wireless communication systems.

---

## IV. Procedure

### Part A – Generation of a DSSS Signal Using a Simple Message
![FIGURE 2 (5)](https://github.com/user-attachments/assets/58c0de74-5389-4ccf-9043-67315e13bda3)

1. Collect the required equipment listed in the materials section.
2. Configure the oscilloscope with the following settings:
   - Trigger Source → **Channel 1**
   - Mode → **CH1**
   - Trigger Source Coupling → **HF Reject**
3. Set the **Sequence Generator DIP switches** to **00**.
4. Establish the circuit connections as follows:
   - **2 kHz sinewave** from the Master Signals module → Multiplier **Input A**
   - **100 kHz clock** → Sequence Generator clock input
   - **PN output** from the Sequence Generator → Multiplier **Input B**
5. Adjust the oscilloscope **Timebase** to display approximately two cycles of the 2 kHz sinewave.
6. Set the oscilloscope to **DUAL mode** to view both the original message signal and the DSSS signal.
7. Adjust the vertical sensitivity to clearly display both waveforms.
8. Observe and compare the message signal with the **envelope of the DSSS waveform**.

---

### Part B – Generation of a DSSS Signal Using Speech
![FIGURE 5 (4)](https://github.com/user-attachments/assets/e2c87a90-4a84-437e-8c45-bae460a19387)
1. Disconnect the **2 kHz sinewave** from the multiplier input.
2. Connect the **Speech Module output** to the multiplier input.
3. Adjust the oscilloscope **Timebase** to **2 ms/div**.
4. Speak or produce sound into the microphone of the Speech Module.
5. Observe the resulting **spread-spectrum waveform** on the oscilloscope.

---

### Part C – Recovering the Message Using a Product Detector
![FIGURE 6 (4)](https://github.com/user-attachments/assets/cfa3048e-af07-4bb0-ae2c-17749b262810)
1. Connect the DSSS output signal to a **second Multiplier module**, which will act as a **product detector**.
2. Use the same **PN sequence from the transmitter** and connect it to the second multiplier.
3. Connect the multiplier output to the **Tunable Low-pass Filter (LPF)**.
4. Adjust the **LPF cut-off frequency and gain** appropriately.
5. Observe the **recovered signal** on the oscilloscope.
6. Replace the PN sequence at the receiver with a **different PN sequence**.
7. Observe the LPF output again and note the changes.

---

### Part D – DSSS with Deliberate Interference (Jamming)
![FIGURE 9 (4)](https://github.com/user-attachments/assets/a6d32697-cbe5-47ad-9843-fb8fff0e53a5)

1. Introduce a **VCO output signal** to the DSSS signal using an **Adder module**.
2. Adjust the VCO frequency to create a **narrowband jamming signal**.
3. Gradually increase the amplitude of the jammer.
4. Observe the **combined signal waveform** on the oscilloscope.
5. Pass the combined signal through the **product detector and LPF**.
6. Observe the recovered message signal.
7. Vary the **jammer frequency and amplitude** and examine their effects on the recovered output signal.

---

## V. Results and Discussion

### Question 1  
**What feature of the Multiplier output indicates that it behaves like a DSBSC signal?**

The multiplier output exhibits **phase reversals corresponding to transitions of the PN sequence**, while the envelope of the signal follows the message waveform. This behavior is characteristic of **Double Sideband Suppressed Carrier (DSBSC)** modulation.

---

### Question 2  
**Why does the DSSS signal appear large on the oscilloscope even though it is expected to appear noise-like?**

In the laboratory setup, the signal is observed directly in the **time domain before transmission losses occur**. In practical communication systems, the signal power is distributed across a much wider bandwidth, which lowers the **power spectral density**, causing it to appear noise-like.

---

### Question 3  
**Why is there no output from the DSSS modulator when there is no speech input?**

The multiplier performs a mathematical multiplication operation:
0xPN

If the input message signal has **zero amplitude**, the multiplication process produces **no output signal**.

---

### Question 4  
**What does the output of the Low-pass Filter look like when the correct PN sequence is used?**

When the correct PN sequence is applied, the recovered signal closely resembles the **original message waveform**, such as the **2 kHz sinewave or speech signal**, although slight attenuation or filtering effects may occur.

---

### Question 5  
**Why does using an incorrect PN sequence produce noise at the output?**

DSSS relies on the principle of **correlation**. When an incorrect PN sequence is used at the receiver, the signal cannot be properly despread. Instead, the multiplication process spreads the signal energy further across the frequency spectrum. As a result, the **Low-pass Filter receives only random components**, producing a noise-like output.

---

### Question 6  
**Why does the jamming signal not prevent recovery of the original message?**

When the received signal is multiplied by the **correct PN sequence**, the DSSS signal is **despread**, returning it to its original narrow bandwidth. However, the jamming signal becomes **spread across a wider bandwidth** during this process. The **Low-pass Filter then removes most of the jammer energy while passing the recovered message**, demonstrating the **processing gain and interference rejection capability of DSSS systems**.

---

## VI. Reflection / Learning Summary

This experiment demonstrated the practical implementation of **Direct Sequence Spread Spectrum (DSSS)** modulation and demodulation. A DSSS signal was produced by multiplying a message signal with a **high-frequency pseudo-noise sequence**, which spread the signal energy across a wide frequency band.

The experiment showed that successful message recovery requires a **synchronized PN sequence** at the receiver. When the correct sequence was used, the original message was successfully reconstructed. However, when an incorrect sequence was applied, the recovered signal appeared as noise.

Additionally, the experiment illustrated the **strong interference resistance of DSSS systems**. Even in the presence of a high-amplitude jamming signal, the receiver was able to recover the original message because the despreading process reduced the effect of the interference.

Overall, this laboratory exercise provided valuable insight into **spread-spectrum communication techniques**, highlighting their advantages in terms of **security, robustness, and interference suppression in modern wireless communication systems**.
