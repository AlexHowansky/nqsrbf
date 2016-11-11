# Not Quite So Repetitive Brainfuck

Not Quite So Repetitive Brainfuck (NQSRBF) is a simple extension to Brainfuck (BF). It extends four existing BF commands to reduce the repetition of characters.

## Backwards Compatibility

BF defines the following commands, all of which operate identically in NQSRBF.

BF Operator | NQSRBF Operator | Meaning
:-: | :-: | ---
> | > | Increment the data pointer.
< | < | Decrement the data pointer.
+ | + | Increment the byte at the data pointer.
- | - | Decrement the byte at the data pointer.
. | . | Output the byte at the data pointer.
, | , | Accept one byte of input, storing its value in the byte at the data pointer.
[ | [ | If the byte at the data pointer is zero, then instead of moving the instruction pointer forward to the next command, jump it forward to the command after the matching ] command.
] | ] | If the byte at the data pointer is nonzero, then instead of moving the instruction pointer forward to the next command, jump it back to the command after the matching [ command.

## Extended Commands

NQSRBF extends the following four BF commands, providing an optional hexadecimal argument prefix.

NQSRBF Operator | Meaning
:-: | ---
n> | Increment the data pointer by n.
n< | Decrement the data pointer by n.
n+ | Increment the byte at the data pointer by n.
n- | Decrement the byte at the data pointer by n.

Thus:

    ++++++++++++++++++++++++++++++++++++++++++

Becomes:

    2a+

## Usage

The `bf2nqsrbf` script will convert a BF program into NQSRBF.

    bf2nqsrbf < source.bf > source.nqsrbf

The `nqsrbf2bf` script will convert an NQSRBF prorgram info BF, which may then be run in your favorite BF interpreter.

    nqsrbf2bf < source.nqsrbf > source.bf

## Examples


The classic BF "Hello World!" example:

    ++++++++++[>+++++++>++++++++++>+++>+<<<<-]>++.>+.+++++++..+++.>++.<<+++++++++++++++.>.+++.------.--------.>+.>.

Translated to NQSRBF via `bf2nqsrbf`:

    a+[>7+>a+>3+>+4<-]>++.>+.7+..3+.>++.<<f+.>.3+.6-.8-.>+.>.

Written specifically for NQSRBF:

    48+.1d+.7+..3+.4f-.37+.18+.3+.6-.8-.43-.
