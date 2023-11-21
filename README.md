# Haskell for Imperative Programmers

## Basics

### Prerequisites

- Imperative programming (C, C++, Python, Java)
- Basic theory on programming language (Types, Evaluation, Compilers, Interpreters)
- Haskell Toolchain (ghc, ghci, cabal)

### Functional Programming

- Pure (mathematical) functions
  They have input some arguments and have a result and nothing else.
- Immutable data
  Our data types cannot be changed in place.
- No/Less side-effects
- Declarative
  Instead of imperative
- Easier to verify

### Declarative vs. Imperative

```
sum [] = 0
sum (x:xs) = x + sum xs
            or
sum = folder (+) 0
```

```
int sum(int *arr, int length) {
    int i, sum = 0;

    for (i = 0; i < length; i++) {
        sum += arr[i];
    }

    return sum;
}
```

In the imperative step (the 2nd one), for each step we do we tell the program what to do. So we say set the sum to 0, then set i to 0, then iterate till a certain condition is met and take every single value of that array which is dependant on the i index then add it to the sum, then return the sum.
So at no point do we give it a definition of what it means to be a sum or what a sum actually is. We just describe an algorithm that can produce a sum.

In the declarative approach, we actually define or sort of define what it means to have a sum. The sum of an empty list is just 0, and a sum with a list with at least one element x is that element x plus whatever the rest of the sum is. Using some fancy tricks like partial function application and the folding function we can have a much shorter function definition.

### Lazy vs. Strict

```
func arg =
    let x = func1 arg
        y = func2 arg
        z = func3 arg
    in
    if z then x else y
```

```
int func(int arg) {
    int x = func1(arg);
    int y = func2(arg);
    int z = func3(arg);

    if(z) {
        return x;
    } else {
        return y;
    }
}
```

Haskell is Lazy evaluated, lazy evaluation is something you need to get your head around when working in haskell.

The 2nd code block is Strictly evaluated, lets assume the functions func1,2,3 all take one year to finish.
A strictly evaluated language let for example C or Java. The 2nd code block would take 3 years to finish, because we evaluate one which will take a year then 2 then 3.

How does it work in Haskell being lazy evaluated, then it works like this. We have the definitions x,y,z on the left and those are defined as the result of certain functions.
Now the are not evaluated right when they occur in the code, they don't have to right now. Haskell looks at what has to be evaluated in order to get the result. Firstly it observes that it needs z otherwise the if doesn't work, so it does z which takes one year and then we either evaluate x or y based on the z statement, this algorithm will only take 2 years.

Those are the basics of haskell.

### How to uninstall Haskell

https://comp.anu.edu.au/courses/comp1100/resources/install/macos/
