# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

 To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.


# PROGRAM
```c
// Rail Fence Cipher
// Programmed by Siddarth A S 212224040316
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main()
{
    int i, j, len, rails, count, code[100][1000];
    char str[1000];

    printf("Enter a Secret Message\n");
    fgets(str, sizeof(str), stdin);

    str[strcspn(str, "\n")] = '\0';

    len = strlen(str);

    printf("Enter number of rails\n");
    scanf("%d", &rails);

    for (i = 0; i < rails; i++)
    {
        for (j = 0; j < len; j++)
        {
            code[i][j] = 0;
        }
    }

    count = 0;
    j = 0;

    while (j < len)
    {
        if (count % 2 == 0)
        {
            for (i = 0; i < rails && j < len; i++)
            {
                code[i][j] = (int)str[j];
                j++;
            }
        }
        else
        {
            for (i = rails - 2; i > 0 && j < len; i--)
            {
                code[i][j] = (int)str[j];
                j++;
            }
        }

        count++;
    }

    for (i = 0; i < rails; i++)
    {
        for (j = 0; j < len; j++)
        {
            if (code[i][j] != 0)
            {
                printf("%c", code[i][j]);
            }
        }
    }

    printf("\n");

    return 0;
}


```
# OUTPUT

<img width="1918" height="1198" alt="Screenshot 2026-05-13 112842" src="https://github.com/user-attachments/assets/9efafa54-ae8e-44b5-9c7a-de1fcdb03e86" />


# RESULT

Thus the implementation of Rail Fence Cipher had been executed successfully.
