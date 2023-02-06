---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 3
Jan 31, 2023

## Objective
To count the number of tokens in the following sample C program:
```plain
int main()
{
        int a, b;
        float i ;
        printf("enter the elements");
        scanf("%d %d", &a, &b);
        i = a+b;
        printf("sum = %d", a);
        return 0;
}
```

---
## Source Code
```plain
# include <stdio.h>
# include <string.h>
# include <stdlib.h>

int count = 0;

int isBreak(char x, char y)
{
        if (x == '.')
        {
                // decimal
                if (y >= '0' && y <= '9')
                {
                        return 0;
                }
                // indirection operator
                else
                {
                        return 1;
                }
        }
        else if (
                // white space
                (x == ' ')  ||
                (x == '\t') ||
                (x == '\n') ||
                // brackets
                (x == '(')  ||
                (x == ')')  ||
                (x == '{')  ||
                (x == '}')  ||
                // separators
                (x == ',')  ||
                (x == ';')  ||
                // address-of operator
                (x == '&')  ||
                // arithmetic operators
                (x == '+')  ||
                (x == '-')  ||
                (x == '*')  ||
                (x == '/')  ||
                (x == '%')  ||
                // assignment operator / equal symbol
                (x == '=')  ||
                // relational operators
                (x == '<')  ||
                (x == '>')  ||
                (x == '!')
                )
                return 1;
        else
                return 0;
}

// this function check for operator
// when the lexeme is separated by breaks
// the breaks are those which separate identifiers and keywords
// includes space, tab, brackets, commas, operator symbols
// basically symbols which signify the ending of a lexeme
// the checking of breaks is done in the above function
int isOperator(char x, char y)
{
        // multi char
        if (
                // arithmetic
                (x == '+' && y == '+') ||
                (x == '-' && y == '-') ||

                // relational
                (x == '=' && y == '=') ||
                (x == '>' && y == '=') ||
                (x == '<' && y == '=') ||
                (x == '!' && y == '=') ||

                // logical
                (x == '&' && y == '&') ||
                (x == '|' && y == '|') ||

                // assignment
                (x == '+' && y == '=') ||
                (x == '-' && y == '=') ||
                (x == '*' && y == '=') ||
                (x == '/' && y == '=') ||
                (x == '%' && y == '=') ||

                // structure dereference
                (x == '-' && y == '>')
                )
                return 2;

        // single char
        else if (
                // arithmetic operators
                (x == '+') ||
                (x == '-') ||
                (x == '*') ||
                (x == '/') ||
                (x == '%') ||
                //relational
                (x == '>') ||
                (x == '<') ||
                // logical
                (x == '!') ||
                // assignment
                (x == '=') ||
                // structure reference
                (x == '.') ||
                // address of
                (x == '&')
                )
                return 1;

        else
                return 0;
}

int isKeyword(char x[])
{
        if (
                (strcmp(x, "auto")              == 0) ||
                (strcmp(x, "break")     == 0) ||
                (strcmp(x, "case")              == 0) ||
                (strcmp(x, "char")              == 0) ||
                (strcmp(x, "const")     == 0) ||
                (strcmp(x, "continue")  == 0) ||
                (strcmp(x, "default")   == 0) ||
                (strcmp(x, "do")                == 0) ||
                (strcmp(x, "double")    == 0) ||
                (strcmp(x, "else")              == 0) ||
                (strcmp(x, "enum")              == 0) ||
                (strcmp(x, "extern")    == 0) ||
                (strcmp(x, "float")     == 0) ||
                (strcmp(x, "for")               == 0) ||
                (strcmp(x, "goto")              == 0) ||
                (strcmp(x, "if")                == 0) ||
                (strcmp(x, "int")               == 0) ||
                (strcmp(x, "long")              == 0) ||
                (strcmp(x, "register")  == 0) ||
                (strcmp(x, "return")    == 0) ||
                (strcmp(x, "short")     == 0) ||
                (strcmp(x, "signed")    == 0) ||
                (strcmp(x, "sizeof")    == 0) ||
                (strcmp(x, "static")    == 0) ||
                (strcmp(x, "struct")    == 0) ||
                (strcmp(x, "switch")    == 0) ||
                (strcmp(x, "typedef")   == 0) ||
                (strcmp(x, "union")     == 0) ||
                (strcmp(x, "unsigned")  == 0) ||
                (strcmp(x, "void")              == 0) ||
                (strcmp(x, "volatile")  == 0) ||
                (strcmp(x, "while")     == 0)
        )
                return 1;
        else
                return 0;
}

int isConstant(char x[])
{
        int constant=1;
        if (strcmp(x, "NULL") == 0)
                return 1;
        else
        {
                for (int i=0; i<strlen(x); i++)
                {
                        if (i == 0)
                                if (x[i] >= '0' && x[i] <= '9')
                                        constant = 1;
                                else
                                {
                                        constant = 0;
                                        break;
                                }
                        else
                                if (x[i] >= '0' && x[i] <= '9' || x[i] == '.')
                                        constant = 1;
                                else
                                {
                                        constant = 0;
                                        break;
                                }
                }
                if (constant == 0)
                        return 0;
                else
                        return 1;
        }
}


int isIdentifier(char x[])
{
        if (
                (x[0] >= 'A' && x[0] <= 'Z') ||
                (x[0] >= 'a' && x[0] <= 'z') ||
                (x[0] == '_')
                )
                return 1;
        else
                return 0;
}

// ---------------------------------------------------------------

void check_line(char line[], int v)
{
        char *lex = (char *) calloc(1, sizeof(char));
        int left=0, right=0;
        int string_flag=0;

        if (v == 1)
        {
                for (int i=0; i<strlen(line)-1; i++)
                {
                        if (line[i] == '\t')
                                printf("\t");
                        printf("%2d ", i);
                }
                printf("\n");
                for (int i=0; i<strlen(line) ; i++)
                {
                        printf("%c  ", line[i]);
                        if (line[i] == '\t')
                                printf("  ");
                }
        }


        for (int i=0; i<strlen(line)-1; i++)
        {
                if (string_flag == 0 && line[i] == '"')
                {
                        string_flag = 1;
                        right++;
                }
                else if (string_flag == 1 && line[i] == '"')
                {
                        lex = (char *) realloc(lex, sizeof(char)*(right-left+2));
                        for (int j=left; j<=right; j++)
                        {
                                lex[j-left] = line[j];
                        }
                        lex[right-left+1] = '\0';
                        count++;

                        right++;
                        left=right;

                        string_flag = 0;
                }
                else if (string_flag == 1)
                {
                        right++;
                }
                else if (!isBreak(line[i], line[i+1]))
                {
                        right++;
                }
                else
                {
                        if (right-left > 0)
                        {

                                lex = (char *) realloc(lex, sizeof(char)*(right-left+1));
                                for (int j=left; j<right; j++)
                                {
                                        lex[j-left] = line[j];
                                }
                                lex[right-left] = '\0';
                                count++;
                        }
                        if (isOperator(line[i], line[i+1]) == 1)
                        {
                                count++;
                        }
                        else if (isOperator(line[i], line[i+1]) == 2)
                        {
                                count++;
                                right++;
                                i++;
                        }
                        else if (line[i] != ' ' && line[i] != '\t')
                        {
                                count++;
                        }

                        right++;
                        left=right;
                }
        }
}

int main(int argc, char *argv[])
{
        FILE *f = fopen("program.txt", "r");
        char line[100];

        int v;
        if (argc == 2)
                v = atoi(argv[1]);
        else
                v = 0;

        while (fgets(line, 100, f))
        {
                check_line(line, v);
        }

        printf("number of tokens: %d", count);
        fclose(f);

        printf("\n");
        return 0;
}
```
---
## Output
```plain
number of tokens = 46
```