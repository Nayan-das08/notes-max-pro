# Experiment 16
Mar 24, 2023

## Aim
Write a program for smoothening of image using 3x3, 5x5, 7x7, 15x15 low pass filter.

## Source Code
```
clc;
clear all;
close all;

% Reading input image
I = imread('medical_images\3.png');

% Convert input image to grayscale
I_gray = rgb2gray(I);

% Display original image
figure(1);
subplot(2,3,1);
imshow(I_gray);
title('Original Image');

% Create different sizes of low pass filters
h_3 = ones(3,3)/9;
h_5 = ones(5,5)/25;
h_7 = ones(7,7)/49;
h_15 = ones(15,15)/225;

% Apply different filters on input image
I_3 = imfilter(I_gray, h_3);
I_5 = imfilter(I_gray, h_5);
I_7 = imfilter(I_gray, h_7);
I_15 = imfilter(I_gray, h_15);

% Display smoothened images
subplot(2,3,2);
imshow(I_3);
title('3x3 filter');

subplot(2,3,3);
imshow(I_5);
title('5x5 filter');

subplot(2,3,4);
imshow(I_7);
title('7x7 filter');

subplot(2,3,5);
imshow(I_15);
title('15x15 filter');
```
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div>

## Output
![[lab13 output.png|900]]
