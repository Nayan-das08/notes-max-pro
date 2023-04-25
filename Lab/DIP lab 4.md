# Experiment 4
Jan 20, 2023

## Aim
Write a program to perform grey level slicing with background.

## Source Code
```
clc;
close all;
clear;
A1 = imread('medical_images\3.png');
A2 = imread('medical_images\2.jpg');
B1 = im2gray(A1);
B2 = im2gray(A2);
C1 = gray_level_slicing(B1);
C2 = gray_level_slicing(B2);
subplot(2,2,1)
imshow(B1)
title('original image 1')
subplot(2,2,2)
imshow(C1)
title('grey level slicing with background 1')
subplot(2,2,3)
imshow(B2)
title('original image 2')
subplot(2,2,4)
imshow(C2)
title('grey level slicing with background 2')
function y=gray_level_slicing(x)
    y=x;
    for i=1:size(x,1)
        for j=1:size(x,2)
            if x(i,j)>200 || x(i,j)<100
                y(i,j)=0;
            else
                y(i,j)=x(i,j);
            end
        end
    end
end
```

## Output
![[lab4 output.png|630]]