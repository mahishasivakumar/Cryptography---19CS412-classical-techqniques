# Cryptography---19CS412-classical-techqniques


# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To develop a simple C program to implement Caeser Cipher.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <string.h>

int main()
 {
    int key;
    char s[1000];

    printf("Enter a plaintext to encrypt:\n");
    fgets(s, sizeof(s), stdin);
    printf("Enter key:\n");
    scanf("%d", &key);

    int n = strlen(s);

    for (int i = 0; i < n; i++) 
    {
        char c = s[i];
        if (c >= 'a' && c <= 'z') 
        {
            s[i] = 'a' + (c - 'a' + key) % 26;
        }
        else if (c >= 'A' && c <= 'Z')
        {
            s[i] = 'A' + (c - 'A' + key) % 26;
        }
    }
    printf("Encrypted message: %s\n", s);

    for (int i = 0; i < n; i++)
    {
        char c = s[i];
        if (c >= 'a' && c <= 'z') 
        {
            s[i] = 'a' + (c - 'a' - key + 26) % 26; 
        }
        else if (c >= 'A' && c <= 'Z')
        {
            s[i] = 'A' + (c - 'A' - key + 26) % 26; 
        }
    }
    printf("Decrypted message: %s\n", s);

    return 0;
}
```

## OUTPUT:
![image](https://github.com/mahishasivakumar/Cryptography---19CS412-classical-techqniques/assets/119559812/e5e1473a-15a4-47d5-9622-7713575e6dc5)

## RESULT:
The program is executed successfully

---------------------------------

# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To develop a simple C program to implement PlayFair Cipher.

## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <ctype.h>

#define SIZE 5

int main() 
{
    char key[SIZE * SIZE];
    char plaintext[100];
    char ciphertext[100];
    char keyMatrix[SIZE][SIZE];

    printf("Enter the key: ");
    scanf("%s", key);

    int k = 0;
    char alphabet[26] = "ABCDEFGHIKLMNOPQRSTUVWXYZ";
    for (int i = 0; i < SIZE; ++i)
    {
        for (int j = 0; j < SIZE; ++j) 
        {
            if (k < 25) 
            {
                keyMatrix[i][j] = key[k++];
            } 
            else 
            {
                keyMatrix[i][j] = alphabet[k - 25];
            }
        }
    }

    printf("Enter plaintext: ");
    scanf("%s", plaintext);

    k = 0;
    while (plaintext[k] != '\0')
    {
        char a = plaintext[k++];
        char b = plaintext[k++];

        int rowA, colA, rowB, colB;
        for (int i = 0; i < SIZE; ++i)
        {
            for (int j = 0; j < SIZE; ++j)
            {
                if (keyMatrix[i][j] == a)
                {
                    rowA = i;
                    colA = j;
                }
                if (keyMatrix[i][j] == b)
                {
                    rowB = i;
                    colB = j;
                }
            }
        }

        if (rowA == rowB)
        {
            ciphertext[k - 2] = keyMatrix[rowA][(colA + 1) % SIZE];
            ciphertext[k - 1] = keyMatrix[rowB][(colB + 1) % SIZE];
        } 
        else if (colA == colB)
        {
            ciphertext[k - 2] = keyMatrix[(rowA + 1) % SIZE][colA];
            ciphertext[k - 1] = keyMatrix[(rowB + 1) % SIZE][colB];
        } 
        else 
        {
            ciphertext[k - 2] = keyMatrix[rowA][colB];
            ciphertext[k - 1] = keyMatrix[rowB][colA];
        }
    }

    ciphertext[k] = '\0';

    printf("Ciphertext: %s\n", ciphertext);

    return 0;
}
```
## OUTPUT:
![image](https://github.com/mahishasivakumar/Cryptography---19CS412-classical-techqniques/assets/119559812/c486c951-98e5-4c17-b415-11505179f6fe)

## RESULT:
The program is executed successfully


---------------------------

# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>

int main() 
{
    unsigned int key[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}};
    unsigned int inverseKey[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};

    char msg[4];
    unsigned int enc[3] = {0}, dec[3] = {0};

    printf("Enter plain text: ");
    scanf("%3s", msg);

    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            enc[i] += key[i][j] * (msg[j] - 'A') % 26;

    printf("Encrypted Cipher Text: %c%c%c\n", enc[0] % 26 + 'A', enc[1] % 26 + 'A', enc[2] % 26 + 'A');

    for (int i = 0; i < 3; i++)
        for (int j = 0; j < 3; j++)
            dec[i] += inverseKey[i][j] * enc[j] % 26;

    printf("Decrypted Cipher Text: %c%c%c\n", dec[0] % 26 + 'A', dec[1] % 26 + 'A', dec[2] % 26 + 'A');

    return 0;
}
```
## OUTPUT:
![image](https://github.com/mahishasivakumar/Cryptography---19CS412-classical-techqniques/assets/119559812/c9b9f601-b2ac-4e63-876a-965351168da5)

## RESULT:
The program is executed successfully

-------------------------------------------------

# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple C program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define MAX_LENGTH 100

int main() 
{
    char input[MAX_LENGTH];
    char key[MAX_LENGTH];
    char result[MAX_LENGTH];

    printf("Enter the text to encrypt: ");
    fgets(input, MAX_LENGTH, stdin);
    input[strcspn(input, "\n")] = '\0'; 

    printf("Enter the key: ");
    fgets(key, MAX_LENGTH, stdin);
    key[strcspn(key, "\n")] = '\0'; 

    int inputLength = strlen(input);
    int keyLength = strlen(key);

    for (int i = 0, j = 0; i < inputLength; ++i) 
    {
        char currentChar = input[i];

        if (isalpha(currentChar))
        {
            int shift = toupper(key[j % keyLength]) - 'A';
            int base = isupper(currentChar) ? 'A' : 'a';

            result[i] = ((currentChar - base + shift + 26) % 26) + base;
            ++j;
        }
        else
        {
            result[i] = currentChar;
        }
    }

    result[inputLength] = '\0';
    printf("Encrypted text: %s\n", result);

    for (int i = 0, j = 0; i < inputLength; ++i) 
    {
        char currentChar = result[i];

        if (isalpha(currentChar)) 
        {
            int shift = toupper(key[j % keyLength]) - 'A';
            int base = isupper(currentChar) ? 'A' : 'a';

            result[i] = ((currentChar - base - shift + 26) % 26) + base;
            ++j;
        }
    }

    result[inputLength] = '\0';
    printf("Decrypted text: %s\n", result);

    return 0;
}
```

