EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT
AIM:
To Obtain DFT and FFT of a given sequence in SCILAB.
APPARATUS REQUIRED:
PC installed with SCILAB.

PROGRAM:
// DISCRETE FOURIER TRANSFORM


clc;
clear;

// Step 1: Take N and x(n) as input
N = input("Enter the length of the signal N: ");
x = zeros(1, N);

disp("Enter the signal values:");
for i = 1:N
    x(i) = input("x(" + string(i-1) + ") = ");
end

// Step 2: Initialize DFT array
X = zeros(1, N);

// Step 3: Compute DFT
for k = 0:N-1
    sum_val = 0;
    for n = 0:N-1
        sum_val = sum_val + x(n+1) * exp(-%i * 2 * %pi * k * n / N);
    end
    X(k+1) = sum_val;
end

// Step 4: Display in desired { a ± jb } format
str_out = "{";
for k = 1:N
    real_part = round(real(X(k))*1000)/1000; // rounding to 3 decimals
    imag_part = round(imag(X(k))*1000)/1000;
    
    if imag_part >= 0 then
        str_out = str_out + string(real_part) + " + j" + string(imag_part);
    else
        str_out = str_out + string(real_part) + " - j" + string(abs(imag_part));
    end
    
    if k < N then
        str_out = str_out + ", ";
    else
        str_out = str_out + "}";
    end
end

disp("X(k) = " + str_out);

// Step 5: Plot magnitude and phase
freq_index = 0:N-1;

subplot(2,1,1);
plot(freq_index, abs(X), 'o-');
xlabel("Frequency index (k)");
ylabel("|X(k)|");
title("Magnitude Spectrum");

subplot(2,1,2);
plot(freq_index, atan(imag(X), real(X)), 'o-'); // phase = atan2(imag, real)
xlabel("Frequency index (k)");
ylabel("Phase (radians)");
title("Phase Spectrum");
OUTPUT:
image image
RESULT:
