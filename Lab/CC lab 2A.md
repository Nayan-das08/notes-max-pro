---
subject: 
category: lab-file
---
>%%Links: [[Lab Files]]%%

# Experiment 2A
Jan 17, 2023

## Objective
To create a DFA in program for the regular expression
$$0^*1^+(0+1)$$
---
## Source Code
```plain
# include <stdio.h>
# include <stdlib.h>
# include <string.h>

int main()
{
	// Q: set of all states that are traversable
	int states[10][10];
	states[0][0] = 0;
	states[0][1] = 1;
	states[1][0] = 3;
	states[1][1] = 2;
	states[2][0] = 3;
	states[2][1] = 2;
	states[3][0] = -1;
	states[3][1] = -1;

	// F: set of final states
	int final[] = {2,3}, n_final = sizeof(final)/sizeof(int);

	char regex[20];
	printf("Enter the regex : ");
	scanf("%s", regex);

	int current = 0, next, input, flag=0;

	for (int i=0; i<strlen(regex); i++)
	{
		// get the input from the string regex
		input = atoi((char [2]){regex[i], '\0'});
		
		// get the next state from state transitions on current node and input
		next = states[current][input];

		if (next != -1)
		// when there exists a node to travel next to in next iteration
			printf("q%d(%d) -> q%d\n", current, input, next);
		else
		{
			printf("q%d(%d) -> invalid\n", current, input);
			// we don't iterate anymore as the string upto now
			// got us to a dead-end
			break;
		}

		current = next;
	}

	for (int j=0; j<n_final; j++)
	// for each final state
	{
		// check if the last node reached is the final node
		if (next == final[j])
		{
			flag = 1;
			break;
		}
	}

	if (flag == 1)
		printf("\nString accepted");
	else
		printf("\nString not accepted");

	printf("\n");
	return 0;
}
```
---
## Output
```plain
Enter the regex : 01101
q0(0) -> q0
q0(1) -> q1
q1(1) -> q2
q2(0) -> q3
q3(1) -> invalid

String not accepted
-------------------------------------------
Enter the regex : 01111
q0(0) -> q0
q0(1) -> q1
q1(1) -> q2
q2(1) -> q2
q2(1) -> q2

String accepted
```