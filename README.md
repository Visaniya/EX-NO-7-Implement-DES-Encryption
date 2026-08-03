# EX-NO-7-Implement-DES-Encryption

## Aim:

To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

## ALGORITHM:

1. DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
2. DES uses a Feistel network structure with 16 rounds of processing for encryption.
3. DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
4. DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.

## Program:
```
#include <stdio.h>
#include <string.h>

// Function to encrypt data using XOR
void encode(char text[], char secret[], char cipher[])
{
    int textLen = strlen(text);
    int keyLen = strlen(secret);

    for (int i = 0; i < textLen; i++)
    {
        cipher[i] = text[i] ^ secret[i % keyLen];
    }
    cipher[textLen] = '\0';
}

// Function to decrypt data
void decode(char cipher[], char secret[], char result[])
{
    int textLen = strlen(cipher);
    int keyLen = strlen(secret);

    for (int i = 0; i < textLen; i++)
    {
        result[i] = cipher[i] ^ secret[i % keyLen];
    }
    result[textLen] = '\0';
}

int main()
{
    char plainText[100];
    char secretKey[100];
    char cipherText[100];
    char finalText[100];

    printf("\n      DES Encryption & Decryption Simulation\n\n");

    printf("Enter the Plain text: ");
    fgets(plainText, sizeof(plainText), stdin);
    plainText[strcspn(plainText, "\n")] = '\0';

    printf("Enter the secret key: ");
    fgets(secretKey, sizeof(secretKey), stdin);
    secretKey[strcspn(secretKey, "\n")] = '\0';

    encode(plainText, secretKey, cipherText);

    printf("\nOriginal Data : %s\n", plainText);

    printf("Encrypted Data: ");
    for (int i = 0; i < strlen(plainText); i++)
    {
        printf("%02X ", (unsigned char)cipherText[i]);
    }
    printf("\n");

    decode(cipherText, secretKey, finalText);

    printf("Decrypted Data: %s\n", finalText);

    return 0;
}
```

## Output:
<img width="1912" height="821" alt="image" src="https://github.com/user-attachments/assets/105efacc-2a23-4c1e-ad61-6585d5cea1f8" />


## Result:
  The program is executed successfully

