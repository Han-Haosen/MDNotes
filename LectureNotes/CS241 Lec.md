# Lecture 2

Assmebly language and Machine code

single statement in Al is a single statement in machine code.

MIPS 32 32-big architecture

lis $1 .word 10 //load constant 10 into reg 1

lis $2 .word 15

add $3,$1,$2

jr $31 //terminate jump register

lis = load immediate and skip

uses registers



for MIPS 32, 32 registers $0 to $31

$31 is return address and $0 is always zero

opcode designate operation, operands designate data sources and destination

5 bits to specify 32 registers

add $d, $s, $t

means

0000 00ss ssst tttt dddd d000 0010 0000

sub changes the 0010 0000 to 0000 0000

## Addresses manipulation

lis $d .word i

load constant i into register $d

store value i aftre lis $d instruction

Program Counter-- hold address of current instruction

instruction Register -- holds the instruction being executed

ALU -- performs arithmatic and logic operations

general purpose registers $S1 etc

branch if equal beq

branch if not equal bne

set if less than for signed integers slt

set if less than for unsigned integers sltu

beq $s,$t,i

branch if equal

compares contents of s and t

if equal skip i instructions

similarly bne $s,$t,i means if not equal

fetch first instruction would be fetched from RAM location 0x1000 and stored in IR

when an instruction is done, PC incremented by 4 bytes

MIPS each instruction is 4 bytes long

skip over, add a multiple of 4 to PC

go backward (say in a while loop) :subtract off some multiples of 4

start executing set PC to the address

bne $s,$t,i means if (s!=t) PC += i * 4


Slt :

slt $d,$s,$t

compares s and t,

if $s < $t then set $d i.e d = 1
if $s >= $t then reset $d d = 0

reverse it you can have 4 combinations



lw $t, i($s) load word from Mem[$s+i] into $t

$s+i must be word-aligned

sw $t, i($s)

store word from register $t into Mem[$s+i]

## Multiplication and Division

operatios uses hi, lo register

mult $s, $t

place the most significant 32 bits in hi

place least significant 32 bits in lo

only need to consider lo register so far

div $s $t

divides $s by the contents of $t and place quotient in lo, remainder in hi

mfhi $d copy contents of hi to $d

mflo $d  copy contents of the lo register to $d

# Actual Lecture

Assmebly are low level English-like instructions

then convert to machine language

assemblers turn assembly into machine code

loader

operate on data

computer programs are also datas

von Neumann architecture

programs reside in the same memory as data they operate on

possible to write programs that manipulate other programs

operating system operate other programs/viruses



how do we know whether memory contains machine instructions or data?

we don't

what does a machine instruction look like?

machine instructions are specific sequence of 1 and 0

many different machine languages

processor specific


MIPS instructions, not the full but a subset of it


## Lecture Sep 13

Recall: $31 is the special used to store address

need to set PC to $31 -- jr $31

add value in register $s to reg 7, store result in reg 3 and return

add $3,$5,$7 //0000 0000 1010 0111 0001 1000 0010 0000
//3 is 00011 5 is 00101 7 00111
jr $31 // 0000 0011 1110 0000 0000 0000 0000 0100


$0 always 0

lis $d // load immediate and skip
treat next word as an immediate value
.word i

//similar to addi $d, $0, i

lis // need to skip here

immediate value is not an instruction

lis $5 //0
.word 42 //4
lis $7 //8
.word 52 //c
add $3,$5,$7 //10
jr $31 //14

Assembly :

replace 1/0s with instructions

easier to use mnemonics

help you debug your codes

translation can be automated

one line of assembly = one machine instruction

32 bit word

computes abs value of $1, store in $1 and return

2 cases: negative and non-negative

some instructions modify the PC to jump around

branches and jumps

eg. jr and beq/bne

branch if two registers have equal contents

if two registers have equal contents

if equal increment PC by given number of words

can branch backwards

also bne branch if not equal

slt "set less than"

slt $a,$b,$c  a = 1 when b < c

slt $2,$1,$0 -- to check if $1 is smaller or larger than $0

sub $1,$0,$1 // negative number where

only if negative

slt $2,$1,$0
beq $2,$0,1
sub $1,$0,$1
jr $31


add $3 $0 $0 to initialize

use labels

e,g label: operation operand

foo: add $3,$3,$2

bne $2,$0,foo

foo-- memory address for the next instruction

looping and store

lw $a, i($b)  load word

contents into $a, go to memory stored in $b + i

arrays

$1 = address of an array
$2 = # of elements in an arrays
place elemenet at 5 in $3


lw $3, 20($1)

lis $5
.word 5
lis $4
.word 4
mult $5,$4

need hi and lo

# Lecture Sep 18

mult $a $b

product is 64 bits

too big to handle so use hi and Lo

2 special register

$a*$b => hi:lo