## OUTPUT:
![image](https://github.com/mahishasivakumar/Cryptography---19CS412-classical-techqniques/assets/119559812/ca304862-744a-4d28-9c7c-e3d8fcb15c65)


## RESULT:
The program is executed successfully

-----------------------------------------------------------------------

# Rail Fence Cipher
Rail Fence Cipher using with different key values

# AIM:

To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```

#include<stdio.h>
#include<conio.h>
#include<string.h>

int main()
{
    int i, j, k, l;
    char a[20], c[20], d[20];

    printf("\n\t\t RAIL FENCE TECHNIQUE");
    printf("\n\nEnter the input string : ");
    gets(a);
    l = strlen(a);

    for(i = 0, j = 0; i < l; i++)
    {
        if(i % 2 == 0)
            c[j++] = a[i];
    }
    for(i = 0; i < l; i++)
    {
        if(i % 2 == 1)
            c[j++] = a[i];
    }
    c[j] = '\0';

    printf("\nCipher text after applying rail fence :");
    printf("%s", c);

    if(l % 2 == 0)
        k = l / 2;
    else
        k = (l / 2) + 1;

    for(i = 0, j = 0; i < k; i++)
    {
        d[j] = c[i];
        j = j + 2;
    }
    for(i = k, j = 1; i < l; i++)
    {
        d[j] = c[i];
        j = j + 2;
    }
    d[l] = '\0';

    printf("\nText after decryption : ");
    printf("%s", d);

    return 0;
}
```

## OUTPUT:
![image](https://github.com/mahishasivakumar/Cryptography---19CS412-classical-techqniques/assets/119559812/9f047b33-240e-4d34-9ff3-c2fdfeca98e9)


## RESULT:
The program is executed successfully
