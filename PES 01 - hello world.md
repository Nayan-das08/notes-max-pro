---
subject : PES
category: 
- lecture-notes
module  : 
---
2023-01-02

>Links: [[PES MOC]]

## heading

## python
```python
print('Hello World')
```

## C
```C
# include <stdio.h>
int main()
{
	printf("Hello world");
}
```

## Java
```java
public class temp
{
	public static void main()
	{
		System.out.println("Hello world");
	}
}
```

## C++
```cpp
# include <iostream>
int main()
{
	std::cout << "Hello World";
}
```

## WAP for factorial
```C
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
```C
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