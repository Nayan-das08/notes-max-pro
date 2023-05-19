>%%Links: [[Lab Files]]%%

# Experiment 10
Feb 24, 2023

## Aim
Write a program for Ideal high pass filter.

## Source Code
```
clc;
close all;
clear;
A = imread("medical_images\1.png");
A = im2gray(A);

r = 2;
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
H = zeros(d);

for u=1:1:d(1)
    for v=1:1:d(2)
        D = ((u-M/2)^2 + (v-N/2)^2)^0.5;
        if D<D0
            H(u,v) = 0;
        else
            H(u,v) = 1;
        end
    end
end

subplot(r,c,3)
imshow(H);
title("Ideal High Pass Filter")

X = C.*H;
Y = abs(ifft2(X));

subplot(r,c,4)
imshow(Y);
title("Filtered Image")
```
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div>

## Output
![[lab12 output 1.png|800]]