# Debugging

Author: Peter Tse ([mcreng](http://www.github.com/mcreng))

### Introduction

This tutorial mainly goes through the skills required for debugging in C++11. During software development, bugs are inevitable, and debugging skills can help trace the locations of errors. Main types of bugs include

* Compilation Errors,
* Linking Errors,
* Runtime Errors, and
* Logical Errors

### Compilation Errors

Compilation errors can be discovered when you compile your program. It is shown under both 'Problems' and 'Console' section in Eclipse.

#### A Simple Example

```C++
#include <iostream>

using namespace std;

int main() {
  cout << "Hello World" << endl
}
```

This program cannot be compiled because of a missing colon. 

![img](https://i.imgur.com/BZ6np7L.png)

![img](https://i.imgur.com/g1tTQaQ.png)Error messages are helpful but sometimes could be ambiguous. In that case, Google search the error would help.

To locate the error, you can either

* Go to 'Problems' tab, and double click on the error, or
* Go to 'Console' tab, and double click on the error (red line).

Both of the approaches allow you to go to the line and fix the error.

#### Exercises

In the following questions, locate the errors and the fix.

##### Question 1.

```C++
#include <string>
#include <iostream>

int main() {
  std::string name = 'Smart Car';
  std::cout << name << std::endl;
}
```

##### Question 2.

```C++
#include <iostream>

int main() {
  int a[] = {1, 2, 3, 4, 5};
  cout << a[4] << endl;
}

```

##### Question 3.

```C++
/* foo.h */
#ifndef FOO_H_
#define FOO_H_

class Foo {
public:
  int x;
  Foo(int x) : x(x){}
  Bar toBar() { return Bar(x); }
};

class Bar {
public:
  int x;
  Bar(int x) : x(x){}
  Foo toFoo() { return Foo(x); }
};

#endif /* FOO_H_ */
```

```C++
/* main.cpp */
#include <iostream>
#include "foo.h"
using namespace std;

int main() {
  Foo foo(2);
  Bar bar = foo.toBar();
  cout << bar.x; // expected 2
}
```

### Linking Errors

Linking errors are reflected by linker, which usually occur when working with multiple source files. Linking errors sometimes are not reflected under 'Problems' tab, so it's best to check the 'Console' tab if any error occurs.

#### Example

```C++
#include <iostream>
using namespace std;

int fun();

int main() {
  cout << fun() << endl;
}
```

The linker could not find a definition to `fun()` so it returns an error.

![img](https://i.imgur.com/j1PqFkE.png)

![img](https://i.imgur.com/CS9oMYz.png)

The common error returned by linker is 'undefined reference', but it is not useful in telling you what is wrong.

#### Exercises

##### Question 1.

There are two linking errors in this question.

```C++
/* foo.h */
#ifndef FOO_H_
#define FOO_H_
#include <iostream>
using namespace std;

class Foo {
public:
  Foo();
  void print() { cout << foo_number << endl; }
  static int foo_number;

};

#endif /* FOO_H_ */
```

```C++
/* main.cpp */
#include <iostream>
#include "foo.h"
using namespace std;

int main() {
  Foo foo;
  foo.print();
}
```

### Runtime Errors

Runtime errors cannot be discovered upon compilation/linking. It can only be found when your program runs and crashes unexpectedly. To debug these errors, we will have to run the program in 'Debug' mode.

#### Example 1

```C++
#include <iostream>
#include <vector>
using namespace std;

int main() {
  vector<int> v;
  cout << v[0] << endl;
}
```

The program crashes unexpectedly.

![img](https://i.imgur.com/Fb2HWbB.png)

Note that when programming K60/KEA, if the program crashes, the prompt is different. It could be

![img](https://i.imgur.com/89BqUXk.png)

breaking into watchdog(WDOG) interrupt(IRQ) handler, it could be

![img](https://i.imgur.com/vd97Jqz.png)

breaking into `assert.c`, or even

![img](https://i.imgur.com/0bhyhvX.png)

breaking into `vectors.c`. 

Anyway, if you encounter one of the above situations (or any other, such that you suspect it is runtime error), you should run your program in 'Debug' mode.

Inside 'Debug' mode, you should find a 'Debug' tab.

![img](https://i.imgur.com/XE8qbMx.png)

If you did not change any settings in Eclipse, when you run the program in 'Debug' mode, it sets a breakpoint at the first line of `main()`. You can see the current status of the program in `Thread #1 0 (Suspended : Breakpoint)`. The program is now being suspended by the initial breakpoint.

After clicking 'Continue', the program reaches the point where it crashes.

![img](https://i.imgur.com/o2zJl3t.png)

The debugger suspends the program before it crashes so you can see where the fault is. Now the status read `SIGSEGV:Segmentation fault` at `main.cpp:7`, which means at line 7 in `main.cpp`, it triggers a segmentation fault. Segmentation faults happen during illegal memory access or manipulation, and in our example we are accessing an illegal entry of the vector, which results in the crash.

In K60/KEA, the trace back in 'Debug' tab could be long.

An example of `HardFaultHandlerC()` at `vectors.c`:

![img](https://i.imgur.com/Wul40Cv.jpg)

An example of `__assert_func()` at `assert.c`:

![img](https://i.imgur.com/XJrxnDy.png)

The trace back usually includes details of STL and libsccc, and since you can safely assume they do not contain bugs, you should go from top to bottom to locate the functions that are written by you.

If you get the following trace back, good luck...

![img](https://i.imgur.com/Od13Rva.png)

Without any details you need to run the code line by line and locate the source of error.

#### Example 2

Consider the following code which calculates the slope of the line normal to the line passing through `(x1, y1)` and `(x2, y2)`.

```C++
#include <iostream>
using namespace std;

int findSlope(int dx, int dy) {
  return dy/dx;
}

int main() {
  int x1 = 2, y1 = 3;
  int x2 = 10, y2 = -1;
  int m = -1/findSlope(x1-x2, y1-y2);
  // Finds the slope of normal line
  cout << "Slope = " << m << endl;
}
```

The program crashes and **assume** that you cannot look at the trace back at 'Debug', we will find out the problem by going through the code line by line.

![img](https://i.imgur.com/6rSi4Nm.png)

Instead of clicking 'continue', we use the three buttons (inside the red box) instead. They are (from left to right), 'Step into', 'Step over' and 'Step return'. If you wish to go to the next line of execution, press 'Step over'.

![img](https://i.imgur.com/cF4sj6i.png)

Nothing abnormal up until now, let us 'Step over' once more.

![img](https://i.imgur.com/aYPhtZw.png)

Here we reach a function `findSlope()`, we wish to see if there is anything wrong so we 'step into' the function.

![img](https://i.imgur.com/yCWHItg.png)

We then reach the line inside of the function. Now I wish to check the values of `dx` and `dy` and see if there would be a division by zero. You can hover on `dx` and `dy` and you can see the values.

![img](https://i.imgur.com/bHgTDUt.png)

![img](https://i.imgur.com/dtes5Zj.png)

Still nothing abnormal. Now let us use 'Expressions' to see if `dy/dx` gives our expected value of `-0.5`.

![img](https://i.imgur.com/aMSJ5Wm.png)

Here you may keep track of some variables/expressions during debugging. Note that only the variables visible in current scope is readable.

![img](https://i.imgur.com/Uuw4tIA.png)

Here we can see that `dy/dx` is not giving the same value as intended (because of int/int division). Now we know one logical bug but since the program has not crashed, we will go on. Also note the the variable `x1` is not visible here since the scope is not correct.

Now by clicking 'step return', we return to `main()`.

![img](https://i.imgur.com/pXzCQsI.png)

The expressions except `x1` are now not readable.

![img](https://i.imgur.com/I4srZzB.png)

Now we know the program crashes because of division by zero. We can verify this by adding `-1/findSlope(x1-x2, y1-y2)` into 'Expressions' and see.

![img](https://i.imgur.com/7cCAnLU.png)

And expectedly, by clicking 'step over' once more, the program crashes.

![img](https://i.imgur.com/xI8yCu9.png)

### Logical Errors

Logical errors are the hardest to detect since the problem lies within your algorithm. You might want to use the debugging tools mentioned above and see if the algorithm runs like what you expected. We could not tell you much because the algorithms are written by you!