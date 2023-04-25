# Experiment 15
Mar 17, 2023

## Aim
Write a program for generating noise PDFs for uniform, Rayleigh and Exponential Noise.

## Source Code
```
% Uniform noise
u_min = 0;  % Minimum value
u_max = 1;  % Maximum value
u_pdf = @(x) (x >= u_min & x <= u_max) ./ (u_max - u_min);

% Rayleigh noise
r_sigma = 1;  % Scale parameter
r_pdf = @(x) (x >= 0) .* (x / r_sigma^2) .* exp(-x.^2 / (2 * r_sigma^2));

% Exponential noise
e_lambda = 1;  % Rate parameter
e_pdf = @(x) (x >= 0) .* e_lambda .* exp(-e_lambda * x);

% Plot the PDFs
x = linspace(0, 3, 1000);
figure;
plot(x, u_pdf(x), 'LineWidth', 2);
hold on;
plot(x, r_pdf(x), 'LineWidth', 2);
plot(x, e_pdf(x), 'LineWidth', 2);
legend('Uniform', 'Rayleigh', 'Exponential');
xlabel('x');
ylabel('Probability Density');
```

## Output
<span class="centerImg">![[lab12 output.png]]</span>
