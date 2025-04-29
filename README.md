# Ex. No : 3	
# RECOGNITION OF A VALID ARITHMETIC EXPRESSION THAT USES
## Name: JAGADEESH J
## Register Number : 212223110015
## Date : 29-03-25

## AIM   
To write a yacc program to recognize a valid arithmetic expression that uses operator +,- ,* and /.

## ALGORITHM
1.	Start the program.
2.	Write a program in the vi editor and save it with .l extension.
3.	In the lex program, write the translation rules for the operators =,+,-,*,/ and for the identifier.
4.	Write a program in the vi editor and save it with .y extension.
5.	Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
6.	Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
7.	Compile these with the C compiler as gcc lex.yy.c y.tab.c
8.	Enter an arithmetic expression as input and the tokens are identified as output.

## PROGRAM

```

// Online C compiler to run C program online
#include<stdio.h>
#include<ctype.h>
#include<string.h>
#include<stdlib.h>
#define MAX_EXPRESSION_SIZE 100
int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[5]; // Array to store addresses
    char b[MAX_EXPRESSION_SIZE], d[5], c, srch;
    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; 
    n = i; 
    printf("Given Expression: %s\n", b);
    printf("\nSymbol Table\n");
    printf("Symbol\taddr\ttype\n");
    for (j = 0; j < n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) { 
            if (j == n - 1 || !isalpha(b[j + 1])) { 
                void *p = malloc(sizeof(char));
                add[x] = p; 
                d[x] = c; 
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }
    getchar();
    printf("\nThe symbol to be searched: ");
    srch = getchar();
    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c@address %p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }
    if (flag == 0) {
        printf("Symbol Not Found\n");
    }
    for (i = 0; i < x; i++) {
        free(add[i]);
    }
    return 0;
}

```


## OUTPUT 
<img width="404" alt="image" src="https://github.com/user-attachments/assets/03cfbe56-211e-4c27-a4c1-a56f5bede783" />


## RESULT
A YACC program to recognize a valid arithmetic expression that uses operator +,-,* and / is executed successfully and the output is verified.
