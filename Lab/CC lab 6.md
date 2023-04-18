---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 6
Feb 21, 2023

## Objective
To remove left recursion from a grammar.

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

void show_single_prod(struct single_prod p)
{
    printf("%c -> ", p.LHS);
    if (p.RHS[0] == '~')
        printf("%c\n", 238);
    else
        printf("%s\n", p.RHS);
}

void show_group_prod(struct group_prod p)
{
    printf("    %c -> ", p.LHS);
    for (int i=0; i<p.n; i++)
    {
        if (p.RHS[i][0] == '~')
            printf("%c ", 238);
        else
            printf("%s ", p.RHS[i]);
        if (i != p.n-1)
            printf("| ");
    }
    printf("\n");
}

void func(char src[], char dest[], char NT)
{
    strcpy(dest, "");
    for (int i=1; i<strlen(src); i++)
        dest[i-1] = src[i];
    dest[strlen(src)-1] = NT;
    dest[strlen(src)] = '\0';
}

void remove_prod(struct group_prod *p, int target[], int n_target)
{
    for (int i=0; i<n_target; i++)
    {
        for (int j=target[i]-i; j<(p->n)-1; j++)
        {
            strcpy(p->RHS[j], p->RHS[j+1]);
        }
    }
    p->n -= n_target;
}

int main()
{
    int n_prods = 0;
    struct single_prod *P = NULL;
    int len;

    char NT_list[10];
    char n_LHS = 0;

    char temp[10];
    FILE *f = fopen("productions.txt", "r");

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

    printf("Input Grammar:\n");
    for (int i=0; i<strlen(NT_list); i++)
    {
        show_group_prod(P_new[i]);
    }

    // -----------------------------------

    char NT = 'P';
    struct group_prod *extra = NULL;
    int n_extra = 0;
    char temp2[2];
    char temp3[10];

    int *to_remove;
    int n_remove;

    int recursive_flag;
    int *non_recursive;
    int n_non_recursive;

    // remove left recursive productions
    // and add them to new Non Terminal productions
    for (int i=0; i<strlen(NT_list); i++)
    {
        extra = (struct group_prod *) realloc(extra, ++n_extra*sizeof(struct group_prod));
        // printf("\n%d\n", n_extra);
        extra[n_extra-1].LHS = NT+(n_extra-1);
        extra[n_extra-1].n = 0;
        
        recursive_flag = 0;
        non_recursive = NULL;
        n_non_recursive = 0;


        to_remove = NULL;
        n_remove = 0;

        for (int j=0; j<P_new[i].n; j++)
        {
            if (P_new[i].LHS == P_new[i].RHS[j][0])
            {
                recursive_flag = 1;

                // printf("%s \t-> ", P_new[i].RHS[j]);
                func(P_new[i].RHS[j], temp3, (NT+(n_extra-1)));
                strcpy(extra[n_extra-1].RHS[extra[n_extra-1].n], temp3);
                // printf("%s", extra[n_extra-1].RHS[extra[n_extra-1].n]);
                extra[n_extra-1].n++;

                to_remove = (int *) realloc(to_remove, ++n_remove*sizeof(int));
                to_remove[n_remove-1] = j;
                // printf("\n");
            }
            else
                // for those productions in a group which are non recursive
                // but some of them are
                // they will get extra NT concatenated
                if (recursive_flag == 1)
                {
                    non_recursive = (int *) realloc(non_recursive, ++n_non_recursive*sizeof(int));
                    non_recursive[n_non_recursive-1] = j;
                }
        }
        // this is 0 by default for groups
        // which have no reccursive productions
        for (int j=0; j<n_non_recursive; j++)
        {
            sprintf(temp2, "%c", (NT+(n_extra-1)));
            strcat(P_new[i].RHS[non_recursive[j]], temp2);
        }
        // printf("\n");
        remove_prod(&P_new[i], to_remove, n_remove);
        // printf("\n");

        sprintf(temp2, "%c", '~');
        strcpy(extra[n_extra-1].RHS[extra[n_extra-1].n++], temp2);

        // remove the extra production group
        // if there are no productions in it
        // or the only production in it is epsilon
        if  (extra[n_extra-1].n == 0 || 
            (extra[n_extra-1].n == 1 && extra[n_extra-1].RHS[0][0] == '~'))
            n_extra--;
    }


    // ------------------------------------

    // combine the old and extra productions
    // into a new group
    struct group_prod *final = NULL;
    int n_final = 0;
    for (int i=0; i<strlen(NT_list); i++)
    {
        // show_group_prod(P_new[i]);
        if (P_new[i].n > 0)
        {
            final = (struct group_prod *) realloc(final, ++n_final*sizeof(struct group_prod));
            final[n_final-1] = P_new[i];
        }
    }
    for (int i=0; i<n_extra; i++)
    {
        // show_group_prod(extra[i]);
        if (extra[i].n > 0)
        {
            final = (struct group_prod *) realloc(final, ++n_final*sizeof(struct group_prod));
            final[n_final-1] = extra[i];
        }
    }
    
    printf("\nAfter removing left-recursive productions\n");
    for (int i=0; i<n_final; i++)
        show_group_prod(final[i]);

    return 0;
}

```
---
<div style="page-break-after: always; visibility: hidden">
\pagebreak
</div>

## Output
```plain
Input Grammar:
    A -> Ac | Ab | bB | ab
    B -> bB | ε

After removing left-recursive productions
    A -> bBP | abP
    B -> bB | ε
    P -> cP | bP | ε
```