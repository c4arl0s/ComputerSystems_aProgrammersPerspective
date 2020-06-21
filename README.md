# ComputerSystems_aProgrammersPerspective
i
Computer Systems A Programmer’s Perspective (Lecture)

1. [A Tour of computer Systems]()
2. [Part I: Program Structure and Execution]()
3. [Part II: Running Programs on a System]()
4. [Part III: Interaction and Communications Between Programs]()
5. [A: Error Handling]()


# ComputerSystems_aProgrammersPerspective

# 1. [1 A Tour of computer Systems]()
# 2. [Part I: Program Structure and Execution]()
* [2 Representing and Manipulating Information]()
* [3 Machine-Level Representation of Programs]()
     
# 3. [Part II: Running Programs on a System]()
* [2 Representing and Manipulating Information]()
* [3 Machine-Level Representation of Programs]()
* [4 Processor Architecture]()
* [5 Optimizing Program Performance]()
* [6 The Memory Hierarchy]()
# 4. [Part III: Interaction and Communications Between Programs]()
* [7 Linking]()
* [8 Exceptional Control Flow]()
* [9 Virtual Memory]()
* [10 System-Level I/O]()
* [11 Network Programming]()
* [12 Concurrent Programming]()
# 5. [A: Error Handling]()
* [A.1 Error Handling in Unix Systems]()
* [A.2 Error-Handling Wrappers]()

# 1. [1 A Tour of computer Systems]()
# [1.2 Programs are translatedxd by other Programs into Different Forms]()

![Screen Shot 2020-06-21 at 12 37 15](https://user-images.githubusercontent.com/24994818/85231358-f5a97080-b3bb-11ea-98a8-00e139f7212c.png)

* Preprocessing Phase.
* Compilation Phase.
* Assembly Phase.
* Linking Phase.

**Preprocessing Phase**
The preprocessor modifies the original C program according to directives that begin withe # character. 
**Compilation Phase**
The compiler translates the text file into the text file .s, which contains an assembly-language program. Each stateent in an assembly-language program exactly describes one low-level machine-language instruction in standard text form.
**Assebly Phase**
Next, the assembler translates into machine language instructions, packages them in a form known as a relocatable object program, and stores the result in the object file *.o. This file i a binary file whose bytes encode machine language instructions rather than characters. If we were to view .o file with a text edito, it would appear to be gibberish.
**Linking Phase**
Notice that our program calls the printf function, which is part of the standard C library privided by ever C compiler The printf function resides in a separate precompiled object file called printf.o, which must somehow be merged with our hellow.o program. The linked (ld) handles this mergin. The result is the hello file,w hich is an executable object file (or simply executable) that is ready to be loaded into memory and executed by the system.

