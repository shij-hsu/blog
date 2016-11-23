### Lectures about Coq's

1. `return` 
```
(* ProofByReflection.v *)
Definition partialOut (P:Prop) (x:[P]) :=
match x return (match x with
            | Proved _ =>P
            | Uncertain =>True
            end) with
| Proved pf => pf
| Uncertain => I
end.
```
This keyword is used to determined the return **type** of the *[match ... with ... end]* syntax. Usually, a function has only one return type, but sometimes we need to definition e.g.-like functions, their return type is not unique, so we use `return` to declarate their vary return types.

2. `Hint`

> Hint Resolve length_O length_S.

We can apply these hints to prove something with `auto`. `Resolve` and `Immediate` have the same meaning for a premise-free hint.