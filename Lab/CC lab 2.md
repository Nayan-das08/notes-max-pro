---
subject: CC
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 2
Jan 10, 2023

## Objective
To convert infix expression into prefix expression.

## Source Code
```plain
// convert infix expression to prefix expression

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

    // reverse the infix expression
    for (int i=1; i<count/2; i++)
    {
        strcpy(temp, new[i]);
        strcpy(new[i], new[count-i]);
        strcpy(new[count-i], temp);
    }

    // swap the inverted parenthesis
    for (int i=0; i<=count; i++)
    {
        if (strcmp(new[i], "(") == 0 && (i != 0 && i != count))
            strcpy(new[i], ")");
        else if (strcmp(new[i], ")") == 0 && (i != 0 && i != count))
            strcpy(new[i], "(");
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

void convert(char infix[][10], int count)
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
			    strcpy(output[++j], stack[top]);
				top--;
			}
			if (stack[top][0] == '(')
				top--;
		}
    }
    for (; j>=0; j--)
    {
        printf("%s ", output[j]);
    }
}

int main(int argc, char *argv[])
{
    char infix[10];
    char infix_sep[100][10];
    int  count;

    printf("Enter infix expression : ");
    scanf("%s",infix);
    
    printf("\ninfix   = \t");
    count = separate(infix,infix_sep);

    printf("\nprefix  = \t");
    convert(infix_sep, count);

    printf("\n");
    return 0;
}
```

## Output
```plain
Enter infix expression : 12*(587+2)-8/7

infix   =       ( 12 * ( 587 + 2 ) - 8 / 7 )
prefix  =       - * 12 + 587 2 / 8 7
```