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

## Lec Oct 11

genuine variable -- any value, universal quantification yields a formula true

unknown variable -- a specific but unknown value

g when genuine and u when unknown

exists_i

for all x P(f(c),x)
for some Y all x p(f(y),x)

forall_i

for every Xg {
  P(xg/x)
}
forAllX . p

exists_e

some X . P

for some xu P[xu/x]{
  Q
}
Q

e.g

for all x P(x) => q(x)

forall X p(x)

prove forall X q(x)

for every xg {
  p(xq)=>Q(xq)
  p(xq)
  q(xq)
}

forall x q(x)

for all X p(x)
for every xq {
  P(f(xq))
}

for all x p(f(X))

for all x for all y p(x,y) => for all y for all x p(x,y)

assume {
  for every yq {
    for every x q {
      for all y p(xq,y)

      p(xq,yq)
    }
    for all x p(x,yq)
  }
  for all y for all x p(x,y)
}
proves the imp by imp_i on 1-7

for all x p(x,x) |- for all x exists y p(x,y)

for all x p(x,x)

for every xg {
  p(xg,xg)

  exists y p(xg,y) by exists_i
}
for all x exists y p(x,y) by for all_i on 2-4

for all x p(x) => q(x), exists x. P(x) |- exists x Q(x)
1)for all x p(x) => q(x)
2)exists x. p(x)
3) for some xu P(xu){
  p(xu) => q(xu)
  q(xu)
  some x q(x) by exists_i on 5
}
for some x Q(X)

some x p(x) |- not (for all x !p(x))

1) some x . P(x)
2) disprove for all x !p(x){
  for some xu p(xu){
    !p(xq) by forall_e on 2
    false by not_e on 4,5
  }
  false by exists_e on 1,4-6
}
not for all x !P(x) by raa

!(some x P(x)) |- for all x !P(x)
1) premise
for every xq{
disprove p(xq){
  exists x P(x) by exists_ion3
  false not_e
}
!P(xq) by raa


}
for all x !p(x)

!(for all x p(x)) |- some x !p(x)

disprove !(some x !p(x)){
  for every xq {
    disprove !p(xq){
      some x !P(x) by exists_i
      false by not_e
    }
    p(xq)
  }
  for all x p(x)
  false
}
some x not P(x)


all x some y !w(x,y) |- !(some x all y w(x,y))

premise

disprove some x all y w(x,y){
  some xu all y .w(xu,y){
    some y !w(xu,y) by forall_e
    for some yu !w(xu,yu){
      w(xu,yu) by forall_e
      false
    }
    false by exists_e
  }
  false by exists_e
}
raa prove


semantic tableaux

some x p(x) |- !(for all x . !P(x))

some x P(x)
!!(...)
by not not nb on 2
for all x ! p(x)
by exist_nb
p(xu)
by for all_nb on 3
!p(xu)
closed on 4,5


## Lecture OCT 16

sample midterm

likes(a,b)
or likes_ice_cream(a)

need to match

e.g

for all x,y. line(x) & line(y) & parallel(x,y) ^ !(x == y) =>
!(exists P point of(x,p) & pointof(y,p))

for all x. twoline(x) & parallel(x) & notidentical(x) => nopoints in common(x)

for all x. twolines(x) & parallel(x) & notidentical(x) => !intersect(x)

for all x. twolines(x) & parallel(x) => noptsincommon(x) OR allptsincommon(X)



hidden premises

i.e one man can't be at 2 places at the same times

two constants are not the same

hidden premise 1 for all x ,y,z,w 10cn(x,y,w) & 10cn x,z,w => y = z
hidden premise 2 !(J = GS)
for all x,y,z cc(x,y,z) => 10cn(x,y,z)

disprove cc(B,GS,6){
  5)cc(B,gs,b) => 10cn(b,gs,6) by for all_e on hp1
  6)10cn(b,gs,6) by imp_e on 4,5
  7)10cn(B,J,6) & ....
}

exists x. age(x) != 10

prime(5)

exists x. soln(x)

for all x. soln(x) & soln(y) => x = y

(exists x. soln(x)) & (forall x,y . soln(x) ^ soln(y) => x = y)

only formalization

likes(A,b) & for all x likes(A,x) => x = b

lieks(A,bic) & for all x likes(X,bic) => x = alice

reflexivity

t=t eq_i

for all x .P(x) <=> x = b

|- P(b) & for all x y p(x) & p(y) => x = y

for all x p(x) <=> b
p(b) <=> b = b by forall_e on 1
b = b by eq_i
p(b) by iff_imp on 2,3

for every xg {
  for every yg {
    assume p(xg) & p(yg){
      p(xg) by and_e
      p(yg)
      p(xg) <=> xg = b by forall_e
      xg = b by iff_imp
      p(yg) <=> yg = b
      xg = b by iff_mp
      yg = b by iff_mp
      xg = yg by eq_e on 11,12


    }
  }
}


## Lecture Oct 18

show following argument not valid

exists x. p(x) & q(x), p(A), A = B |= q(b)

premise true conclusion false

domain

mapping
