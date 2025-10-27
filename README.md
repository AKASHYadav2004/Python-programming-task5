# Python-programming-task5
import re

def check_password_strength(password):
    """
    Check the strength of a password.

    Args:
        password (str): The password to check.

    Returns:
        str: "Strong" if the password meets all criteria, "Weak" otherwise.
    """
    # Define the regex patterns
    patterns = {
        "min_length": r".{8,}",
        "has_number": r"\d",
        "has_special_char": r"[^a-zA-Z0-9]",
        "has_uppercase": r"[A-Z]"
    }

    # Check each pattern
    checks = [
        bool(re.search(patterns["min_length"], password)),
        bool(re.search(patterns["has_number"], password)),
        bool(re.search(patterns["has_special_char"], password)),
        bool(re.search(patterns["has_uppercase"], password))
    ]

    # Determine the password strength
    if all(checks):
        return "Strong"
    else:
        return "Weak"

def main():
    # Ask the user to input a password
    password = input("Enter a password: ")

    # Check the password strength
    strength = check_password_strength(password)

    # Print the result
    print(f"Password strength: {strength}")

if __name__ == "__main__":
    main()
    
