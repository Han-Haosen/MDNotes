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