def vigenere_encrypt(plaintext, key):
    key = key * (len(plaintext) // len(key)) + key[:len(plaintext) % len(key)]
    ciphertext = ""

    for i in range(len(plaintext)):
        char_plaintext = plaintext[i]
        char_key = key[i]
        
        encrypted_char = str((ord(char_plaintext) + ord(char_key)) % 256)
        ciphertext += encrypted_char + " "

    return ciphertext.strip()

def vigenere_decrypt(ciphertext, key):
    key = key * (len(ciphertext) // len(key)) + key[:len(ciphertext) % len(key)]
    decrypted_text = ""
    
    cipher_chars = ciphertext.split()

    for i in range(len(cipher_chars)):
        cipher_char = int(cipher_chars[i])
        char_key = key[i]
        
        decrypted_char = chr((cipher_char - ord(char_key)) % 256)
        decrypted_text += decrypted_char

    return decrypted_text

while True:
    choice = input("Pilih mode (enkripsi/dekripsi/exit): ").lower()

    if choice == "exit":
        print("Program keluar. Terima kasih!")
        break

    elif choice == "enkripsi":
        plaintext = input("Masukkan plaintext: ")
        key = input("Masukkan kunci: ")
        
        encrypted_text = vigenere_encrypt(plaintext, key)
        print("\nEnkripsi Text:", encrypted_text)

        continue_to_decrypt = input("Apakah Anda ingin melanjutkan ke dekripsi? (y/n): ").lower()
        if continue_to_decrypt != "y":
            print("Program keluar. Terima kasih!")
            break

    elif choice == "dekripsi":
        ciphertext = input("Masukkan ciphertext: ")
        key = input("Masukkan kunci: ")
        
        decrypted_text = vigenere_decrypt(ciphertext, key)
        print("Dekripsi Text:", decrypted_text)

    else:
        print("Pilihan tidak valid. Silakan pilih 'enkripsi', 'dekripsi', atau 'exit'.")
