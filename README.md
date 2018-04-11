# J
# JOD: Shan & Maxim 9

### **PLEASE NOTE: WE'RE ONLY POSTING WHAT WE COVERED IN CLASS**

---

### **Throughout this turtorial, you can either [download J](http://code.jsoftware.com/wiki/System/Installation) or use this convenient [online version](https://tio.run/#j)**
### **If you use the online version, add `echo` before each code tidbit or else outputs won't be displayed.**

---

## Backjround and jeneral info

J was created in early 1990s.
J is considered to be extremely terse and difficult to use by most programmers.

- a notational programming language designed for interactive use
- an array language; data is universally structured as rectangular arrays 
- a functional language: creation and composition of functions is emphasized 
- object-module and imperative techniques are supported, but not required

 There will some code later to show why it’s so hard to transition into using. 

## Where did it come from? 

It is a synthesis of APL and the FP and FL function-level languages created by John Backus. While project leader with IBM Backus developed in the early 1950's with his team Fortran -- Formula Translator, the first widely used high-level programming language. He also created BNF (Backus Normal Form or Backus–Naur Form), a metalanguage used to describe other languages. 

- APL: A Programming Language. 1964. Main datatype is multidimensional Array, influenced many languages
- FP: Functional Programming. 1977  The de facto standard for functional programming. 
- FL: Functional Level. Successor of FP

## What is it used for?	

J is extremely strong in the mathematical, statistical, and logical analysis of data. It is also extremely terse, in that everything it does is highly compact. For example, code which could take multiple lines in Java or Python, can be done in 5 characters in J.

Because it’s so terse, J is not often used in production of code. It is most often used by people for personal/internal use, but not for any situation where you would want someone to be able to read or speak it, simply because there is so much info in so few characters.

It’s great for math and science computations! (eg Project Euler)

## Try this!
## Averaging

Make your code! Pick whatever language you want, and define a function for average in the fewest amount of characters/lines possible. Then get the average for [0,4].

You have 3 min. - [here's some music to listen to](https://www.youtube.com/watch?v=bNiRqE4vudA)

## AveraJe

```j
  avg=: +/%#
  avg i.5
2
```

## Grammar

J features 3 kinds of syntax - verbs, operators, adverbs.

Nouns are “things”, like numbers and characters, as well as arrays and their atoms

“Ordinary” functions compute numbers from number - these are verbs. Think + and * . 

Some functions compute functions from functions. These are operators. 

Adverbs are a special kind of operator which only takes one argument to the left of it. 

“Verbs modify things and adverbs modify verbs”.

## Examples of Verbs and Operators

`+ , - , * , %` . Your normal, everyday mathematical operation are all verbs. This includes `|` , the residue function. It does the opposite of mod, so 2 `|` 7 would return 1. 

`/` and `~` are examples of adverbs. +/ was used in the average function. `/` is the insert operator - it “inserts” the preceding verb into the given list. So `+/` 1 2 3 would turn `+` into a list summing verb, and evaluate the list as `1 + 2 + 3`. `~` exchanges the left and right arguments, so 2 `|` 7 is the same as 7 `|~` 2. 

![~](http://www.jsoftware.com/help/learning/diag03.gif)

## Monads and Dyads 

Functions can have 2 arguments, one to the right or one to the right AND left. Monads only accept ones to the right,

![monad](http://www.jsoftware.com/help/learning/diag01.gif)

Dyads accept both. 

![dyad](http://www.jsoftware.com/help/learning/diag02.gif)

Many functions act as both. For example: 


Functions can have 2 arguments, one to the right or one to the right AND left.
Monads only accept ones to the right, Dyads accept both. Many functions act as both. For example: 

2 `-` 1 is subtraction. `-` as a Dyad.   `-` 1 is negation.( negative 1 is displayed as `_1`) `-` as a Monad.
 
3 `%` 4 is division. `%` as a Dyad. `%` 4 is reciprocal. `%` as a Monad. 

`>:` is increment by 1 as a Monad. It is larger or equal too as a Dyad.

`*:` 2 is the square function, and would return 4. Its is Monadic only. 

## So, how did averaje work?

(V1 V2 V3) N is interpreted as (V1 N) V2 (V3 N) 

If V1 and V3 are monads (`+/` and `#`) and V2 is a dyad( % %), it is called a fork, and interpreted that way. 

![fork](http://www.jsoftware.com/help/learning/diag08.gif)

`+/` uses the adverb `/` to find the sum of the list. `#` is a verb called tally which finds the number of things in a list, and `%` will divide the two. 

 Hence we have: `(1 + 2 + 3 + 4) % (4)`

## Euler’s Problem #1

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

## Euler’s Problem#1 With J (Solution)
### Yes, there are other possible solutions ([Here are a few of Hank's](http://www.hakank.org/j/)), but this one is most intuitive.

```j
  +/ (i.1000) * (0 E. 3|i.1000) +. (0 E. 5|i.1000)
233168
```

## Euler’s Problem#1 With J (BreakDown)

### Note: the `...` means it goes on, but isn't dislaying due to convenience (displaying 1000 numbers is sort of bad)

Create an array of 1000 i.e. [0-999]

```j
  i.1000
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 
49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88...
```

---

Calculate module 5 of each element

```j
  (0 E. 5|1000)
1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 
0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 ...
```

---

Calculate module 3 of each element

```j
  (0 E. 3|1000)
1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 
0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 0 1 0 ...
```

---

Combine the modulos using the OR operator `+.`

```j
  (0 E. 3|i.1000) +. (0 E. 5|i.1000)
1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 0 1 1 0 1 0 0 1 0 0 1 0 1 1 0 ...
```

---

Multiply the resulting array with another array of 1000 elements i.e. the [0-999] array

This will multiply each number by 0 if not divisible by 3 OR 5, or by 1 if divisible by 3 OR 5

```j
  (i.1000) * (0 E. 3|i.1000) +. (0 E. 5|i.1000)
0 0 0 3 0 5 6 0 0 9 10 0 12 0 0 15 0 0 18 0 20 21 0 0 24 25 0 27 0 0 30 0 0 33 0 35 36 0 0 39 40 0 42 0 0 45 0 0 48 0 50 51 0 0 54 55 0 57 0 0 60 0 0 63 0 65 66 0 0 69 70 0 72 0 0 75 0 0 78 0 80 81 0 0 84 85 0 87 0 0 90 0 0 93 0 95 96 0 0 99 100 0 102 0 0 ...
```

---

Now we just summate each element from the resulting array using `+`. And we're left with our final solution.

```j
  +/ (i.1000) * (0 E. 3|i.1000) +. (0 E. 5|i.1000)
233168
```

