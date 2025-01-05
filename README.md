# Pass-generate-
import random
import string

def generate_password(length=12, include_uppercase=True, include_numbers=True, include_special_chars=True):
    # Define character pools
    lower = string.ascii_lowercase
    upper = string.ascii_uppercase if include_uppercase else ''
    numbers = string.digits if include_numbers else ''
    special = string.punctuation if include_special_chars else ''
    
    # Combine pools into a full set
    all_characters = lower + upper + numbers + special
    
    # Ensure at least one character from each selected pool
    password = []
    if include_uppercase:
        password.append(random.choice(upper))
    if include_numbers:
        password.append(random.choice(numbers))
    if include_special_chars:
        password.append(random.choice(special))
    
    # Fill the rest of the password with random choices
    while len(password) < length:
        password.append(random.choice(all_characters))
    
    # Shuffle to ensure randomness
    random.shuffle(password)
    
    return ''.join(password)

# Example usage
password = generate_password(length=12)
print("Generated Password:", password)
