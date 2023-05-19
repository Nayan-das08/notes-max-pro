>%%Links: [[Lab Files]]%%

# Experiment 1
Jan 6, 2023

## Aim
To read and display images using `imread()` and `imshow()` functions.

## Source Code
```
clc;
close all;
A = imread('medical_images\1.png');
figure;
imshow(A)
title('image 1');

B = imread('medical_images\2.jpg');
figure;
imshow(B)
title('image 2');
```

## Output
![[Pasted image 20230419023256.png|500]]![[Pasted image 20230419023240.png|500]]