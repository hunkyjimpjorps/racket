# About

## Basic values

The basic Racket *values* include numbers, strings, characters and booleans.

Racket numbers are either *exact* (an integer or rational number) or *inexact* (a floating-point number).  Racket also supports complex numbers of the form *a + bi*.  All of these are examples of valid Racket numbers:

```scheme
1       3.14
1/2     6.02e+23
1+2i    9999999999999999999999
```

Characters represent a single Unicode character.  `#\a` corresponds to the character **a**, `#\λ` corresponds to a lowercase lambda, `#\😎` corresponds to 😎, and so forth.

Strings are text written between double quotes.  Racket uses Unicode for strings, so any Unicode character can appear in a string.  Common "string escapes" like `\n` for a new line and `\"` for a double quote are valid in Racket strings.  Here are some valid Racket strings:

```scheme
"Hello, world!"
"Benjamin \"Bugsy\" Siegel"
"Roses are red\nViolets are blue\nAnd red and blue\nAre Racket's colors too"
"λx:(μα.α→α).xx"
```

The Booleans (truth values) are `#true` and `#false`, or `#t` and `#f` for short.  In Racket, any value that isn't `#f` is treated as if it were true.

Racket has many other kinds of values, but these are enough to get started.

## Calling a function

A function call starts with the name of the function, is followed by all of the *arguments* (inputs) it takes, and is wrapped in parentheses.  This is called an *S-expression*.

For example, to use the function `+` to add `1`, `2` and `3`, the S-expression we write to perform the function call looks like

```scheme
> (+ 1 2 3)
6
```

(In the examples in these concepts, the `>` indicates the input, and the following line is the output from Racket, as if we were using the DrRacket interactions window or the Racket REPL.)

If you try to do a function call on something that isn't a function, you'll get an `application: not a procedure` error.  In the example below, `(1 2 3)` raises an error because `1` is a number, not the name of a function.

```scheme
> (1 2 3)
application: not a procedure;
    expected a procedure that can be applied to arguments
    given: 1
```

## Binding a value to a variable name

To save a value to a name that we can reuse later, we use `define`:

```scheme
> (define length 10)
> (define width 5)
> (* length width)
50
```

## Defining a function

We also use `define` to define new functions.  The syntax is a little different: the first argument to `define` is the name of the function and the names of all the arguments it takes, wrapped in parentheses.

```scheme
> (define (double x) (* 2 x))
> (double 10)
20
> (define (three-sum x y z) (+ x y z))
> (three-sum 100 200 300)
600
```

Unlike some other languages, there is no `return` keyword in Racket.  The result of the final expression within the function definition is what's returned by the function.

## Comments

When Racket finds a `;`, it ignores everything after the semicolon until the end of the line.

To comment out a large block of text, surround it with `#|` and `|#`.

```scheme
#|
This is my surefire method for finding the perimeter of a rectangle.
I have to find so many rectangle perimeters in my job at the box factory.
This function has never failed me once.
(x and y are the lengths of the sides of the rectangle, by the way.)
|#

(define (rectangle-perimeter x y)
    (+ (* 2 x) (* 2 y))) ; I found this equation in my math textbook
```