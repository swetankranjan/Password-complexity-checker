# Password-complexity-checker
import re

def check_password_strength(password):
    length_error = len(password) < 8
    digit_error = re.search(r"\d", password) is None
    uppercase_error = re.search(r"[A-Z]", password) is None
    lowercase_error = re.search(r"[a-z]", password) is None
    symbol_error = re.search(r"[!@#$%^&*()_+\-=\[\]{};':\"\\|,.<>\/?]", password) is None

    # Count the number of missing criteria
    errors = [length_error, digit_error, uppercase_error, lowercase_error, symbol_error]
    score = 5 - sum(errors)

    # Provide feedback
    if score == 5:
        return "Strong password!"
    elif score >= 3:
        return "Moderate password. Try adding more character types to improve it."
    else:
        return "Weak password. Consider making it longer and including uppercase, lowercase, numbers, and symbols."

# Example usage
password = input("Enter your password: ")
feedback = check_password_strength(password)
print(feedback)
