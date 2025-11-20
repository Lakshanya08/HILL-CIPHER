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
def char_to_num(c):
    return ord(c) - 65

def num_to_char(n):
    return chr(n + 65)

def multiply(mat, vec):
    return [
        (mat[0][0]*vec[0] + mat[0][1]*vec[1]) % 26,
        (mat[1][0]*vec[0] + mat[1][1]*vec[1]) % 26
    ]

def hill_encrypt(plain, key):
    plain = plain.replace(" ", "").upper()
    if len(plain) % 2 == 1:
        plain += "X"

    cipher = ""
    for i in range(0, len(plain), 2):
        p = [char_to_num(plain[i]), char_to_num(plain[i+1])]
        c = multiply(key, p)
        cipher += num_to_char(c[0]) + num_to_char(c[1])
    return cipher

def inverse_key(key):
    det = (key[0][0]*key[1][1] - key[0][1]*key[1][0]) % 26

    for x in range(26):
        if (det * x) % 26 == 1:
            det_inv = x
            break

    inv = [
        [( key[1][1] * det_inv) % 26, (-key[0][1] * det_inv) % 26],
        [(-key[1][0] * det_inv) % 26, ( key[0][0] * det_inv) % 26]
    ]
    return inv

def hill_decrypt(cipher, key):
    inv_key = inverse_key(key)
    cipher = cipher.upper()
    plain = ""
    for i in range(0, len(cipher), 2):
        c = [char_to_num(cipher[i]), char_to_num(cipher[i+1])]
        p = multiply(inv_key, c)
        plain += num_to_char(p[0]) + num_to_char(p[1])
    return plain

key = [[3, 3],
       [2, 5]]

plaintext = "HELLO"
cipher = hill_encrypt(plaintext, key)
decrypted = hill_decrypt(cipher, key)

print("Plaintext :", plaintext)
print("Ciphertext:", cipher)
print("Decrypted :", decrypted)
```

## OUTPUT:
<img width="411" height="80" alt="image" src="https://github.com/user-attachments/assets/0d893b8c-bc61-4566-a6df-a6c138d89c9b" />

## RESULT:
Thus the implementation of hill cipher had been executed successfully.
