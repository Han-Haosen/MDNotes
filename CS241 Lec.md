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




