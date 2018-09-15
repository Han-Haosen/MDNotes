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
