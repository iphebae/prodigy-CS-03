# prodigy-CS-03
PASSWORD COMPLEXITY CHECKER involves developing a password strength assessment tool that evaluates a password based on various security criteria


import re

def check_password_strength(password):
    strength = 0
    feedback = []
    
    # Criteria Checks
    if len(password) >= 8:
        strength += 1
    else:
        feedback.append("Password should be at least 8 characters long.")
    
    if re.search(r"[A-Z]", password):
        strength += 1
    else:
        feedback.append("Include at least one uppercase letter.")
    
    if re.search(r"[a-z]", password):
        strength += 1
    else:
        feedback.append("Include at least one lowercase letter.")
    
    if re.search(r"\d", password):
        strength += 1
    else:
        feedback.append("Include at least one number.")
    
    if re.search(r"[@$!%*?&]", password):
        strength += 1
    else:
        feedback.append("Include at least one special character (@$!%*?&).")
    
    # Strength Rating
    if strength == 5:
        return "Strong password ✅", feedback
    elif strength >= 3:
        return "Moderate password ⚠️", feedback
    else:
        return "Weak password ❌", feedback

# Example Usage
if __name__ == "__main__":
    user_password = input("Enter a password to check its strength: ")
    strength, suggestions = check_password_strength(user_password)
    print(f"\nPassword Strength: {strength}")
    if suggestions:
        print("Suggestions to improve:")
        for tip in suggestions:
            print(f"- {tip}")
