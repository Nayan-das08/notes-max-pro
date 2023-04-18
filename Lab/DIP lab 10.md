# Experiment 10
Mar 3, 2023

## Aim
Write a program for Butterworth low pass filter.

## Source Code
```
clc;
close all;
clear;
A = imread("medical_images\1.png");
A = im2gray(A);

r = 3;
c = 2;

subplot(r,c,1)
imshow(A);
title("Original image")

d = size(A);
M = d(1);
N = d(2);

B = fft2(A);
C = fftshift(B);

subplot(r,c,2)
imshow(B);
title("Fourier Transformed Shifted Image")

D0 = 120;
n = 1;
H = zeros(d);

for u = 1:d(1)
    for v = 1:d(2)
        D = ((u - M/2)^2 + (v - N/2)^2)^0.5;
        H(u, v) = 1 / (1 + (D / D0)^(2*n));  % Butterworth filter equation
    end
end

subplot(r,c,3)
imshow(H);
str = sprintf("Butterworth Low Pass Filter (n=%d)", n);
title(str)

X = C.*H;
Y = abs(ifft2(X));

subplot(r,c,4)
imshow(Y);
title("Filtered Image")

...--------------------------

D0 = 120;
n = 5;
H = zeros(d);

for u = 1:d(1)
    for v = 1:d(2)
        D = ((u - M/2)^2 + (v - N/2)^2)^0.5;
        H(u, v) = 1 / (1 + (D / D0)^(2*n));  % Butterworth filter equation
    end
end

subplot(r,c,5)
imshow(H);
str = sprintf("Butterworth Low Pass Filter (n=%d)", n);
title(str)

X = C.*H;
Y = abs(ifft2(X));

subplot(r,c,6)
imshow(Y);
title("Filtered Image")
```

## Output
<span class="centerImg">![[lab10 output.png]]</span>
