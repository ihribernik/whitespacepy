Whitespace: specification
=========================

Commands
========
IMP
===

There are different types of commands in Whitespace, and they all have different Instruction Modification Parameters (IMP). You have to do IMP first, then command, then parameters if necessary. The parameters end with a linefeed.

IMP	Command
[Tab][LF]	I/O
[Space]	Stack Manipulation
[Tab][Space]	Arithmetic
[LF]	Flow control
[Tab][Tab]	Heap access
Numbers
To input numbers, first there's a sign. A space is positive, a tab is negative. Then you need to input the numbers in binary. A space is 0, a tab is 1.

I/O
So let's take some inputs and outputs.

Commands	Parameters	Meaning
[Tab][Space]	-	Read a character and place it in the location given by the top of the stack
[Tab][Tab]	-	Read a number and place it in the location given by the top of the stack
[Space][Space]	-	Output the character at the top of the stack
[Space][Tab]	-	Output the number at the top of the stack
Basically, all you need to remember is first, [Tab] for input, [Space] for output, and second, [Space] for character, [Tab] for number.

Stack manipulation
Of course, you need to actually do stuff with the stack.

Commands	Parameters	Meaning
[Space]	Number	Push number on the top of the stack
[LF][Space]	-	Duplicate the top item on the stack
[LF][Tab]	-	Swap the top two items on the stack
[LF][LF]	-	Discard the top item on the stack
[Tab][Space]	Number	Copy the nth item on the stack (given by the argument) onto the top of the stack (v0.3)
[Tab][LF]	Number	Slide n items off the stack, keeping the top item (v0.3)
Arithmetic
Of course, you actually need to do something with the top of the stack.
Arithmetic commands operate on the top two items on the stack, and replace them with the result of the operation. The first element pushed is considered to be left of the operator.

Command	Parameters	Meaning
[Space][Space]	-	Addition
[Space][Tab]	-	Subtraction
[Space][LF]	-	Multiplication
[Tab][Space]	-	Integer Division
[Tab][Tab]	-	Modulo
Flow Control
Of course, you need to have jumps, subroutines, those stuff.

Commands	Parameters	Meaning
[Space][Space]	Label	Mark a location in the program
[Space][Tab]	Label	Call a subroutine
[Space][LF]	Label	Jump unconditionally to a label
[Tab][Space]	Label	Jump to a label if the top of the stack is zero
[Tab][Tab]	Label	Jump to a label if the top of the stack is negative
[Tab][LF]	-	End a subroutine and transfer control back to the caller
[LF][LF]	-	Ends the program
Heap Access
Heap access commands look at the stack to find the address of the items to be stored or retrieved. To store an item, push the address then the value and run the store command. To retrieve an item, push the address and run the retrieve command, which will place the value stored in the location at the top of the stack.

Command	Parameters	Meaning
[Space]	-	Store
[Tab]	-	Retrieve
