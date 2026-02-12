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

