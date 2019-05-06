## Q 1,2,3,4,5,14

Q1 first nullable follow and predictor table

first -- first terminal in a string generated from this
non terminal

nullable this non terminal can generate a epsilon

follow first terminal after a nullable non-terminal


Nonterminal       First-set      Nullable-set      Follow Set

S (same as E first set) a       x               

E (same as T first set) a     x

T (same as first set of F) a      x             + *

F                 a           x               +,*


S' rule 0

    S   T  F   E

a   1  4,5 6,7 2,3

*

+

Q 2

S -> T x R  R -> e
T -> int    E -> NULL
T -> int*   E-> 0
R -> = E


symbol     stack    read    input     action
               0            int x ;   shift(int)
| int          0 4  int     x;         reduce(0)
T              0    int     x;         
T              0 8    int     x;
 T x           0 8 6  int x   ;         shift(x)
 T x R           0 8 6 5  int x   ;         reduce (5)

T x R ;  0 8 6 5 9 int x ;      e    shift(;)




3
x ** y
type checking

rule appropriate?

Q 5

lexing scanning

parsing

code generation

__ ** __

__ * *

"** " exp

term -> efactor

term -> term STAR efactor

term -> term slash efactor

term -> term percent efactor

efactor -> factor

efactor -> factor EXP efactor

code(efactor)


if rule == efactor -> factor {
  code(factor)
}else factor exp efactor {
  code(factor)
  push($3)
  code(efactor)
  pop($5)
  add $6,$3,$0
  slt $7,$6,$0
  add $3,$0,$0
  beq $11,$7,endExp_X
  add $3,$11,$0
  beginExpo_x
  beq $0,$6,endExpo-x
  mult $3,$5
  mflo $3
  sub $6,$6,$11
  beq $0,$0,beginExpo_x
  endExp_x

}
