def print_hi(name):
    # Use a breakpoint in the code line below to debug your script.
    print(f'Hi, {name}')  # Press Ctrl+F8 to toggle the breakpoint.
    
if __name__ == '__main__':
    print_hi('Welcome to my repository')
#code for the project

def encrypt(plain_text, shift):
    encrypted_text = ""
    for char in plain_text:
        if char.isalpha():
            start = ord('a') if char.islower() else ord('A')
            encrypted_text += chr((ord(char) - start + shift) % 26 + start)
        else:
            encrypted_text += char
    return encrypted_text


def decrypt(ciphertext, shift):
    decrypted_text = ""
    for char in ciphertext:
        if char.isalpha():
            start = ord('a') if char.islower() else ord('A')
            decrypted_text += chr((ord(char) - start - shift) % 26 + start)
        else:
            decrypted_text += char
    return decrypted_text


# Main function to run the program
def main():
    def show_menu():
        print("\n Choose from Caesar Cipher Menu:")
        print("1. Encrypt a Message")
        print("2. Decrypt a Message")
        print("3. Return to the Menu")
        print("0. Exit")

    def msg_to_encrypt():
        message = input("Enter the message to encrypt: ")
        shift = int(input("Enter the shift value: "))
        print("Encrypted Message:", encrypt(message, shift))

    def msg_to_decrypt():
        message = input("Enter the message to decrypt: ")
        shift = int(input("Enter the shift value: "))
        print("Decrypted Message:", decrypt(message, shift))

    def return_to_menu():
        print("Returning to the menu...")

    # Menu choices and corresponding functions
    switch = {
        '0': lambda: print("Exiting the program."),
        '1': msg_to_encrypt,
        '2': msg_to_decrypt,
        '3': return_to_menu
    }

    while True:
        show_menu()
        choice = input("Enter your choice: ").strip()

        # Calling the corresponding function or print an error message
        action = switch.get(choice, lambda: print("Invalid choice! Please select a valid option."))
        action()

        if choice == '0':
            break  # end the program


if __name__ == "__main__":
    main()


