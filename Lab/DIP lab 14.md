>%%Links: [[Lab Files]]%%

# Experiment 14
Mar 10, 2023

## Aim
Write a program for Gaussian high pass filter.

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

sigma = 30;  % Standard deviation of the Gaussian distribution
H = zeros(d);

for u = 1:d(1)
    for v = 1:d(2)
        D = ((u - M/2)^2 + (v - N/2)^2)^0.5;
        H(u, v) = 1 - exp(-(D^2) / (2 * sigma^2));  % Gaussian filter equation
    end
end

subplot(r,c,3)
imshow(H);
str = sprintf("Gaussian High Pass Filter (sigma=%d)", sigma);
title(str)

X = C.*H;
Y = abs(ifft2(X));

subplot(r,c,4)
imshow(Y);
title("Filtered Image")

...--------------------------

sigma = 100;  % Standard deviation of the Gaussian distribution
H = zeros(d);

for u = 1:d(1)
    for v = 1:d(2)
        D = ((u - M/2)^2 + (v - N/2)^2)^0.5;
        H(u, v) = 1 - exp(-(D^2) / (2 * sigma^2));  % Gaussian filter equation
    end
end

subplot(r,c,5)
imshow(H);
str = sprintf("Gaussian High Pass Filter (sigma=%d)", sigma);
title(str)

X = C.*H;
Y = abs(ifft2(X));

subplot(r,c,6)
imshow(Y);
title("Filtered Image")
```

## Output
![[lab14 output.png|800]]
