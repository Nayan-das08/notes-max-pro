# Experiment 7
Feb 10, 2023

## Aim
Write a program to display histogram of an image.

## Source Code
```
clc;
close all;
clear;
A1 = imread('medical_images\3.png');
A2 = imread('medical_images\2.jpg');

B1 = im2gray(A1);
B2 = im2gray(A2);

subplot(2,2,1)
imshow(B1)
title('original image 1')
subplot(2,2,2)
bar(hist(B1))
title('histogram 1')

subplot(2,2,3)
imshow(B2)
title('original image 2')
subplot(2,2,4)
bar(hist(B2))
title('histogram 2')

function [H1] = hist(x)
    H1 = zeros(1,255);
    for i = 1:size(x, 1)
        for j = 1:size(x, 2)
            intensity = x(i, j) + 1;
            H1(intensity) = H1(intensity) + 1;
        end
    end
    return
end
```

## Output
<span class="centerImg">![[lab7 output.png]]</span>