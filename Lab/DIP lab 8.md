# Experiment 8
Feb 17, 2023

## Aim
Write a program to perform log transformation of an image.

## Source Code
```
clc;
close all;
clear;
A1 = imread('medical_images\3.png');
A2 = imread('medical_images\2.jpg');

B1 = im2gray(A1);
B2 = im2gray(A2);

C1 = uint8(log(double(B1)+1).*((255)/log10(256)));
C2 = uint8(log10(double(B2)+1).*((255)/log10(256)));

D1 = uint8((2.718.^(double(B1)).^(log(256)/255))-1);
D2 = uint8((10.^(double(B2)).^(log10(256)/255))-1);

subplot(2,3,1)
imshow(B1)
title('original image 1')

subplot(2,3,2)
imshow(C1)
title('log(image 1)')

subplot(2,3,3)
imshow(D1)
title('antilog(image 1)')

subplot(2,3,4)
imshow(B2)
title('original image 1')

subplot(2,3,5)
imshow(C2)
title('log10(image 2)')

subplot(2,3,6)
imshow(D2)
title('antilog10(image 2)')

function y=gray_level_slicing(x)
    y=x;
    for i=1:size(x,1)
        for j=1:size(x,2)
            if x(i,j)>200 || x(i,j)<100
                y(i,j)=0;
            else
                y(i,j)=255;
            end
        end
    end
end
```
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div>

## Output
![[lab8 output.png|800]]
