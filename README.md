# 🚗 Smart Car Functions using Fuzzy Logic

## Project Overview
This project implements **Fuzzy Logic Control** for smart car functionalities based on various driving conditions.  
The system intelligently manages features like **window heating**, **air conditioning**, **lane keeping aid**, **navigation**, **seat cooling/heating**, and many others — based on inputs like **weather**, **road scenario**, **speed**, **temperature**, and **visibility**.

The goal is to enhance driver comfort, safety, and energy efficiency by automating car functionalities using **Fuzzy Inference Systems**.

---

## 🛠️ Techniques Used
- Fuzzy Logic (Fuzzy Membership Functions, Rules)
- NumPy (Numerical operations)
- scikit-fuzzy (Fuzzy logic control library)

---

## 📥 Input Variables (Antecedents)
- **Weather** (Clear, Snow, Rain, Fog)
- **Road Scenario** (City, Motorway, Rural)
- **Temperature** (Frost, Low, Normal, Warm)
- **Speed** (Stopped, Slow, Medium, Fast)
- **Visibility** (Free, Dark Limited)

---

## 📤 Output Variables (Consequents)
Smart functionalities that are either turned **ON** or **OFF** based on conditions:
- Window Heating (Front & Rear)
- Air Conditioning (AC)
- Lane Keeping Aid
- Suspension Adjustment
- Start-Stop System
- Parking Aid
- Camera Activation
- Fan Control
- Voice Assistance
- Seat Cooling / Heating
- Steering Wheel Heating
- Ambient Light
- Driving Modes
- Navigation System
- Sign Recognition Aided Driving
- Auto Driving Features
- Temperature Settings
- Air Recirculation
- Email Notifications
- Music Player

---

## 🧠 Fuzzy Membership Functions
- **Speed**:
  - Stopped, Slow, Medium, Fast
- **Weather**:
  - Clear, Snow, Rain, Fog
- **Road Scenario**:
  - City, Motorway, Rural
- **Temperature**:
  - Frost, Low, Normal, Warm
- **Visibility**:
  - Free, Dark Limited
- **Outputs**:
  - On / Off states for each car functionality

---

## 🔎 Libraries Used
- **NumPy**: For numerical operations
- **scikit-fuzzy (skfuzzy)**: For creating fuzzy variables, membership functions, and control rules

---

## 🚀 How It Works
1. Inputs like weather conditions, speed, road scenario, etc., are **fuzzified** using defined membership functions.
2. Based on fuzzy rules (to be created or extended), the system infers the best settings for different car features.
3. Outputs are **defuzzified** to decide whether to activate or deactivate various smart features.

---

## Example Code Snippet

```python
import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl

# Define fuzzy input variables
weather = ctrl.Antecedent(np.arange(0, 4, 1), 'weather')
speed = ctrl.Antecedent(np.arange(0, 150, 1), 'speed')

# Define fuzzy output variable
ac = ctrl.Consequent(np.arange(0, 2, 1), 'ac')

# Membership functions
speed['stopped'] = fuzz.trapmf(speed.universe, [0, 0, 2, 10])
weather['clear'] = fuzz.trapmf(weather.universe, [0, 0, 0.5, 1])

# Output states
ac['off'] = fuzz.trimf(ac.universe, [0, 0, 1])
ac['on'] = fuzz.trimf(ac.universe, [0, 1, 1])
