---
subject : PES
category: 
- lecture-notes
module  : 
---
## "Hello World" programs in different languages
### python
```plain
print('Hello World')
```

### C
```plain
# include <stdio.h>
int main()
{
	printf("Hello world");
}
```

### Java
```plain
public class temp
{
	public static void main()
	{
		System.out.println("Hello world");
	}
}
```

### C++
```plain
# include <iostream>
int main()
{
	std::cout << "Hello World";
}
```

---
## WAP for factorial
```plain
# include <stdio.h>

int factorial(int n)
{
	if (n<=1)
		return 1;
	else
		return n*factorial(n-1);
}

int main()
{
	int n=10;
	factorial(n);
	return 0;
}
```

## WAP for matrix multiplication
```plain
# include <stdio.h>

const int size

int mult(int A[][size], int B[][size], int C[][size])
{
	int sum;
	for (int i=0; i<p; i++)
	{
		for (int j=0; j<q; j++)
		{
			C[i][j]=0;
			for (int k=0; k<r; k++)
			{
				C[i][j] += A[i][k] + B[k][j];
			}
		}
	}
}
```

---
## WAP to sort a very large array containing 0s and 1s (min time and space complexity)
```plain
from random import randint

a = [randint(0,1) for i in range(2000)]
# a = [0,1,0,1,1,0,0,0,1,0,1,0,1,1,1,0,0,0]
# print(a)

p = 0
q = len(a)-1

# for i in range(len(a)):
while (p <= q):
    if a[p] == 1 and a[q] == 0:
        a[p],a[q] = a[q],a[p]
    elif a[p] == 0:
        p += 1
    elif a[q] == 1:
        q -= 1

print(a)
```