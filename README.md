1.pip install numpy

2.pip install numpy pip install matplotlib pip install scikit-fuzzy

3.pip install numpy pip install matplotlib pip install scikit-fuzzy

4.pip install numpy pip install matplotlib

5.pip install numpy pip install matplotlib

6.pip install numpy pip install matplotlib


1#operations
import numpy as np
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
U = np.array([1, 2, 3, 4, 5])
print("Universe of Discourse (U):", U, "\n")
A = np.array([1.0, 0.8, 0.4, 0.1, 0.0])
B = np.array([0.0, 0.1, 0.3, 0.7, 1.0])

print("Original Sets")
print("Fuzzy Set A:", A)
print("Fuzzy Set B:", B, "\n")
A_OR_B = fuzzy_union_or(A, B)
print("Fuzzy UNION (A OR B):")
print(A_OR_B, "\n")

A_AND_B = fuzzy_intersection_and(A, B)
print("Fuzzy INTERSECTION (A AND B):")
print(A_AND_B, "\n")

NOT_A = fuzzy_complement_not(A)
print("Fuzzy COMPLEMENT (NOT A):")
print(NOT_A, "\n")

NOT_B = fuzzy_complement_not(B)
print("Fuzzy COMPLEMENT (NOT B):")
print(NOT_B)
