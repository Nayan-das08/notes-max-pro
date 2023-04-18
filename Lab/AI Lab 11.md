---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 11
Apr 6, 2023

## Objective
To study about Fuzzy Scikit Libraries

## Theory
Fuzzy logic is a branch of mathematics that deals with reasoning that is approximate rather than fixed and exact. It is used in various applications, such as control systems, decision making, and data analysis, to deal with uncertainty and imprecision.

Scikit-fuzzy is a fuzzy logic toolkit for Python that provides a comprehensive set of tools for fuzzy control, fuzzy reasoning, and fuzzy analysis. It is built on top of the SciPy and NumPy libraries and provides a user-friendly interface for working with fuzzy logic.

In this experiment, we will use the scikit-fuzzy library to implement a fuzzy logic system to control the speed of a fan. We will use a simple set of rules to adjust the speed of the fan based on the temperature and humidity of the room.

---
## Source Code
```
# To get started, we need to install the scikit-fuzzy library. We can do this using pip:
!pip install scikit-fuzzy
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl

# Create input variables
temperature = ctrl.Antecedent(np.arange(0, 101, 1), 'temperature')
humidity = ctrl.Antecedent(np.arange(0, 101, 1), 'humidity')

# Create output variable
speed = ctrl.Consequent(np.arange(0, 101, 1), 'speed')

# Define fuzzy sets for input variables
temperature['cold'] = fuzz.trimf(temperature.universe, [0, 0, 50])
temperature['warm'] = fuzz.trimf(temperature.universe, [0, 50, 100])
temperature['hot'] = fuzz.trimf(temperature.universe, [50, 100, 100])
humidity['low'] = fuzz.trimf(humidity.universe, [0, 0, 50])
humidity['medium'] = fuzz.trimf(humidity.universe, [0, 50, 100])
humidity['high'] = fuzz.trimf(humidity.universe, [50, 100, 100])

# Define fuzzy sets for output variable
speed['low'] = fuzz.trimf(speed.universe, [0, 0, 50])
speed['medium'] = fuzz.trimf(speed.universe, [0, 50, 100])
speed['high'] = fuzz.trimf(speed.universe, [50, 100, 100])

# Define rules
rule1 = ctrl.Rule(temperature['cold'] & humidity['low'], speed['low'])
rule2 = ctrl.Rule(temperature['cold'] & humidity['medium'], speed['medium'])
rule3 = ctrl.Rule(temperature['cold'] & humidity['high'], speed['medium'])
rule4 = ctrl.Rule(temperature['warm'] & humidity['low'], speed['medium'])
rule5 = ctrl.Rule(temperature['warm'] & humidity['medium'], speed['medium'])
rule6 = ctrl.Rule(temperature['warm'] & humidity['high'], speed['high'])
rule7 = ctrl.Rule(temperature['hot'] & humidity['low'], speed['medium'])
rule8 = ctrl.Rule(temperature['hot'] & humidity['medium'], speed['high'])
rule9 = ctrl.Rule(temperature['hot'] & humidity['high'], speed['high'])

# Create control system
fan_ctrl = ctrl.ControlSystem([rule1, rule2, rule3, rule4, rule5, rule6, rule7, rule8, rule9])
fan_speed = ctrl.ControlSystemSimulation(fan_ctrl)

# Set input values
fan_speed.input['temperature'] = 70
fan_speed.input['humidity'] = 60

# Compute result
fan_speed.compute()

# Print result
print(fan_speed.output['speed'])
speed.view(sim=fan_speed)
```

---
## Output
<span class="centerImg">![[Pasted image 20230413100458.png|600]]</span>