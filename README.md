# J
# JOD: Shan & Maxim

### **PLEASE NOTE: WE'RE ONLY POSTING WHAT WE COVERED IN CLASS**

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

## Monads and Dyads 

Functions can have 2 arguments, one to the right or one to the right AND left. Monads only accept ones to the right, Dyads accept both. Many functions act as both. For example: 


Functions can have 2 arguments, one to the right or one to the right AND left.
Monads only accept ones to the right, Dyads accept both. Many functions act as both. For example: 

2 `-` 1 is subtraction. `-` as a Dyad.   `-` 1 is negation.( negative 1 is displayed as `_1`) `-` as a Monad.
 
3 `%` 4 is division. `%` as a Dyad. `%` 4 is reciprocal. `%` as a Monad. 

`>:` is increment by 1 as a Monad. It is larger or equal too as a Dyad.

`*:` 2 is the square function, and would return 4. Its is Monadic only. 

## So, how did averaje work?

(V1 V2 V3) N is interpreted as (V1 N) V2 (V3 N) 

If V1 and V3 are monads (`+/` and `#`) and V2 is a dyad( % %), it is called a fork, and interpreted that way. ![fork](http://www.jsoftware.com/help/learning/diag08.gif)

`+/` uses the adverb `/` to find the sum of the list. `#` is a verb called tally which finds the number of things in a list, and `%` will divide the two. 

 Hence we have: `(1 + 2 + 3 + 4) % (4)`

## Euler’s Problem #1

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

## Euler’s Problem#1 With J (Solution)
### Yes, there are other possible solutions, but this one is most intuitive.

```j
  +/ (i.1000) * (0 E. 3|i.1000) +. (0 E. 5|1000)
233168
```

## Euler’s Problem#1 With J (BreakDown)

Create an array of 1000 i.e. [0-999]

```j
  i.1000
```








```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```
