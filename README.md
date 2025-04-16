# Ex.No:6
# IMPLEMENTATION OF THE BACK END OF THE COMPILER 
## Register Number:212223043005
## Date:16.04.2025
## AIM:
To write a program to implement the back end of the compiler.
## ALGORITHM:
1. Start the program.
2. Get the three variables from statements and stored in the text file k.txt.
3. Compile the program and give the path of the source file.
4. Execute the program.
5. Target code for the given statement is produced.
6. Stop the program.
## PROGRAM:
```
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

int main() {
    int i = 2, j = 0, k = 2, k1 = 0; 
    char ip[50], kk[50];  // Increase array sizes for safety
    FILE *fp;

    printf("Enter the filename of the intermediate code: ");
    if (scanf("%49s", kk) != 1) {
        printf("Error reading filename.\n");
        return 1;
    }

    fp = fopen(kk, "r"); 
    if (fp == NULL) {
        printf("\nError in opening the file\n");
        return 1;
    }
    
    printf("\nStatement\tTarget Code\n\n"); 

    // Read each line from the file
    while (fscanf(fp, "%49s", ip) != EOF) {
        // Check array size before using indices
        if (i + k < sizeof(ip)) {
            printf("%s\tMOV %c,R%d SUB ", ip, ip[i + k], j);

            // Ensure that ip[i + 1] is within bounds before using it
            if (i + 1 < sizeof(ip) && ip[i + 1] == '+') {
                printf("ADD ");
            } else {
                printf("SUB ");
            }

            // Check if ip[i] is a lowercase letter
            if (i < sizeof(ip) && islower(ip[i])) {
                printf("%c,R%d\n", ip[i + k1], j);
            } else {
                // Check if ip[i + 2] is within bounds before using it
                if (i + 2 < sizeof(ip)) {
                    printf("%c,%c\n", ip[i], ip[i + 2]);
                } else {
                    printf("Error: Index out of bounds\n");
                    fclose(fp);
                    return 1;
                }
            }

            j++;
            k1 = 2;
            k = 0;
        } else {
            printf("Error: Index out of bounds while processing '%s'\n", ip);
            fclose(fp);
            return 1;
        }
    }

    fclose(fp);
    return 0;
}
```
# OUTPUT:
![image](https://github.com/user-attachments/assets/6e32c2a1-aae7-410e-bdb9-9446f0fb2172)


# RESULT:
The back end of the compiler is implemented successfully, and the output is verified.
