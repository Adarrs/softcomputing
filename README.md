1.pip install numpy

2.pip install numpy pip install matplotlib pip install scikit-fuzzy

3.pip install numpy pip install matplotlib pip install scikit-fuzzy

4.pip install numpy pip install matplotlib

5.pip install numpy pip install matplotlib

6.pip install numpy pip install matplotlib



1.import numpy as np

# -----------------------------
# Fuzzy Operations
# -----------------------------

def fuzzy_union_or(A, B):
    if len(A) != len(B):
        raise ValueError("Fuzzy sets must have same length")
    return np.maximum(A, B)

def fuzzy_intersection_and(A, B):
    if len(A) != len(B):
        raise ValueError("Fuzzy sets must have same length")
    return np.minimum(A, B)

def fuzzy_complement_not(A):
    return 1 - A

# -----------------------------
# Universe of Discourse
# -----------------------------

U = np.array([1, 2, 3, 4, 5])
print("Universe of Discourse (U):", U)

# Fuzzy Sets
A = np.array([1.0, 0.8, 0.4, 0.1, 0.0])
B = np.array([0.0, 0.1, 0.3, 0.7, 1.0])

print("\nOriginal Sets")
print("Fuzzy Set A:", A)
print("Fuzzy Set B:", B)

# -----------------------------
# Operations
# -----------------------------

A_OR_B = fuzzy_union_or(A, B)
print("\nFuzzy UNION (A OR B):")
print(A_OR_B)

A_AND_B = fuzzy_intersection_and(A, B)
print("\nFuzzy INTERSECTION (A AND B):")
print(A_AND_B)

NOT_A = fuzzy_complement_not(A)
print("\nFuzzy COMPLEMENT (NOT A):")
print(NOT_A)

NOT_B = fuzzy_complement_not(B)
print("\nFuzzy COMPLEMENT (NOT B):")
print(NOT_B)

2.import numpy as np
import skfuzzy as fuzz
from skfuzzy import control as ctrl
import matplotlib.pyplot as plt

# -----------------------------
# Define Inputs (Antecedents) and Output (Consequent)
# -----------------------------

service = ctrl.Antecedent(np.arange(0, 11, 1), 'service')
food = ctrl.Antecedent(np.arange(0, 11, 1), 'food')
tip = ctrl.Consequent(np.arange(0, 26, 1), 'tip')

# -----------------------------
# Membership Functions
# -----------------------------

service['poor'] = fuzz.trimf(service.universe, [0, 0, 5])
service['acceptable'] = fuzz.trimf(service.universe, [0, 5, 10])
service['excellent'] = fuzz.trimf(service.universe, [5, 10, 10])

food['bad'] = fuzz.trapmf(food.universe, [0, 0, 1, 3])
food['decent'] = fuzz.trimf(food.universe, [1, 5, 9])
food['great'] = fuzz.trapmf(food.universe, [7, 9, 10, 10])

tip['low'] = fuzz.trimf(tip.universe, [0, 0, 13])
tip['medium'] = fuzz.trimf(tip.universe, [0, 13, 25])
tip['high'] = fuzz.trimf(tip.universe, [13, 25, 25])

# -----------------------------
# Rules
# -----------------------------

rule1 = ctrl.Rule(service['poor'] | food['bad'], tip['low'])
rule2 = ctrl.Rule(service['acceptable'] & food['decent'], tip['medium'])
rule3 = ctrl.Rule(service['excellent'] & food['great'], tip['high'])
rule4 = ctrl.Rule(food['decent'] & service['poor'], tip['medium'])

# -----------------------------
# Control System
# -----------------------------

tip_control = ctrl.ControlSystem([rule1, rule2, rule3, rule4])
tipping = ctrl.ControlSystemSimulation(tip_control)

# -----------------------------
# Example 1
# -----------------------------

tipping.input['service'] = 6.5
tipping.input['food'] = 9.8
tipping.compute()

print("Service Rating: 6.5/10")
print("Food Rating: 9.8/10")
print(f"Recommended Tip: {tipping.output['tip']:.2f}%")

# Visualize Result
tip.view(sim=tipping)
plt.show()

# -----------------------------
# Example 2
# -----------------------------

print("\n--- Example 2 ---")
tipping.input['service'] = 2
tipping.input['food'] = 3
tipping.compute()
print(f"Recommended Tip: {tipping.output['tip']:.2f}%")


