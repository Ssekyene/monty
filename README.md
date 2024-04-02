# The Monty language interpreter
![snapshot](/snapshot.PNG)

## The Monty language
Monty 0.98 is a scripting language that is first compiled into Monty byte codes (Just like Python). It relies on a unique stack, with specific instructions to manipulate it.The goal of this project is to create an interpreter for Monty ByteCodes files.

### Monty byte code files
Files containing Monty byte codes usually have the .m extension. Most of the industry uses this standard but it is not required by the specification of the language. There is not more than one instruction per line. There can be any number of spaces before or after the opcode and its argument:

```
$ cat -e bytecodes/000.m
push 0$
push 1$
push 2$
  push 3$
                   pall    $
push 4$
    push 5    $
      push    6        $
pall$
```

Monty byte code files can contain blank lines (empty or made of spaces only, and any additional text after the opcode or its required argument is not taken into account:

```
$ cat -e bytecodes/001.m
push 0 Push 0 onto the stack$
push 1 Push 1 onto the stack$
$
push 2$
  push 3$
                   pall    $
$
$
                           $
push 4$
$
    push 5    $
      push    6        $
$
pall This is the end of our program. Monty is awesome!$
```

## Compilation
**Note:**

- The source code files for the interpreter are supported basically by Ubuntu 20.04 LTS.

Compile with:

```c
$ gcc -Wall -Werror -Wextra -pedantic -std=c89 *.c -o monty
```
You may also decide to drop the flags and compile with:

```c
$ gcc *.c -o monty
```
You can run the interpreter together with the bytecode like:

```
$ ./monty bytecodes/00.m
```
or simply add the compiled file the `PATH` and run like:

```
monty bytecodes/00.m
```
## Brainfuck
- The project also includes some simple [Brainfuck](https://en.wikipedia.org/wiki/Brainfuck) files in [bf](/bf) directory.
- You can install the bf interpreter to test your code: `sudo apt-get install bf`.
