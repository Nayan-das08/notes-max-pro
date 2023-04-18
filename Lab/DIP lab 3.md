# Experiment 3
Jan 13, 2023

## Aim
Write a program to perform thresholding of an input image.

## Source Code
```
clc;
close all;
clear;
A1 = imread('medical_images\3.png');
A2 = imread('medical_images\2.jpg');

B1 = im2gray(A1);
B2 = im2gray(A2);

C1 = threshold(B1);
C2 = threshold(B2);

subplot(2,2,1)
imshow(B1)
title('original image 1')
subplot(2,2,2)
imshow(C1)
title('threshold image 1')
subplot(2,2,3)
imshow(B2)
title('original image 2')
subplot(2,2,4)
imshow(C2)
title('threshold image 2')

function y=threshold(x)
    y=x;
    for i=1:size(x,1)
        for j=1:size(x,2)
            if x(i,j)<128
                %y(i,j)=x(i,j);
                y(i,j)=0;
            else
                %y(i,j)=255-x(i,j);
                y(i,j)=255;
            end
        end
    end
end
```

## Output
<span class="centerImg">![[lab3 output.png]]</span>