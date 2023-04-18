---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 7
Feb 28, 2023

## Objective
To remove ambiguity from a grammar.

---
## Source Code
```plain
# include <stdio.h>
# include <string.h>
# include <stdlib.h>
# include <ctype.h> 

struct single_prod
{
    char LHS;
    char RHS[10];
};

struct group_prod
{
    char LHS;
    char RHS[10][10];
    int n;
};

void show_single_prod(struct single_prod p)
{
    printf("%c -> ", p.LHS);
    printf("%s\n", p.RHS);
}

void show_group_prod(struct group_prod p)
{
    printf("    %c -> ", p.LHS);
    for (int i=0; i<p.n; i++)
    {
        printf("%s ", p.RHS[i]);
        if (i != p.n-1)
            printf("| ");
    }
    printf("\n");
}

int nth_occ(char str[], char target, int n)
{
    char *p = NULL;
    char temp[50];
    strcpy(temp, str);

    int hop = 0;
    int x = 0;
    for (int i=1; i<=n; i++)
    {
        p = strchr(temp, target);
        if (p == NULL)
        {
            break;
        }
        x = (p-temp)+hop;
        hop += (++p)-temp;
        if (i != n)
            strcpy(temp, p);
    }
    return x;
}

void remove_prod(struct group_prod *x, int target[], int operator_grammar, int max)
{
    int m = x->n;
    int count = 0;
    for (int i=0; i<m; i++)
    {
        if ((operator_grammar == 1 && target[i] != max) ||
            (operator_grammar == 0 && target[i] == 0))
        {
            for (int j=0+count; j<(x->n)-1; j++)
                strcpy(x->RHS[j], x->RHS[j+1]);
            (x->n)--;
        }
        else
            count++;
    }
}

struct dictionary
{
    char key;
    int value;
    char associativity;
};

int get_value(struct dictionary dict[], char key, int n)
{
    for (int i=0; i<n; i++)
        if (dict[i].key == key)
            return dict[i].value;
}

char max_freq_char(char str[])
{
    int freq[26] = {0}, max = 0;
    for (int i=0; i<strlen(str); i++)
        freq[str[i]-'A'] += 1;
    for (int i=0; i<26; i++)
        if (freq[i] != 0)
        {
            if (freq[i] > max)
                max = i;
        }
    return max+'A';
}

int max_freq_count(char str[])
{
    int freq[26] = {0}, max = 0;
    for (int i=0; i<strlen(str); i++)
        freq[str[i]-'A'] += 1;
    for (int i=0; i<26; i++)
        if (freq[i] != 0)
        {
            if (freq[i] > max)
                max = i;
        }
    return freq[max];
}

int main()
{
    int n_prods = 0;
    struct single_prod *P = NULL;
    int len;

    char NT_list[10];
    int  n_LHS = 0;

    char temp[10];
    FILE *f = fopen("productions2.txt", "r");

    char T_list[10];
    int  n_T = 0;

    int operator_grammar = 0;

    // read single productions from text file
    while (fgets(temp, 10, f))
    {
        len = strlen(temp)-1;
        P = (struct single_prod *) realloc(P, ++n_prods*sizeof(struct single_prod));
        P[n_prods-1].LHS = temp[0];

        if (strchr(NT_list, temp[0]) == 0)
        {
            NT_list[n_LHS++] = temp[0];
            NT_list[n_LHS] = '\0';
        }

        for (int i=3; i<len; i++)
        {
            P[n_prods-1].RHS[i-3] = temp[i];
            if (temp[i] < 'A' || temp[i] > 'Z' && temp[i] != '~')
            {
                if (strchr(T_list, temp[i]) == 0)
                {
                    T_list[n_T++] = temp[i];
                    T_list[n_T] = '\0';
                    if (operator_grammar == 0 && strchr("+-*/", temp[i]) != 0)
                        operator_grammar = 1;
                }
            }
        }
        P[n_prods-1].RHS[len-3] = '\0';
    }

    struct group_prod *P_new = NULL;

    // group the input productions as per the Non Terminals
    for (int i=0; i<strlen(NT_list); i++)
    {
        P_new = (struct group_prod *) realloc(P_new, (i+1)*sizeof(struct group_prod));
        P_new[i].n = 0;
        P_new[i].LHS = NT_list[i];
        for (int j=0; j<n_prods; j++)
        {
            if (P[j].LHS == NT_list[i])
            {
                strcpy(P_new[i].RHS[P_new[i].n++], P[j].RHS);
            }
        }
    }

    printf("\nInput Grammar:\n");
    for (int i=0; i<strlen(NT_list); i++)
    {
        show_group_prod(P_new[i]);
    }

    char term[10];
    struct dictionary dict[strlen(term)];
    if (operator_grammar == 1)
    {
        printf("\nThe terminals are: \n    ");
        for (int i=0; i<strlen(T_list); i++)
            printf("%c ", T_list[i]);
        
        printf("\n\nEnter the sequence of terminal in decreasing order of precedence: \n    ");
        for (int i=0; i<strlen(T_list); i++)
            scanf(" %c", &term[i]);

        for (int i=0; i<strlen(term); i++)
        {
            dict[i].key   = term[i];
            dict[i].value = i;
        }

        char c;
        printf("\nEnter the associativity for each operator (L or R):\n");
        for (int i=0; i<strlen(term); i++)
        {
            if (term[i] == '+' || term[i] == '-' || term[i] == '*' || term[i] == '/' || term[i] == '^' || term[i] == '%')
            {
                printf("  %c: ", term[i]);
                scanf(" %c", &c);
                dict[i].associativity = toupper(c);
            }
            else
                dict[i].associativity = '~';
        }
    }

    char NT = 'Z';
    struct group_prod *extra = NULL;
    int n_extra = 0;
    
    // to count the no. of occurences
    int count;
    
    // to maintain the 'ambiguity check' array
    int amb[10];
    int n_amb;

    // to check if new non terminal is needed
    int flag;

    // to get the index of second occurence of the LHS symbol
    int x;

    // to keep track of lowest precendence (max value)
    int max;

    char temp_NT;
    // for each group of productions
    for (int i=0; i<strlen(NT_list); i++)
    {
        max = 0;
        // for each production in the group
        for (int j=0; j<P_new[i].n; j++)
        {
            count=0;
            // check no. of occurences of lHS Non Terminal
            count = max_freq_count(P_new[i].RHS[j]);

            // if the count is more than twice: ambiguous
            if (count >= 2 && operator_grammar == 1)
            {
                for (int k=0; k<strlen(term); k++)
                {
                    if (strchr(P_new[i].RHS[j], term[k]) != 0)
                    {
                        amb[j] = get_value(dict, term[k], strlen(term));
                        if (amb[j] > max)
                            max = amb[j];
                    }
                }
            }
            else if (count >= 2 && operator_grammar == 0)
            {
                amb[j] = 1;
            }
            else
                amb[j] = 0;
        }

        // flag=0: no new non terminal is required
        flag = 0;
        // for each production in the group
        for (int j=0; j<P_new[i].n; j++)
        {
            if ((operator_grammar == 1 && amb[j] == max && amb[j] >= 2))
            {
                // if ambiguous: get and replace the second occurence
                if (dict[amb[j]].associativity == 'L')
                    x = nth_occ(P_new[i].RHS[j], max_freq_char(P_new[i].RHS[j]), 2);
                else if (dict[amb[j]].associativity == 'R')
                    x = nth_occ(P_new[i].RHS[j], max_freq_char(P_new[i].RHS[j]), 1);
                P_new[i].RHS[j][x] = (NT-(n_extra));

                // flag=1: new non terminal is used
                flag = 1;
            }    
            else if (operator_grammar == 0 && amb[j] != 0)
            {
                // if ambiguous: get and replace the second occurence
                x = nth_occ(P_new[i].RHS[j], max_freq_char(P_new[i].RHS[j]), 2);
                P_new[i].RHS[j][x] = (NT-(n_extra));

                // flag=1: new non terminal is used
                flag = 1;
            }
        }

        // since new non terminal is used
        //      create new-NT -> [non-ambiguous]
        //      remove LHS -> [non-ambiguous]
        //      add    LHS -> new-NT 
        if (flag != 0)
        {
            temp_NT = NT-(n_extra);
            strncat(NT_list, &temp_NT, 1);
            P_new = (struct group_prod *) realloc(P_new, (strlen(NT_list))*sizeof(struct group_prod));
            P_new[strlen(NT_list)-1].n = 0;
            P_new[strlen(NT_list)-1].LHS = temp_NT;
            for (int j=0; j<P_new[i].n; j++)
            {
                if ((operator_grammar == 1 && amb[j] != max) ||
                    (operator_grammar == 0 && amb[j] == 0))
                {
                    strcpy(P_new[strlen(NT_list)-1].RHS[P_new[strlen(NT_list)-1].n++], P_new[i].RHS[j]);
                }
            }

            remove_prod(&P_new[i], amb, operator_grammar, max); 

            strcpy(P_new[i].RHS[P_new[i].n++], (char [2]) {NT-(n_extra), '\0'});
            n_extra++;

        }
    }

    printf("\n\nUnambiguous Grammar:\n");
    for (int i=0; i<strlen(NT_list); i++)
    {
        show_group_prod(P_new[i]);
    }
    return 0;
}
```
---
## Output
```plain
Input Grammar:
    E -> E+E | E^E | E*E | (E) | a

The terminals are:
    + ^ * ( ) a

Enter the sequence of terminal in decreasing order of precedence:
    ()^*+a

Enter the associativity for each operator (L or R):
  ^: R
  *: L
  +: L

Unambiguous Grammar:
    E -> E+Z | Z
    Z -> E*Y | Y
    Y -> X^E | X
    X -> (E) | a

--------------------------------------

Input Grammar:
    S -> A | AB
    A -> a | Ab | AA | ~
    B -> b | Bc | bB | BB | BbB

Unambiguous Grammar:
    S -> A | AB
    A -> AZ | Z
    B -> BY | BbY | Y
    Z -> a | Ab | ~
    Y -> b | Bc | bB
```