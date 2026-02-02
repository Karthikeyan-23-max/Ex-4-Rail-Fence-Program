# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE
# NAME: Karthikeyan C
# REG.NO: 212224040152
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

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main() {
    char text[100], rail[10][100];
    int i, j, len, rails;
    int row = 0, dir = 1;

    printf("Enter the Plain Text: ");
    fgets(text, sizeof(text), stdin);
    len = strlen(text) - 1;   // remove newline

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    // Initialize rail matrix
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            rail[i][j] = '\n';

    // Fill the rail matrix in zig-zag
    for (i = 0; i < len; i++) {
        rail[row][i] = text[i];

        if (row == 0)
            dir = 1;
        else if (row == rails - 1)
            dir = -1;

        row += dir;
    }

    // Read row-wise to get cipher text
    printf("Cipher Text: ");
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);

    return 0;
}
```
# OUTPUT
<img width="1919" height="1091" alt="image" src="https://github.com/user-attachments/assets/fe115269-7358-4266-a8bf-0056c819c737" />

# RESULT
The Rail Fence Transposition Cipher was successfully implemented using C and the ciphertext was generated correctly for the given plaintext and number of rails.
