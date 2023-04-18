---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 8
Mar 7, 2023

## Objective
To determine FIRST and FOLLOW of all the non-terminals in a grammar.

---
## Source Code
```plain
# include <stdio.h>
# include <string.h>
# include <stdlib.h>

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

struct first_follow
{
    char LHS;
    char RHS[10];
    int n;
};

int find_production(struct group_prod P_new[], char X, int n)
{
    for (int i=0; i<n; i++)
        if (P_new[i].LHS == X)
            return i;
}

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

char pop_this(char str[], int k)
{
    char c = str[k];
    for (; k<strlen(str)-1; k++)
    {
        str[k] = str[k+1];
        printf("%c", str[k]);        
    }
    str[strlen(str)-1] = '\0';
    return c;
}

void insert(char str[], int pos, char c)
{
    for (int i=strlen(str); i>=pos; i--)
        str[i+1] = str[i];
    str[pos] = c;
}


void FIRST(struct group_prod P_new[], int x, int current, int from_i, int from_j, int recall_j, char NT_list[], struct single_prod first[], int tab, int recall)
{
    char temp_char;
    char popped, *ptr;
    int next;

    char space[50];

    if (recall == 1)
    {
        // check P_new[x].RHS[recall_j]
        strcpy(space, "");
        for (int i=1; i<=tab; i++)
            strcat(space, "    ");
        // printf("%s", space);

        temp_char = P_new[x].RHS[recall_j][0];
        // printf("  (%d) %c->  %c from \"%s\"", x, P_new[x].LHS, temp_char, P_new[x].RHS[recall_j]);

        if (strchr(NT_list, temp_char) != 0)
        {
            next = find_production(P_new, temp_char, strlen(NT_list));
            // printf("  (NT) (%d) (recall)", next);
            // call FIRST for P_new[next]
            // printf("\n");
            FIRST(P_new, next, current, x, recall_j, 0, NT_list, first, tab+1, 0);
        }
        else if (temp_char == '~')
        {
            // printf("  eSpilon");
            if (strchr(first[current].RHS, temp_char) == 0)
                {
                    strcat(first[current].RHS, (char [2]){temp_char, '\0'});
                    // printf("  appended to first(%c)", first[current].LHS);
                }
        }
        else
        {
            // printf("  terminal");
            if (strchr(first[current].RHS, temp_char) == 0)
            {
                strcat(first[current].RHS, (char [2]){temp_char, '\0'});
                // printf("  appended to first(%c)", first[current].LHS);
            }
        }
    }
    else
    {
        for (int j=0; j<P_new[x].n; j++)
        {
            strcpy(space, "");
            for (int i=1; i<=tab; i++)
                strcat(space, "    ");
            // printf("%s", space);
            
            temp_char = P_new[x].RHS[j][0];
            // printf("  (%d) %c->  %c from \"%s\"", x, P_new[x].LHS, temp_char, P_new[x].RHS[j]);

            // temp_char is a non terminal
            if (strchr(NT_list, temp_char) != 0)
            {
                next = find_production(P_new, temp_char, strlen(NT_list));
                // printf("  (NT) (%d)", next);
                // printf("\n");
                // call FIRST for P_new[next]
                FIRST(P_new, next, current, x, j, 0, NT_list, first, tab+1, 0);
            }
            else if (temp_char == '~')
            {
                // printf("  (eSpilon)");
                if (tab == 0)
                {
                    if (strchr(first[current].RHS, temp_char) == 0)
                    {
                        strcat(first[current].RHS, (char [2]){temp_char, '\0'});
                        // printf("  appended to first(%c)", first[current].LHS);
                    }
                }
                else
                {
                    // popped = pop_this(P_new, from_i, from_j);
                    if (strlen(P_new[from_i].RHS[from_j]) == 1)
                    {
                        popped = P_new[from_i].RHS[from_j][0];
                        P_new[from_i].RHS[from_j][0] = '~';
                        // printf("\n  %s%s \t%d,%d\n", space, P_new[from_i].RHS[from_j], from_i, from_j);
                        FIRST(P_new, from_i, current, x, j, from_j, NT_list, first, tab+1, 1);
                        P_new[from_i].RHS[from_j][0] = popped;
                        // printf("\n  %s%s", space, P_new[from_i].RHS[from_j]);
                    }
                    else
                    {
                        popped = P_new[from_i].RHS[from_j][0];
                        ptr = P_new[from_i].RHS[from_j] + 1;
                        strcpy(P_new[from_i].RHS[from_j], ptr);
                        // printf("\n  %s%s \t%d,%d\n", space, P_new[from_i].RHS[from_j], from_i, from_j);
                        
                        FIRST(P_new, from_i, current, x, j, from_j, NT_list, first, tab+1, 1);

                        for (int k=strlen(P_new[from_i].RHS[from_j])-1; k>=0; k--)
                            P_new[from_i].RHS[from_j][k+1] = P_new[from_i].RHS[from_j][k];
                        P_new[from_i].RHS[from_j][0] = popped;
                        // printf("\n  %s%s", space, P_new[from_i].RHS[from_j]);
                    }
                }
                // printf("\n");
            }
            else
            {
                // printf("  (T)");
                if (strchr(first[current].RHS, temp_char) == 0)
                {
                    strcat(first[current].RHS, (char [2]){temp_char, '\0'});
                    // printf("  appended to first(%c)", first[current].LHS);
                }
                // printf("\n");
            }
        }
    }
}

void FOLLOW(struct group_prod P_new[], int x, int current, int from_i, int from_j, char NT_list[], struct single_prod follow[], struct single_prod first[], int tab, int recall)
{
    int loc, epsilon_flag;
    char temp_char, popped;

    struct single_prod temp_first, temp_follow;

    char space[50];

    if (recall == 1)
    {
        int i=from_i;
        int j=from_j;
        loc = strchr(P_new[i].RHS[j], follow[current].LHS) - P_new[i].RHS[j];
        temp_char = P_new[i].RHS[j][loc+1];

        if (loc == strlen(P_new[i].RHS[j])-1)
        {
            temp_follow = follow[find_production(P_new, P_new[i].LHS, strlen(NT_list))];
            for (int k=0; k<strlen(temp_follow.RHS); k++)
            {
                if (strchr(follow[current].RHS, temp_follow.RHS[k]) == 0)
                {
                    strcat(follow[current].RHS, (char [2]){temp_follow.RHS[k], '\0'});
                }
            }
        }
        else
        {
            // the succeeding char is NT
            if (strchr(NT_list, temp_char) != 0)
            {
                temp_first = first[find_production(P_new, temp_char, strlen(NT_list))];
                epsilon_flag = 0;
                for (int k=0; k<strlen(temp_first.RHS); k++)
                {
                    if (temp_first.RHS[k] == '~')
                        epsilon_flag = 1;
                    else if (strchr(follow[current].RHS, temp_first.RHS[k]) == 0)
                    {
                        strcat(follow[current].RHS, (char [2]){temp_first.RHS[k], '\0'});
                    }
                }
                if (epsilon_flag == 1)
                {
                    popped = pop_this(P_new[i].RHS[j], loc+1);
                    
                    FOLLOW(P_new, x, current, i, j, NT_list, follow, first, tab+1, 1);

                    insert(P_new[i].RHS[j], loc+1, popped);
                }
            }
            // the succeeding char is Terminal
            else
            {
                if (strchr(follow[current].RHS, temp_char) == 0)
                {
                    strcat(follow[current].RHS, (char [2]){temp_char, '\0'});
                }
            }
        }
    }
    else
    {
        for (int i=0; i<strlen(NT_list); i++)
        {
            for (int j=0; j<P_new[i].n; j++)
            {
                if (strchr(P_new[i].RHS[j], follow[current].LHS) != 0)
                {
                    loc = strchr(P_new[i].RHS[j], follow[current].LHS) - P_new[i].RHS[j];
                    temp_char = P_new[i].RHS[j][loc+1];

                    if (loc == strlen(P_new[i].RHS[j])-1)
                    {
                        temp_follow = follow[find_production(P_new, P_new[i].LHS, strlen(NT_list))];
                        for (int k=0; k<strlen(temp_follow.RHS); k++)
                        {
                            if (strchr(follow[current].RHS, temp_follow.RHS[k]) == 0)
                            {
                                strcat(follow[current].RHS, (char [2]){temp_follow.RHS[k], '\0'});
                            }
                        }
                    }
                    else
                    {
                        // the succeeding char is NT
                        if (strchr(NT_list, temp_char) != 0)
                        {
                            temp_first = first[find_production(P_new, temp_char, strlen(NT_list))];
                            epsilon_flag = 0;
                            for (int k=0; k<strlen(temp_first.RHS); k++)
                            {
                                if (temp_first.RHS[k] == '~')
                                    epsilon_flag = 1;
                                else if (strchr(follow[current].RHS, temp_first.RHS[k]) == 0)
                                {
                                    strcat(follow[current].RHS, (char [2]){temp_first.RHS[k], '\0'});
                                }
                            }
                            if (epsilon_flag == 1)
                            {
                                popped = pop_this(P_new[i].RHS[j], loc+1);
                                
                                FOLLOW(P_new, x, current, i, j, NT_list, follow, first, tab+1, 1);

                                insert(P_new[i].RHS[j], loc+1, popped);
                            }
                        }
                        // the succeeding char is Terminal
                        else
                        {
                            if (strchr(follow[current].RHS, temp_char) == 0)
                            {
                                strcat(follow[current].RHS, (char [2]){temp_char, '\0'});
                            }
                        }
                    }

                }
            }
        }
    }
}

int main()
{
    int n_prods = 0;
    struct single_prod *P = NULL;
    int len;

    char NT_list[10];
    int  n_LHS = 0;

    char temp[10];
    FILE *f = fopen("operator3.txt", "r");

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

    // for (int i=0; i<n_prods; i++)
    //     show_single_prod(P[i]);

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

    // --------------------------------------------------

    printf("\n------------------------------------");

    printf("\n\nFIRST");
    
    struct group_prod *P_new_copy = calloc(strlen(NT_list), sizeof(struct group_prod));
    // memcpy(P_new_copy, P_new, sizeof(P_new));
    
    // to store the FIRSTs
    struct single_prod first[strlen(NT_list)];
    
    for (int i=0; i<strlen(NT_list); i++)
    {
        P_new_copy[i].LHS = P_new[i].LHS;
        P_new_copy[i].n = P_new[i].n;
        for (int j=0; j<P_new[i].n; j++)
            strcpy(P_new_copy[i].RHS[j], P_new[i].RHS[j]);
    }

    for (int i=0; i<strlen(NT_list); i++)
    {
        // printf("\n%c\n", P_new[i].LHS);
        first[i].LHS = P_new[i].LHS;
        strcpy(first[i].RHS, "");

        FIRST(P_new_copy, i, i, i, 0, 0, NT_list, first, 0, 0);
        // memcpy(P_new_copy, P_new, sizeof(P_new));
    }

    printf("\n");
    for (int i=0; i<strlen(NT_list); i++)
    {
        printf("    %c -> ", first[i].LHS);
        printf("%s\n", first[i].RHS);
    }

    printf("\n------------------------------------");

    printf("\n\nFOLLOW");
    struct single_prod follow[strlen(NT_list)];

    char start = P_new[0].LHS;

    for (int i=0; i<strlen(NT_list); i++)
    {
        follow[i].LHS = NT_list[i];
        strcpy(follow[i].RHS, "");

        if (NT_list[i] == start)
            strcat(follow[i].RHS, (char [2]){'$', '\0'});
    }

    int limit = strlen(NT_list);
    for (int i=0; i<limit; i++)
    {
        FOLLOW(P_new, i, i, 0, 0, NT_list, follow, first, 0, 0);
    }

    printf("\n");
    for (int i=0; i<limit; i++)
    {
        printf("    %c -> ", follow[i].LHS);
        printf("%s\n", follow[i].RHS);
    }
    return 0;
}
```
---
## Output
```plain
Input Grammar:
    E -> TZ
    T -> FY
    F -> (E) | a
    Z -> +TZ | ~
    Y -> *FY | ~

------------------------------------

FIRST
    E -> (a
    T -> (a
    F -> (a
    Z -> +~
    Y -> *~

------------------------------------

FOLLOW
    E -> $)
    T -> +$)
    F -> *+$)
    Z -> $)
    Y -> +$)
```