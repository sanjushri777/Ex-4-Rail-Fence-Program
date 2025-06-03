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

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main() {
    int i, j, len, rails, count;
    char str[1000];
    int code[100][1000] = {0};  // Initialize all elements to 0

    printf("Enter a Secret Message:\n");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';  // Remove trailing newline

    len = strlen(str);

    printf("Enter number of rails:\n");
    scanf("%d", &rails);

    count = 0;
    j = 0;

    // Write characters in zig-zag pattern over the rails
    while (j < len) {
        if (count % 2 == 0) {
            // Going down the rails
            for (i = 0; i < rails && j < len; i++) {
                code[i][j] = (int)str[j];
                j++;
            }
        } else {
            // Going up the rails (excluding first and last rail)
            for (i = rails - 2; i > 0 && j < len; i--) {
                code[i][j] = (int)str[j];
                j++;
            }
        }
        count++;
    }

    printf("Encrypted Message:\n");
    // Read the matrix row-wise to get the encrypted message
    for (i = 0; i < rails; i++) {
        for (j = 0; j < len; j++) {
            if (code[i][j] != 0) {
                printf("%c", code[i][j]);
            }
        }
    }
    printf("\n");

    return 0;
}
```

# OUTPUT

![image](https://github.com/user-attachments/assets/f45758c5-078b-4cb2-acca-4d8342a673e3)


# RESULT

Thus, the implementation of Rail Fence program executed successfully
