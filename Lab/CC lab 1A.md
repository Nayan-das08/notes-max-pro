---
subject: CC
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 1A
Jan 3, 2023

## Objective
To convert infix expression into postfix expression.

---
## Source Code
```plain
// convert infix expression to postfix expression

# include <stdio.h>
# include <string.h>
# include <stdlib.h>

int check(char c)
{
	if (c >= 40 && c <= 41)
		return 0;
	else if (c >= 48 && c <= 57)
    	return 1;
	else if (c == '+' || c == '-' || c == '*' || c ==  '/')
    	return 2;
	else
    	return -1;
}

int separate(char infix[], char new[][10])
{
    char temp[10];
    int k=0, count=0;
    strcpy(new[count++], "(");

    for (int i=0; i<strlen(infix); i++)
    {
        // not a number
        if (check(infix[i]) != 1)
        {
            // temp not empty
            if (strcmp(temp, "") != 0)
            {
                strcpy(new[count++], temp);
                strcpy(temp,"");
            }
            strcpy(new[count++], (char [2]) {infix[i], '\0'});
        }
        // a number
        else if (check(infix[i]) == 1)
        {
            strncat(temp, &infix[i], 1);
        }
    }

    // insert the last operand 
    // and the final parenthesis
    if (strcmp(temp, "") != 0)
        strcpy(new[count++], temp);
    strcpy(new[count], ")");

    // display the infix expression
    for (int i=0; i<=count; i++)
    {
        printf("%s ", new[i]);
    }
    return count;
}

int precedence(char c)
{
    if (c == '-')
        return 1;
    else if (c == '+')
        return 1;
    else if (c == '/')
        return 2;
    else if (c == '*')
        return 2;
    return 0;
}

void convert(char infix[][10], int count, int verbose)
{
    int top=-1;
    char stack[10][5], output[20][10], a, b;
	int j=-1;
    for (int i=0; i<=count; i++)
    {
		if (strcmp(infix[i], "(") == 0)
		{
			strcpy(stack[++top], infix[i]);
		}
		else if (check(infix[i][0]) == 1)
		{
            if (verbose == 0)
                printf("%s ", infix[i]);
            else
                strcpy(output[++j], infix[i]);
		}
		else if (check(infix[i][0]) == 2)
		{
			a = infix[i][0];
			b = stack[top][0];
			if (check(b) == 2)
			// stack top is an operator
			{
                // pop till stack[top] > infix[i]
                while (precedence(b) >= precedence(a))
                {
                    if (verbose == 0)
                        printf("%s ", stack[top]);
                    else
                        strcpy(output[++j], stack[top]);
                    top--;

                    // get new stack[top]
                    b = stack[top][0];
                }
                // push
                strcpy(stack[++top], infix[i]);
            }
            else
            {
                // push
                strcpy(stack[++top], infix[i]);
            }
		}
		else if (strcmp(infix[i], ")") == 0)
		{
			while (stack[top][0] != '(')
			{
				// pop
                if (verbose == 0)
				    printf("%s ", stack[top]);
                else
				    strcpy(output[++j], stack[top]);
				top--;
			}
			if (stack[top][0] == '(')
				top--;
		}

        if (verbose != 0)
        {
        	printf("\n%s \tstack = ", infix[i]);
        	for (int k=0; k<=top; k++)
        		printf("%s ", stack[k]);
            if (top <= 2)
                printf("\t");
        	printf("\to/p = ");
        	for (int k=0; k<=j; k++)
        		printf("%s ", output[k]);
        }
    }
}

int main(int argc, char *argv[])
{
    char infix[10];
    char infix_sep[100][10];
    int  count;
    int verbose;
    if (argc == 1)
        verbose = 0;
    else
        verbose = atoi(argv[1]);

    printf("Enter infix expression : ");
    scanf("%s",infix);
    
    printf("\ninfix   = \t");
    count = separate(infix,infix_sep);

    printf("\npostfix = \t");
    convert(infix_sep, count, verbose);

    printf("\n");
    return 0;
}
```

---
## Output
```plain
Enter infix expression : 12*(587+2)-8/7

infix   =       ( 12 * ( 587 + 2 ) - 8 / 7 )
postfix =       12 587 2 + * 8 7 / -
```