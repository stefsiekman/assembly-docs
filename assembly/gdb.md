# GNU debuggger cheat sheet

## Compilation

When compiling with GCC use the ```-g``` flag to ensure more debugging information is added to the executable. This means using the GCC command as follows for example:

```
gcc -g -o printf my_printf.s
```

## Opening

Open the de bugger using the following command:

```
gdb <executable>
```

### Opening an executable with an argument

The easiest way to execute your executable with an argument is the following:

```
gdb --args <executable> <arg1> <arg2> ...
```

## Commands

There are several handy commands that can help you to get started with the GNU debugger.

### ```run```

This command is used to start your program's execution.

### ```break <breakpoint>```

This command is used to set a point at which the execution of your program should pause. The names of subroutines can always be used for this. It is a good idea to always set at least one breakpoint, to skip over the setup phase of your program. If you don't have any specific breakpoint in mind to test, a good default would be: ```break main```. If you compiled using the ```-g``` flag, line numbers within files can also be used a breakpoints.

### ```si``` (step instruction)

This command is used to execute the next instruction. This 'next' instruction is always displayed above where you enter you command as the address in memory. If you compiled using ```-g``` you can even see what instruction this is and it's location in the file (with comments behind it).

### ```ni``` (next instruction)

This command can be used to execute the next instruction and any instructions that are called by this instruction. This command should be used if you're about to execute a ```call``` instruction, especially with the standard C libraries. If you were to use the regular ```si``` you would have to step through all of the instructions in the subroutine that's called.

### ```i r``` (info registers)

This command can be used to see the contents of all the registers.

### ```x/x <memory location>```

This command is used to display the contents (double word) of specific memory location. The content is displayed in hexadecimal. The memory location can be provided in different ways. Keep in mind it is always possible to use ```+``` or ```-``` to add to or subtract from the memory location. This is especially handy if you want to inspect arrays.

#### Direct

Give the address as number in hexidecimal, decimal, etc.

#### Register

Give the address by referencing a register, this can be done in the following manner: ```$rax```. This can also be used to obtain the address of the stack pointer (```$rsp```).

#### Label

Give the address by referencing a label (such as a string or array), this can be done in the following manner: ```&my_string```.

### ```x/d <memory location>```

The same as ```x/x <memory location>```, but now gives the content of the memory as decimal number.

### ```x/c <memory location>```

The same as ```x/x <memory location>```, but now gives the content of the memory as character.

### ```x/b <memory location>```

The same as ```x/x <memory location>```, but now only gives a sigle byte of memory.