special instructions

mf lo $a move from lo to $a
mf hi $a move from hi to $a

hi stores the remainder for division

low stores the quotient

implementing a procedure f

call and return

how do we transfer control into and out of f?

what if f calls another procedure g

how do we pass in parameters?

what if f that we call overwrites data another procedure is using?

implement the call stack

keep track of what is in use

MIPS $30 initialized by the loader
to just passed the last word in memory

we can use $30 as a bookmark to separate used
and unused RAM if allocate from the bottom

f calls g, g calls h, h returns, g returns , f returns

f registers

g registers

g calls h , save h Registers

use RAM to save content of registers we want to use

strategy :

each procedure stores in RAM

the registers it wants to use

and restores them when return

RAM used LIFO => Stack

$30 is a stack pointer that contains the address of the top of the stack

Templates:

f:sw $2,1($30)
sw $3, -8($30)

two registers into RAM

push regs $2 and $3 into RAM

lis $3
.word 8
sub $30 $30 $3 //decrement stack pointer $30
place body of f here
add $30,$30,$3
lw $3, -8($30)
lw $2, -4($30)


call: main:
lis $s
.word f ;addr of line lablled f
jr $s  ;jump
(HERE)
f: ;address of that line in memory
return?

need to set PC to the line right after jr

i.e here

jalr

jump and link to the current register

save $31 on the stack too

main:
lis $5
.word f
sw $31, -4($30)
lis $31
.word 4
sub $30,$30,$31
jalr $5
lis $31
.word 4
add $30,$30,$31
lw $31, -4($30)
jr $31

jr $31

parameter and result passing

generally use Registers //so write docs about it

too many then use Stack

e.g Proc sum to N

sum to N adds numbers 1 .. N

$1 working
$2 input
$3 output

sum1toN
sw $1,-4($30)
sw $2 -8($30)
lis $1
.word 8
sub $30,$30,$1
lis $1
.word -1
add $3,$0,$0
topofLoop :add $3,$2,$3
add $2,$2,$2
bne $2,$0 topofLopp

lis $1
.word 8
add $30,$30,$1
lw $1,-4($30)
lw $2 -8($30)
jr $31

I/O output sw to 0xffff000c

prints least significant byte to screen

input : lw from 0xffff0004
next character from std in will be the least significant byte


Quick E.g

lis $1
.word 0xffff000c
lis $2
.word 67
sw $2,0($1)


# Lecture Sep 20

Assembler

input assembly, out put machine

analysis and synthesis

analysis - understnad the meaning of source strings
synthesis output equivalent machine

assembly file - stream of characters

group characters into meaning tokens

asm.cc

your job:

  group tokens into instructions
  output equivalent machine code
  anything else is Error -- to stderr

Big problem :
  beq $2,$1,here //how to branch things?? recognize labels?
  standard sdn?

group tokens into instructions
record addresses of all labelled instructions "symbol table"
-list of (label, address) pairs

a line of assembly may have multiple labels

f:
g:

mult $1,$2

translate each instr to machine code:

lookup labels as required

output assembled MIPS to stdout

output symbol table to stderr

ex:

  main: list $2
  .word 13
  top:
  add $3,$0,$0
  lis $1
  .word -1
  add $2,$2,$1
  bne $2,$0,top
  jr $31
  Beyond:

pass 1
group tokens
build symbol table
first label (main, 0x0)
second label (top, 0xc)
beyond:(0x24)

pass 2
translate each instruction

lis $2 0000 0000 0000 0000 0001 0000 0001 0000
.word  0000 1101...

write it in hex

= 0x0000000d

lookup top (0xc)

bne // offset

calculation --

(top-pc)/4

= -5
= 0xfffb

2's complement flip and add 1

bne = 000101 = 510 /opcode

6 bits opcode
5 bits registers
5 bits registert
16 bits offset = -5

to put 000101 into first 6 bits
need to append 26 0s
=> left-shift by 26 bits

int instr = 339804155;
char c = instr >> 24; ///move the most to least significant bytes
cout<<c;
char c2 = instr >> 16;// etc

Formal languages

Assembly lang /high level language

translation to ML not ambiguous, 1 to 1 // no single translation

recognition easy // harder

structure

definitions:

alphabets : finite set of symbols

string or word finite sequence of symbols from alphabet

length of a strings

empty strings

languages set of strings

language of strings where we have an

E empty strings

{} empty languages

{e} language with 1 string, the empty string

symbols can be anything

e = {dot, dash} l = {valid English words in morse codes}

## Lec Sep 25

automatically recognize if word w is in language

charaterize according to how hard they are to recognize

finite regular language
context free/context sensitive
recursive

finite language

only finite # of strings in your language

ex L = {cat,car,cow}

read left to right

if 1st char is 'c'
  if 2nd char is 'a'
    if 3rd char is 't'
  else if 2nd char is 'o'


