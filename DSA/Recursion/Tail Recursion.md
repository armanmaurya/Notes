**Tail [Recursion](Recursion.md)** is defined as a recursive function in which the recursive call is the last statement that is executed by the function. So basically nothing is left to execute after the recursion call.

For example the following code function print() is tail recursive.
````tabs

tab: C++
```cpp
// An example of tail recursive function

static void print(int n)
{
	if (n < 0)
		return;
	cout << " " << n;

	// The last executed statement is recursive call
	print(n - 1);
}
```
tab: C
```c
// An example of tail recursive function

void print(int n)
{
	if (n < 0)
		return;
	printf("%d ", n);

	// The last executed statement is recursive call
	print(n - 1);
}
```
tab: Java
```java
// An example of tail recursive function

static void print(int n)
{
	if (n < 0)
		return;

	System.out.print(" " + n);

	// The last executed statement
	// is recursive call
	print(n - 1);
}
```
tab: Python
```python
# An example of tail recursive function


def prints(n):

	if (n < 0):
		return
	print(str(n), end=' ')

	# The last executed statement is recursive call
	prints(n-1)
```
tab: Javascript
```javascript
// An example of tail recursive function 
function print(n) 
{ 
	if (n < 0) 
	return; 
	
	document.write(" " + n); 
	
	// The last executed statement 
	// is recursive call 
	print(n - 1); 
} 
```
````
