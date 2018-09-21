# SE212 Notes

## Lecture 2

|= entails/valid

|= p means P is valid where P is a wff(well-formed formula);

p1,p2,...pn |= Q

means from premises p1, p2, pn can conclude Q where p1,p2 are all wff

|- proves

p1,p2 ... |- Q means from p1, p2 ,pn can prove Q using a proof theory

may be multiple proof theories for same logic

Proof theories are methods that perform mechanical manipulations
on strings of symbols.

n. A proof theory is sound if P1, P2, . . . , Pn |- Q (proof)
then P1, P2, . . . , Pn |= Q (valid).

semantics transform them to deduced formulas

A proof theory is complete if P1, P2, . . . , Pn |= Q
(valid) then P1, P2, . . . , Pn |---- Q (proof).

proof theory unsound means cannot prove things

proof theory incomplete unable to have a proof

## propositional logic

also called sentential logic or boolean logic

transformational proof

natural deduction

semantic tableaux

The proposition symbols, and the constants, true and false,
are formulas. These are called prime propositions.

P is a prime proposition

contrapositive

p->Q means !Q->!p

prime if it is indecomposable .i.e snow is red

practice: 1. cold but not snowing

c & !s

2 neither snowing nor cold

!(s or c)

there are ambiguous statements


r means "it rains"

u means "i take an umbrella"

it rains unless I take an umbrella

P->q AND r;

p = f, q = f, r = t;

f IMP f = T

tautology if for all boolean valuatiosn p = true

The range of the semantic function for propositional logic is the
set of truth values: TF

A formula P is satisfiable if there is a Boolean valuation
such that [P] = T.

A formula is satisfiable if its truth table has some T’s in the last
column.

When a formula Q is a tautology, we write:|= Q

A formula P logically implies a formula Q if and only if
for all Boolean valuations, if [P] = T then [Q] = T.

P |= Q iff |= P ⇒ Q


A set of formulas P1, P2, . . . , Pn logically imply a
formula Q if and only if for all Boolean valuations, if [P1] = T and
[P2] = T, . . . ,[Pn] = T then [Q] = T.

A propositional formula A is a contradiction (or
falsehood) if [A] = F for all Boolean valuations.

A contingent formula is one that is neither a tautology
nor a contradiction.

# SE212 Tutorial 1

command of george start with #

```
#check PROP //syntax check for propositional logic

a => ((b & !c) | (b | (!d)))


formalize logic in george
a => b
a:= dog is barking
b:= dog is in the house
```


formalize logics

```
if dog in the house then someone is at the front door unless dog is not barking

a = dog in the house
b = someone at front door
c = dog is barking

a => b | !c

```

## Lec 4

soundness means that something is valid

complete really is true then a series of steps to prove it

satisfiable, contingent, tautology, contradiction

contingent means it is satisfiable

satisfiable maybe tautology , could be contingent


logically equivalent if for all boolean valuations p = q

p <=> Q

p <=> q iff |= p <-> q

<-> is a material equivalence , syntactic symbol

logical equivalence for <=>, semantic symbol


collection of forumlas is consistent if there is a boolean valuation

in which all formulas are true

r->s AND s -> -h AND r AND h

one evaluation where all is correct?

from truth table, no

p is not Q?

prove |= p<=>Q

## Tutorial Sep 19

P=>q p AND r |= q

p<=>q P OR NOT r |= q

p <=> q
= p AND q OR NOT p and NOT Q

which is
P => Q AND Q => P equivalence
(NOT P OR Q) AND (NOT Q OR P)
((NOT P OR Q) AND TRUE) AND ((NOT Q OR P) AND TRUE)
change TRUe to P OR NOT P  