each of those bubbles as states

scanner or tokenizrs

e = {ASCII } L = {tokens for MIPS }

regular languages

built from finite lanugages

union L1 U l2 or concatenation L1*L2

repetition kleene *

regular expressions  E1|E2 E1 . E2

set notation L1 U L2 L1L2

description

precedence * before ./repetiiton aa* = a(a*)
. beofre | aa|b = (aa)|b

is C regular ?

start state

set of accepting state


## Lec Sep 27,2018

If I can make a DFA, can automate

alphabet,set of states, start state, accepting state, transition function

Theta(Q,e) -> Q or Q2 // if not then crash

DFA with actions

possible actions

state look up

alphabet: 0,1

1(1|0)* | 0 //start with 1 and then later repetition of 1 or 0s leading 0 means more than one 0 after the first 0

special cases?

 start -> (0 | N<-0) -> accepting states
 start -> (1 | N<-1) ->(1|N*2+1,0|N*2) accepting state

 simultaneously compute value of number

 Deterministic and ND

 NDFA

 more complex?

 New Machine e NFAs transition on epsilon

 one state to another state without reading


## Lecture Oct 2

L = {cab} U {strings with even # as }

epsilon NFA

change state without consuming an input symbol

epsilon transition move on to another without input

infinite loop?

merging those states? complicated

epsilon transition is like just one state

free-pass into another state

Tract: caba

read epsilon not readStates

e closure(S)= all states reacheable from a state in S by 0 or more E transitions

states = e closure({q0})

while not ECF do

  ch<read()


convert E NFA to DFA using a similar method

considering e transitions

states DFA are again set of states

conversion can be automated

Kleene theorem  reg exp => e-NFA -> DFA

one direction


is C a regular language?


## Lec Oct 4

Maximal Munch Algorithm

Run DFA without e moves until no non error move available

if in an accepting state, output found token

else back up to most recent accepting state

use a variable to keep tract of this input to that tpoint is next token ,

output token result from here

endif

e move back to q0

simplified maximal munch

if not in an accepting state when no valid transitions

don't back up ,simply ERROR

ex TOkens identifier must start with letter, a-z + - as internal char

must end with a letter

operator ++

simplified MM tries to read 1 token

in practice simplified MM is good enough

ex C++ before 11

s -> e
s -> (S)
s -> ss

s -> s | (S) | SS

Notation => mean "derives"

e finite non empty alphabet terminal symbols

N a finite non-empty set of non-terminals -- variables often they called

context free grammar

P finite set of production rules

A-> B, A belongs to N b belongs to V*

S a start symbol s belongs to N

ABS non terminals from N

S start symbol

a,b,c symobls from E

w x y words from e*

alpha beta thetha elements of V*

RHS of production rules

may contain both terminals and nonterminals

a A B => a theta B

a -> thetha in P RHS

a =>* b means a = s0 => theta1 => theta 2 => tehta 3 ... thetaK = beta

where k>= 0 0 or more steps

defn L(G) = {W | S =>* w} w belongs to e*

lanugage L if L = L(G) for some grammar G

ex palindromes

e = {a,b,c}

e1 = {a,b,c,d,+,-,times,/}

L1 = valid arithmetic expressions

s -> a|b|c | S OP S | (S)

op-> + | - | / | times

e2 = {a,b,c,+,-,/,times,(,)} L2 = {arith exp over {2}}

show s => * a + b : s => SOPS => a OP S => a + S => a + ****


parse tree

```
    S
  |   |  |
  s   op  s
| | |  | |
S op S * C
a + b
```

2 different parse trees

a grammar for which some word has more than 1 distinct left most derivation /parse trees

is called ambiguous


## Lec Oct 10

S-> a | b | c | S OP S
op-> + | - | * | /

ambiguity

why w belongs L(G)

the derivation(parse tree)matters

shape of parse tree describes the meaning of string wrt the grammar

grammar which some word has more than 1 distinct leftmost derivation

give precedence to * / over + -

PM -> + | -
TD -> * | /

a + b * c
E =< E PM T => T PM T => F PM T  => a PM T
=> a + T => a +  T TD F =>

... => a + b * c

WLP4

Recognizer

what class of computer programs is needed to recognize a context free language

DFA finite memory/states // must be finite

top down -- forward

start with s figure out deriation to expand into w

bottom-up

start with w backward to s

what rule could have produced W?

start with S, apply grammar rules to get w

s=>a1=>a2...=>w

use stack to store intermediate ai in reverse

supposed w = |- abywa -|

stack s'
read e
not read ...
action

when top of stack is a terminal

pop and match with the input

when TOS is a non terminal A

pop A and push a^R reverse of a

where A->a is a grammar rule

No brute force

## Tut Oct 12 CS241

Assembly instructions continue

## Lecture Oct 16

Stack and FA

augmented grammar

only access top FILO order

balanced parenthesis

context-free grammar

FA + stack

read input one char at a time

S on the stack and apply (S) rule

using the stack to count the number of opening parenthesis

pop 1 off when have a matching )

