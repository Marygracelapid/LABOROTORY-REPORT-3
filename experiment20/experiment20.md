# Experiment 20: Undersampling in SDR (Software Defined Radio)

## I. Objectives

The objectives of this experiment are:

- To configure and observe a **bandwidth-limited Double Sideband Suppressed Carrier (DSBSC)** signal.
- To demonstrate the **direct down-conversion** of a high-frequency signal through the principle of **undersampling**.
- To examine the relationship among **sampling frequency, carrier frequency, and the resulting baseband signal**.

---

## II. Materials and Components Used

| Equipment / Component | Description |
|-----------------------|-------------|
| Trainer | Emona Telecoms-Trainer 101 with power pack |
| Oscilloscope | Dual-channel 20 MHz Oscilloscope |
| Oscilloscope Leads | Two Emona Telecoms-Trainer 101 oscilloscope leads |
| Patch Leads | Assorted Emona Telecoms-Trainer 101 patch leads |
| Modules | Master Signals Module, Multiplier Module, Dual Analog Switch Module, Tuneable Low-Pass Filter (LPF), Baseband Low-Pass Filter (LPF) |

---

## III. Procedure

### Part A – Setting Up a Bandwidth-Limited Signal
![FIGURE 2 (7)](https://github.com/user-attachments/assets/fb6c7923-7627-4a85-9771-2031b7d79819)

1. Assemble the circuit following the **“Setting up a Bandwidth-limited Signal”** block diagram.
2. Apply a **2 kHz sine wave** as the message signal and a **100 kHz sine wave** as the carrier signal to the **Multiplier module**.
3. The Multiplier produces a **Double Sideband Suppressed Carrier (DSBSC)** modulated signal.
4. Connect the output of the Multiplier module to **Channel 1 of the oscilloscope** to observe the resulting waveform.
5. Measure and record the **frequency components and bandwidth** of the generated signal.

---

### Part B – Direct Down-Conversion Using Undersampling
![FIGURE 4 (7)](https://github.com/user-attachments/assets/12f3dbe7-a358-4dca-bb8b-4b0ada270996)

1. Feed the DSBSC signal generated in **Part A** into the **Dual Analog Switch module** to perform signal sampling.
2. Provide the **sampling clock frequency (\(f_s\))** using the **VCO module or Master Signals module**.
3. Pass the sampled signal through the **Baseband Low-Pass Filter (LPF)** to recover the message signal.
4. Observe the recovered signal on **Channel 2 of the oscilloscope**.
5. Compare the recovered signal with the original **2 kHz message signal**.
6. Adjust the sampling frequency to analyze how **undersampling affects signal reconstruction**.

---

## IV. Results and Discussion

### Data Observations

Based on the oscilloscope captures (Images 74, 75, and 76), the following signals were observed:

- **Message Signal (\(f_m\))**: 2 kHz sine wave  
- **Carrier Signal (\(f_c\))**: 100 kHz sine wave  
- **DSBSC Output**: A modulated waveform with a suppressed carrier, displaying characteristic **phase reversals** typical of DSBSC modulation  
- **Recovered Signal**: After sampling and filtering, the **original 2 kHz message signal** was successfully reconstructed even though the sampling rate was significantly lower than the carrier frequency

---

### Questions and Answers

#### 1. For the given inputs to the Multiplier module, what are the frequencies of the two sine waves that form the DSBSC signal?

The DSBSC signal consists of two frequency components produced by the **sum and difference** of the carrier and message frequencies:

- **Upper Sideband (USB):**

\[
f_{USB} = f_c + f_m = 100\,kHz + 2\,kHz = 102\,kHz
\]

- **Lower Sideband (LSB):**

\[
f_{LSB} = f_c - f_m = 100\,kHz - 2\,kHz = 98\,kHz
\]

Thus, the DSBSC signal contains frequency components at **102 kHz and 98 kHz**.

---

#### 2. What is the bandwidth of the DSBSC signal?

The bandwidth of a DSBSC signal is twice the message frequency:

\[
BW = (f_c + f_m) - (f_c - f_m) = 2f_m
\]

\[
BW = 102\,kHz - 98\,kHz = 4\,kHz
\]

Therefore, the **bandwidth of the DSBSC signal is 4 kHz**.

---

#### 3. What is the significance of the signal at the output of the Baseband LPF?

The signal observed at the **Baseband LPF output** represents the **recovered message signal**.  

This demonstrates that through **undersampling**, a high-frequency bandpass signal can be effectively translated to **baseband**. The low-pass filter isolates the desired alias component, allowing the original message signal to be reconstructed.

---

#### 4. Given a sampling frequency (\(f_s\)) of X, why is the signal still recovered?

The signal is successfully recovered due to the **Nyquist Criterion for bandpass signals**. While the traditional Nyquist requirement for baseband signals is:

\[
f_s > 2f_{max}
\]

bandpass signals follow a different condition. As long as:

\[
f_s > 2 \times BW
\]

the signal information is preserved in the **alias frequencies** produced during sampling. The filtering stage then selects the correct alias corresponding to the **baseband representation of the original signal**.

---

## V. Reflection / Learning Summary

This experiment demonstrated the practical application of **undersampling in Software Defined Radio (SDR)** systems. One key takeaway is that the conventional Nyquist sampling rule primarily applies to **baseband signals**, whereas **bandpass signals** can be sampled at lower rates without losing information.

By intentionally undersampling the DSBSC signal, the high-frequency carrier was effectively **aliased to a lower frequency**, allowing the system to recover the original **2 kHz message signal** after low-pass filtering.  

This technique is widely used in **SDR architectures**, as it reduces the required **Analog-to-Digital Converter (ADC) sampling speed** and minimizes the need for additional **analog mixers and local oscillators** for frequency down-conversion. The clear reconstruction of the message signal on the oscilloscope confirmed that accurate recovery is possible as long as the **sampling frequency satisfies the bandwidth-based sampling condition**.
