# Experiment 6
Feb 3, 2023

## Aim
Write a program to perform bit plane slicing.

## Source Code
```
clc;
close all;
clear;
A = imread('medical_images\3.png');
...A2 = imread('medical_images\2.jpg');

B = im2gray(A);
...B2 = im2gray(A2);

x=2;
y=5;

A0 = double(B);
A1 = mod(A0,2);%Least Significant Layer
A2 = mod(floor(A0/2),2);
A3 = mod(floor(A0/4),2);
A4 = mod(floor(A0/8),2);
A5 = mod(floor(A0/16),2);
A6 = mod(floor(A0/32),2);
A7 = mod(floor(A0/64),2);
A8 = mod(floor(A0/128),2);%Most Significant Layer
Image = (2*(2*(2*(2*(2*(2*(2*A8+A7)+A6)+A5)+A4)+A3)+A2)+A1);

subplot(x,y,1);
imshow(B);
title('Original Image');

subplot(x,y,2);
imshow(uint8(256*A8));
title('1st Plane');

subplot(x,y,3);
imshow(uint8(256*A7));
title('2nd Plane');

subplot(x,y,4);
imshow(uint8(256*A6));
title('3rd Plane');

subplot(x,y,5);
imshow(uint8(256*A5));
title('4th Plane');

subplot(x,y,6);
imshow(uint8(256*A4));
title('5th Plane');

subplot(x,y,7);
imshow(uint8(256*A3));
title('6th Plane');

subplot(x,y,8);
imshow(uint8(256*A2));
title('7th Plane');

subplot(x,y,9);
imshow(uint8(256*A1));
title('8th Plane');

subplot(x,y,10);
imshow(uint8(Image));
title('Combined Image');
```

## Output
<span class="centerImg">![[lab6 output.png]]</span>