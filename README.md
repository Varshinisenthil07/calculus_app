import sympy as sp

# Define the complex variable and function
z = sp.symbols('z')
f = 1 / (z**2 + 1)

# Step 1: Find the poles (where denominator is zero)
denominator = sp.denom(f)  # Get denominator
poles = sp.solve(denominator, z)  # Solve for poles

# Step 2: Classify the poles by checking their multiplicity
pole_classification = {}
for pole in poles:
    order = sp.limit((z - pole) * f, z, pole)
    pole_classification[pole] = "Simple Pole" if sp.simplify(order) != 0 else "Multiple Pole"

# Step 3: Determine the order of the function (based on highest power of z in denominator)
order_of_function = sp.degree(denominator)

# Display results
print("Poles of f(z):", poles)
for pole, classification in pole_classification.items():
    print(f"Pole at z = {pole}: {classification}")
print("Order of the function:", order_of_function)
