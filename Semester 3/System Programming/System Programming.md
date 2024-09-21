[Semester:: 3]   •   [Year:: 2]   •   [ECT:: 6]• [Completed:: ✅]
# Basic Syntax of C:

## Printing in C

The function which is used to print data in C is `printf`.

```c
\#include <stdio.h>

int main() {
	printf("My name is %s. \ni was %d in the year 2000. \n",
				"Harkeerat", 2000 - 2002);
}
```

The first argument is a **format string** that includes **conversion specifications,**

**%d** prints an integer in decimal notation.

**%c** prints an integer as a character.

**%g** prints a float in decimal notation.

## Basic Types

C has pretty much the set of basic types which is expected:

```c
\#include <stdio.h>

int main() {
	int i;
	char c;
	float x;
	i = 10;
	c = 'a';
	x = 1.2;

	printf("i = %d, c = %c, x = %f\n", i, c, x);
}
```

## Basic Functions:

### `getchar():`

- `getchar()` reads the next character (byte) from the "standard input"
    - return an `int` value
    - return `EOF` at the end of file

**Example:**

```c
\#include <stdio.h>

int main() {
	int i = 0;
	while (getchar() != EOF) {
	++i;
	}
	printf("%d chracters\n", i);
	return 0;
}
```

### `putchar():`

- `putchar( int c)` writes one byte to the "standard output"

**Example:**

```c
\#include <stdio.h>
\#include <limits.h>

int main() {
	int c;
	while ((c = getchar()) != EOF) {
		c += 3;
		if (c > CHAR_MAX) {
			c = CHAR_MIN + (c - CHAR_MAX);
		}
		putchar(c);
	}
}
```

# Control Structures

C and C++ have the usual control structures:

- `for`
- `while`
- `do` ..... `while`
- `switch`
- `if` .... `else`....
- `break`
- `continue`
- `return`

**Example:**

```
int f(int n) {
	int p, pp, r;
	switch(n) {
	case 0:
	case 1: return n;
	default:
		p = 1;
		pp = 0;
		do {
			r = p + pp;
			pp = p;
			p = r;
		} while (--n > 1);
		return r;
	}
}
```

# Memory Model

C talks with the memory directly. For instance as bellow:

![[../../Attachments/Untitled 9.png|Untitled 9.png]]

```
/* an int variable */
int i;
i = 5;

/* pointer to an int */
int * p;

/* pointer assigment */
p = &i;

/* pointer dereference */
printf("%d\n", *p);
```

![[../../Attachments/Untitled 1 3.png|Untitled 1 3.png]]

```
/* an int variable */
int i;
i = 5;

/* pointer to an int */
int * p;

/* pointer assigment */
p = &i;                      /*adress-of operator */

/* pointer dereference */
printf("%d\n", *p);          /* "*p" is object pointed-to by p */

*p = 13;
```

  

# Object and Pointers

- An **object** is an area in memory that holds a **value** of a certain **type**
    - e.g., an `int` , a `char` , a "structure", an array of `int`, and array of struct, ...
- A **pointer** is an **object** whose value is the **memory address of another object**
- Pointers are **typed** according to the object they point to

```
int * p;       /* pointer to an int */
int ** pp;     /* pointer to a pointer to an int */
char c;        /* a char variable */
int i;         /* an int variable */

p = &c;        /* type mismatch! */
p = &i;        /* okay */
pp = &i;       /* type mismatch! */
pp = &p;       /* okay */
```

## Pointer Objects:

- A pointer is like any other variable
    - it can be assigned a value (of a compatible _pointer_ type_)_
    - it can be "dereferenced" to read the "pointed" value
    - it can be "dereferenced" to write the "pointed" value

```
int main() {
	int i = 123;
	int * p; /* pointer declaration */
	p = &i; /* address-of operator */
	*p = 345; /* dereference operator */
	printf("i=%d\n", i);
	printf("*p=%d\n", *p);
}
```

## Uses of Pointers:

- Pointers causes **side-effects**
- at the same time they are _indispensable_

### Invalid Pointers:

- Pointers are "dangerous" because they can take a **restricted set of valid values**
    - values set by the platform
    - values themselves are _meaningless to the application_
    - in general, you can not check whether a pointer is valid

```
int * p;
*p = 345; /* dereference on invalid pointer */
```

- Dereferencing an invalid pointer causes **undefined behavior**

  

# Data Structures in C

## Basic Syntax:

```
struct date {
	int year;
	int month;
	int day;
};

void print_date(const struct date * d);
int main() {
	struct date moon_landing;
	moon_landing.year = 1969;
	moon_landing.month = 7;
	moon_landing.day = 20;
	print_data(&moon_landing);
}

void print_data(const struct data * d) {
	printf("%d%d%d\n", d->day, d->month, d->year);
}
```

Structures can be made as above, in which a new specific data structure is made in which you can make its own elements within that. This is why later, when you create a object of that structure, then its elements can be defined as well.

## Linked List:

**Definition:** an ordered set of data elements, each containing a link to its successor (sometimes its predecessor).

  

![[../../Attachments/Untitled 2 3.png|Untitled 2 3.png]]

  

M**aking the Linked List by element:**

```
/* linked list to represent a sequence of integers */
struct list_int {
	int value;
	struct list_int * next;
};

int main() {
	struct list_int L[4];
	struct list_int * l;

	l[0].value = 1;
	l[1].value = 2;
	l[2].value = 3;
	l[3].value = 4;
	
	l[0].next = L + 1;  /* &(L[1]); */
	l[1].next = L + 2;
	l[2].next = L + 3;
	l[3].next = 0;

	l = L;

	printf("value of the first element is %d\n", l->value);
	printf("value of the first element is %d\n", (*l).value);

	printf("value of the first element is %d\n", l->value->next->value);
	printf("value of the first element is %d\n", (*(*(*l).next).next).value);
}
```

  

**Making the Linked List by Input**

```
/* linked list to represent a sequence of integers */
struct list_int {
	int value;
	struct list_int * next;
};

struct list_int * read_ints_from_input() {
	int i;
	struct list_int * first = 0;
	while (scanf ("%d", &i) > 0) {
		struct list_int * new_elem = malloc(sizeof(struct list_int));
		new_elem -> value = i;
		new_elem-> next = first;
		first = new_elem;
	}
	return first;
}

int main() {
	struct list_int L[4];
	struct list_int * l;

	l = read_ints_from_input();

	printf("value of the first element is %d\n", l->value);
	printf("value of the first element is %d\n", (*l).value);

	printf("value of the first element is %d\n", l->value->next->value);
	printf("value of the first element is %d\n", (*(*(*l).next).next).value);
}
```