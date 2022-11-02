# Programming in Erlang 2nd ed. Notes

`higher level function` - a function that returns function(s)

`fun` - Erlang anonymous function. Data type that represents a function

`arity` - the number of arguments a function accepts

[Term Comparisons](http://erlang.org/doc/reference_manual/expressions.html#term-comparisons) equal, not equal, etc...

`list-at-a-time` operation - doing a single operation on an entire list

- can be thought of as a single step in the program, simpler conceptually than thinking of each operation to each element as a single program step

## Functions that return `funs` (anonymous functions)

What is this code doing? 

```
31> Mult = fun(Times) -> (fun(X) -> (X+9) * Times end) end.
#Fun<erl_eval.6.99386804>
32> Triple = Mult(3).
#Fun<erl_eval.6.99386804>
33> Triple(2).
33
34> Triple(1).
30
```

`Mult` is a function that returns an anonymous function

When it gets invoked, 3 is the vaule assigned to `Times` because that's the value `Mult(3)` is invoked with

`Triple` when invoked then becomes the value of `X` because that it's the function returned by `Mult` with a method signature of `fun(X)`

## List Comprehensions

Syntax

```
[F(X) || X <- L].
```

Expl - the function of `X` where `X` is taken from `L`

The right side of `||` is the **pattern matcher**, and the left side of `||` is the **constructor**

## NEXT

p. 61