accept no more input stack empty

Using NFA to shift between push char and match char

start - b/push B  

or b/match b on top of stack pop b

no brute force algorithm

we want a deterministic procedure

can use next symbol of input look ahead to help decide

what rule to follow

more than 1 rule?

grammar called LL(1) if each cell of the predictor table contains at most 1 entry

LL(1)

left to right scan of input

leftmost derivation produced

1 symbol of lookahead

automaticall create symbol table

predict(A,a) rules that apply when A is the top of stack and a is next input char

{A->B | a belongs to First(B)} A->ab

first(B) ~ B belongs to V* V = e OR N

= {a | B =>

## LEcture Oct 18

prodict (A,a) rules that apply when A is top of stack

## Midterm Review

Q5

use recursion for bincoeff

$1 = n $2 = k

if k==0 or k == n
return 1

else return bin coeff(n -1 k -1) + bin coeff(n-1,k)

bincoeff:

Prologue:

sw $1,-4($30)
sw $2,-8($30)
sw $4,-12($30)
sw $11,-16($30)
sw $31,-20($30)
lis $31,
.word 20
sub $30,$30,$31
lis $11
.word 1  // $11 is 1 now

base case :
add $3,$11,$0
beq $2,$0,end
beq $2,$1,end

call to bincoeff (n-1,k-1)//store in $4
lis $31
.word bincoeff
sub $1,$1,$11
sub $2,$2,$11
jalr $31
add $1,$1,$11
add $2,$2,$11
add $4,$3,$0

call to bincoeff(n,k-1)
lis $31
.word bincoeff
sub $1,$1,$11
jalr $31
add $1,$1,$11
add $3,$3,$4

end:
lis $31
word 20
add $30,$30,$31
lw....

jr $31


DFA

NFA

0,1 at least 2 0s and no 111 as a sub string

-> (e,e) 0 (0,e) 0 (00,e)//2 statement for each number to track

a square shaped dfa with different states and a final state of 3 or more 0s


0,1,2,3 that contains all strings startign with 212 or ends with 03

language of balanced parenthesis

()()
()()()
(())

S-> (S)S | E
if ther exists DFA with n states that matches this language

maximal munch for /*


# Nov 6 2018

# Nov 13 2018

code(test) = code(expr1)
add $5,$3,$0
code(expr2)
slt $6,$5,$3
slt $7,$3,$5
add $3,$6,$7


code(factor) = add $3,$0,$11
factor -> NULL
deref: factor -> * expr
code(factor) = code(expr)
lw $3,0($3)


pointer arithmatic

expr1-> expr 2 + term

if expr2 : int, term int ~ as before

if expr2 is int* term int meaning expr2 + 4* term

code(expr1 = code(expr2)
push($3)
code(term)
mult $3,$4
mflo $3
pop($5)
add $3,$5,$3

sub instead of add

if expr2 is int and term is int*

assignment through pointer deref

LHS addr at which to store the values
RHS the value
stmt-> ID BECOMES expr2 SEMI
stmt-> STAR expr1 BECOMES expr2 SEMI lvalue

code stmt = code(expr2)
push($3)
code(expr1)
pop($5)
sw $5,0($3)

Address of 2 cases ID STAR expr factor -> AMP lvalue

&a if expr = ID
code(factor) = lis $3
.word lookup ID in symbol table//offset
add $3,$29,$3




## Nov 20

callee-save

factor -> ID LPAREN arglist RPAREN
4* num args and add to offset

code(factor) = push $29
push $31
code expr 1
push $3
...
code expr n
push $3
lis $5
.word FID


code(procedure) = sub $29,$30,$4
push (dcls)
push regs
code statements
code expr
pop regs
add $30,$29,$4
jr $31



optimization

heuristics

code for 1 + 2
lis $3
.word 1
sw $3, -4($30)
sub $30,$30,$4
lis $3
.word 2

constant folding


int x = 2;
return x + x;

lis $3,
.word 2
sw $3, -4($30)
sub $30,$30,$4
lw $3____($29)
push $3
lw $3,____($29)
pop($5)
add $3,$5,$3


lis $3,
.word 2
sw $3,-4($30)
sub $30,$30,$4
lis $3
.word 4

overloading

## Tutorial 1 

Legal value 

explicit Rational (int num)

constructor initalizes new object to a legal value 

Rational a = 4 

rational n = rational {4}

accessor don't change anything in your class 

overloading -- same function name for variants of the same function

different argument signatures

non member functions 

## Lecture 3

copy assignment operator

Rational& operator = (const Rational & object) {
  
}