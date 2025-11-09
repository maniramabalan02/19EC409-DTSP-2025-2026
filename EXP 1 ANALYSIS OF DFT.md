# EXP 1 :  ANALYSIS OF DFT WITH AUDIO SIGNAL

# AIM: 
 To analyze audio signal by removing unwanted frequency.

# APPARATUS REQUIRED: 
   PC installed with SCILAB/Python. 

# PROGRAM:
```
// analyze audio signal
clc; clear;

// ---- Step 1: Load audio file ----
// Make sure the file exists in the given path
[x, fs, bits] = wavread("C:\Users\acer\Downloads\waptt.wav");

// If stereo, take only one channel
if size(x, 2) > 1 then
    x = x(:,1);
end

// ---- Step 2: (Optional) Trim first 2 seconds ----
cut_samples = round(2 * fs);
if length(x) > cut_samples then
    x = x(cut_samples+1:$);
end

// ---- Step 3: Play audio (if playsnd available) ----
disp("Playing trimmed audio...");
playsnd(x, fs);

// ---- Step 4: Compute FFT ----
N = length(x);             // Number of samples
Y = fft(x, -1);            // FFT
f = (0:N-1) * (fs / N);    // Frequency axis in Hz

// ---- Step 5: Plot magnitude & phase ----
clf();
subplot(2,1,1);
plot(f, abs(Y));
xlabel("Frequency (Hz)");
ylabel("Magnitude");
title("Magnitude Spectrum of Audio Signal");

subplot(2,1,2);
plot(f, atan(imag(Y), real(Y)));  // Phase
xlabel("Frequency (Hz)");
ylabel("Phase (radians)");
title("Phase Spectrum of Audio Signal");
```
# OUTPUT: 
![WhatsApp Image 2025-09-08 at 15 44 14_a425ca46](https://github.com/user-attachments/assets/b22a11ab-8dad-4c35-b162-1e9c530d032e)

# RESULTS
Audio signal by removing unwanted frequency was analysised
