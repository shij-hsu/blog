## Notes about Coq's

[TOC]

### return
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

### Hint
> Hint Resolve length_O length_S.

We can apply these hints to prove something with `auto`. `Resolve` and `Immediate` have the same meaning for a premise-free hint.
> Hint Extern 1 (sum _ = _) => simpl.

The command to register a custom hint. That is, we provide a pattern to match against goals during proof search. Whenever the pattern matches, a tactic (given to the right of an arrow =>) is attempted. Below, the number 1 gives a priority for this step. Lower priority are tried before higher priorities, which can have a significant effect on proof search time.

### decide equality

This tactic solves a goal of form `forall x y:R, {x=y}+{~x=y}`, where R is an inductive type such that its constructors do not take proofs or functinos as arguments, nor objects in dependent types.


### compare term1 term1

This tactic compares two given objects `term1` and `term2` of an inductive datatype. If G is the current goal, it leaves the sub-goals `term1 = term2 -> G` and `~term1 = term2 -> G`. The type of `term1` and `term2` must satisfy the same restrictions as in the tactic decide equality.


### congruence

```
Coq < intros.
1 subgoal
H : a = f a
H0 : g b (f a) = f (f a)

H1 : g a b = f (g b a)
============================
g a b = a
Coq < congruence.
No more subgoals.
```
*congruence tries to prove that a hypothesis is equal to the goal or to the negation of another hypothesis.* So it likes repeating rewrite tactics?

### autorewrite 

See the code in coq/tac/autorewrite.v

Tactic `autorewrite with db in *` does rewriting in hypothesis, as well as in the conclusion. See it in coq/cpdt/ProofSearchByLP.v.

### || 

See the code also in coq/tac/autorewrite.v. 

Tactic `exp1 || exp2` is equivalent to `first [progress exp1 | progress exp2]`.

### specialize 

`specialize (ident term1 term2 ... termn)` is equivalent to `assert(ident' := ident term1 term2 ... termn); clear ident; rename ident' into ident`

### idtac 

What the fuck tactic means? I think it's trivial.

### fail 

It always fail. It is useful for defining other tacticals since it can be caught by try, repeat, match goal, or the branching tacticals. The fail tactic will, however, succeed if all the goals have already been solved.

`fail n`, the number n is failure level.

### solve 

`solve [exp1 | exp2 | ... |expn]` use tactics `expi` to solve the goal by order. If all the tactics fail, the tactic fail.

### search 

This command displays the name and type of all objects (hypothesis of the current goal, theorems, axioms, etc) of the current context  whose statement contains qualid . This command is useful to remind
the user of the name of library lemmas.

### fresh 

*The expression `fresh component .. component` returns an identifier, it evaluates to an identifier unbound in the goal.*

**What does it mean???**  WHY follow code is wrong in Coq?

```
Theorem t5' : (forall x:nat, S x > x ) -> 2 > 1.
  intros H.
  let H':=fresh "H" in apply (H' 1).
  ------------------------------------------
  Error: The variable H0 was not found in the current environment.
```

### Instance

The Instance command is used to declare a type class instance named ident of the class Class with parameters t 1 to t n and fields b 1 to b i , where each field must be a declared field of the class.

```
Instance LS: listspec _list _tail.
Proof. eapply mk_listspec; reflexivity. Defined.
```

