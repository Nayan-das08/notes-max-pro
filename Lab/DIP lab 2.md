# Experiment 2
Jan 6, 2023

## Aim
Write a program to display the negative of a digital image.

## Source Code
```
clc;
close all;
clear;
A1 = imread('medical_images\3.png');
A2 = imread('medical_images\2.jpg');
B1 = im2gray(A1);
B2 = im2gray(A2);
C1 = negative(B1);
C2 = negative(B2);
subplot(2,2,1)
imshow(B1)
title('original image 1')
subplot(2,2,2)
imshow(C1)
title('negative image 1')
subplot(2,2,3)
imshow(B2)
title('original image 2')
subplot(2,2,4)
imshow(C2)
title('negative image 2')
function y=negative(x)
    y=x;
    for i=1:size(x,1)
        for j=1:size(x,2)
            y(i,j)=255-x(i,j);
        end
    end
end
```

## Output
![[lab2 output.png|700]]