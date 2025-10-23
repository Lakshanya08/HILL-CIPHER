# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM:
```
def hill_cipher_encrypt(message, key):
    message = message.upper().replace(" ", "")
    key_size = len(key)
    while len(message) % key_size != 0:
        message += 'X'

    ciphertext = ""

    for i in range(0, len(message), key_size):
        block = message[i:i + key_size]
        block_vector = [ord(c) - 65 for c in block]
        result = [0] * key_size
        for r in range(key_size):
            for c in range(key_size):
                result[r] += key[r][c] * block_vector[c]
            result[r] %= 26
        ciphertext += ''.join(chr(num + 65) for num in result)
    return ciphertext
message = input("Enter message: ")

key = [[3, 3],
       [2, 5]]

encrypted = hill_cipher_encrypt(message, key)
print("Encrypted text:", encrypted)
```

## OUTPUT:
<img width="275" height="55" alt="image" src="https://github.com/user-attachments/assets/77fc2ab0-153e-44dc-8cb4-385b9216003a" />

## RESULT:
Thus the implementation of hill cipher had been executed successfully.
