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

## Lecture Sep 25

natural deduction

b => c premise
prove !b | c

b | !b by lem

3) case b{
  c by imp_e on 1,3
  !b | c by or_i on 4
} case !b{
  !b | c by or_i on b
}
!b | c by cases on 2,3-5,6-7

may get premises don't match goal, check params

semantic tableux

consistent -- one boolean valuation where everything is true

it is a tree

either pick up one compound formula

or close a branch because it contains contradictory formulas

if all brnaches contains contradictory formulas then the premises are inconsistent

prove b&c,d, !(c&d) is an inconsistent set of formulas
|and_nb on|
4)b
5)c  not-and-bran 3

6) !c (closed on 5,6) 7 !d closed on 2,7 so inconsistent

a branch is closed if p and not p both appear on the path from root to leaf

1 r=>s
2 s=> !h
3 r
4 h

imp_br on 1
5 !r closed on 3 and 5 | 6 s impl branch 2
7 !s closed on 6,7 8 !h closed on 4,8

thus it is an inconsistent set of formulas

show valid, use a ST to show that premises and !Q is invalid

prove B | !b

1 !(b | !B)
not_or_nb on 1
2 !b
3 !!b //just closed on 2,3  
not_not_nb on 3
4 b
closed on 2,4

p, p <=> q |- q
1 p
2 p<=>q
3 !q


iff_br on 2
4 p & q 5 !p & !q
and nb on 4  and nb on 5
6 p        8 !p
7 q       9!q

closed on 3,7 closed on 1,8

invalid provide a boolean valuation in which premises are T and conclusion is F

## Lec Sep 27

Predicate logic

all p are q
x is p
therefore x is q

a,b |- c

refer to a value

symbolize both a claim and the value about which the claim is made

relations

unary predicates

ravi is an adult

adult(ravi)

round(earth)

duck(Esmerelda) ^ likes(E,water)
Everything likes Fridays

for all x likes(x,Fridays )

for some X rotten(x) AND in (x,Denmark)

something is rotten in the state of Denmark

for all x adult(x) ^ tall(x)

for all y happy(y) | hungry(y)

for all x child(x) => likes(x,micky)

northof(birthplace(E),Toronto)

for all x value("input") = x => value(output) = x^2

p(k(x,y,g(z)),h(x)) ^ q(x,c) both side well formed

terms describe values

for all x k(x,y,g(x)) not a well formed formula

for all x p(x,y) is a wff

for all x q(p(x)) no not a well formed formulas


everything doesn't like something

for all x exists y !likes(x,y)

!(for some x for all y likes(x,y))

for all x b(x) => g(x)

for some x b(x) => g(x)

older(x,y) means x is older than y

scope of qualifiers

free variable not in the scope of quantifier

for all x student(x) & likes(x,SE) => like(X,logic)


## Lecture Oct 2 2018

for all X rich(x) AND actor(x) => some Y valuable(Y) Collect(x,y)

3 (!(for all x) in（X，L）=> speaks(x,Fr) ) & (for all X in (X,L) => some Y knows(x,y) ^ speaks(y,Fr) ^ in(Y,L))

for all X some Y votes_for(x,y) everyone votes for someone

it is not the case that someone votes for every political party

!(for some X for all Y polParty(Y) => votes_for(x,y))

Check PRED

for all X INT some Y INT x >= Y

for all P PERSON likes(p,ice_cream)

exists some B flightlevel(b) > FL 290


## Lec Oct 4

if P is q(x) then P[y/x] is q(y)

iff P is for all X q(y,x) then p [4/y] is forall x q(4,x)
