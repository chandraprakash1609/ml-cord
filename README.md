def find_s_algorithm(training_data):
    # Initialize the hypothesis with the first positive example
    for example in training_data:
        if example[-1].lower() == "yes":
            hypothesis = example[:-1]
            break
    else:
        return None  # No positive example found

    # Iterate over the rest of the training data
    for example in training_data:
        if example[-1].lower() == "yes":  # Only consider positive examples
            for i in range(len(hypothesis)):
                if hypothesis[i] != example[i]:
                    hypothesis[i] = "?"  # Generalize the attribute
    return hypothesis

# Example dataset
# Format: [attribute1, attribute2, ..., attributeN, 'yes'/'no']
training_data = [
    ['Sunny', 'Warm', 'Normal', 'Strong', 'Warm', 'Same', 'Yes'],
    ['Sunny', 'Warm', 'High', 'Strong', 'Warm', 'Same', 'Yes'],
    ['Rainy', 'Cold', 'High', 'Strong', 'Warm', 'Change', 'No'],
    ['Sunny', 'Warm', 'High', 'Strong', 'Cool', 'Change', 'Yes']
]

# Run FIND-S
final_hypothesis = find_s_algorithm(training_data)

print("Final Hypothesis:", final_hypothesis)
