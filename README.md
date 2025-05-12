# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 
ALGORITHM DESCRIPTION:
In the rail fence cipher, the plaintext is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

## PROGRAM:

PROGRAM:
~~~
def rail_fence_encrypt(text, rails):
    fence, rail, step = [''] * rails, 0, 1
    for char in text:
        fence[rail] += char
        rail += step * (rail != 0 and rail != rails - 1 or -1)
    return ''.join(fence)

def rail_fence_decrypt(ciphertext, rails):
    pattern, rail, step = [0] * len(ciphertext), 0, 1
    for i in range(len(ciphertext)):
        pattern[i], rail = rail, rail + step * (rail != 0 and rail != rails - 1 or -1)
    result, fence = [''] * len(ciphertext), iter(ciphertext)
    for i in sorted(range(len(pattern)), key=lambda k: pattern[k]): result[i] = next(fence)
    return ''.join(result)

plaintext, rails = "SECURITYLABORATORY", 2
ciphertext, decrypted_text = rail_fence_encrypt(plaintext, rails), rail_fence_decrypt(rail_fence_encrypt(plaintext, rails), rails)
print(f"Rails: {rails}\nPlaintext: {plaintext}\nCiphertext: {ciphertext}\nDecrypted Text: {decrypted_text}")
~~~
## OUTPUT:
OUTPUT:
Enter a Secret Message wearediscovered
Enter number of rails 2
waeicvrderdsoee

![Screenshot 2025-03-19 092028](https://github.com/user-attachments/assets/8294b06a-d172-45a6-9af8-f9c711fbcc66)

## RESULT:
The program is executed successfully



