# Prodigy-InfoTech-task-01
encrypt and decrypt text using the Caesar Cipher algorithm
This program allows the user to choose between encryption and decryption, input a message, and specify the shift value. Then, it performs the chosen operation and displays the result.

def caesar_cipher(text, shift, mode):
    result = ''
    for char in text:
        if char.isalpha():
            if char.isupper():
                if mode == 'encrypt':
                    result += chr((ord(char) + shift - 65) % 26 + 65)
                elif mode == 'decrypt':
                    result += chr((ord(char) - shift - 65) % 26 + 65)
            elif char.islower():
                if mode == 'encrypt':
                    result += chr((ord(char) + shift - 97) % 26 + 97)
                elif mode == 'decrypt':
                    result += chr((ord(char) - shift - 97) % 26 + 97)
        else:
            result += char
    return result

def main():
    choice = input("Do you want to encrypt or decrypt? (encrypt/decrypt): ").lower()
    if choice not in ['encrypt', 'decrypt']:
        print("Invalid choice. Please enter 'encrypt' or 'decrypt'.")
        return

    message = input("Enter your message: ")
    shift = int(input("Enter the shift value: "))

    if choice == 'encrypt':
        encrypted_message = caesar_cipher(message, shift, 'encrypt')
        print("Encrypted message:", encrypted_message)
    else:
        decrypted_message = caesar_cipher(message, shift, 'decrypt')
        print("Decrypted message:", decrypted_message)

if __name__ == "__main__":
    main()
