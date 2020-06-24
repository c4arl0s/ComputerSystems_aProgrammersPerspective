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

# [1.3 It pays to understand How Compilation System Works]()

Important reasons why programmers needs to understand how compilation works:

- **Optimzation program performance**
- **Understanding link-time errors**
- **Avoiding security holes**


- **Optimzation program performance**

Modern compilers are sophisticated tools that usually produce good code. As programmers, we do not need to know the inner workings of the compiler in order to write efficient code. However, in order to make god coding decisions in our C programs, we do need a basi understanding of machine-level code and how the compiler translates different C statements into machine code. For example, is a switch statement always more efficient than a sequence of if-else statements? how much overhead is incurred by a function call ?Is a while loop more efficient that a for loop? Are pointer references more efficient than array indexes ? Why does our loop run so much faster if we sum into a local variable instead of an argument that is passed by reference ? How can a function un faster when we simply rearrange the parentheses in an arithmetic expresion ?

We describe how compilers translate different C constructs into these languages. In Chapter 5, you will learn hohw to tune the performance of your C programs by making simple transfromations to the C code that help the compiler do its job better. In Chapter 6, you will leran about the hierarchical nature of the memory system, how C compilers store data arrays in memory, and how your C programs can exploit this knowledge to run more efficiently.

- **Understanding link-time errors**
In our experience, some of the most perplexing programming errors are related to the operation of the linker, especially when you are trying to build large software systems. For example, what does it mean when the linker reports that it cannot resolve a reference? What is th difference between a static variable and a global variable ? What happens if you define two global variables in diferrent C files with the same name ? what is the difference between a static library and a dinamyc library ? Why does it matter what order we list libraries on the command line ? And scariest of all, why do some linker-related errors not appear until run time ?. You will learn tha answers to these kinds of questions in chapter 7.

- **Avoiding security holes**
For many years, **buffer overflow vulnerabilities** have accounted for the majority of security holes in network and Internet Servers. These vulnerabilities exist because too few programmers understand the need to carefully restrict the quantity and form of data they accept from untrusted sources. A first step in learning secure programming is to understand the consequences of the way data nd control information are stored on the program stack. We cover the stack discipline and buffer overflow vulnerabilities in Chapter 3 as part of our study of assembly language. We will also learn about methods that can be used by the programmer, compiler, and operating system to reduce the thread of attack.

# [1.5 Caches Matters]()

Because of the physical laws, larger storage devices are slower than smaller storage devices. And faster devices are more expensive to build than their slower counterparts.

It is easier and cheaper to make processors run faster than it is to make main memory run faster.

To deal with the processor-memory gap, system designers include smaller faster storage devices called **cache memories** that serve as temporary staging areas for information that the processor is likely to need in the near future .

![Screen Shot 2020-06-24 at 17 34 54](https://user-images.githubusercontent.com/24994818/85634486-19c9b380-b641-11ea-9937-8728815f80bf.png)

An **L1 cache** on the processor chip holds tens of thousands of bytes and can be accessed nearly as fast as the register file.

An **L2 cache** with hundred of thousands to million of bytes is connected to the proccessor by a special bus, It might take 5 times longer for the process to acces the L2 cache than the L1 cache, but this is still 5 to 10 times faster than acessing the main memory. 

The L1 and L2 caches are implemented with a hardware technology known as **static random access memory** **(SRAM)**, Newer and more powerful systems even have three levels of cach: L1, L2, and L2. The idea behind caching is that a sustem can get the effect of both a very large memory and a very fast one by exploiting **locality**. the tendency for programs to access data and code in localized regions. By setting up caches to hold data that is likely to accessed often, we can perform most memory operations using the fast caches.

One of he most important lessons in this book is that applications programmers who are aware of cache memories can exploit them to improve the performance of their programs by an order of magnitude. You will learn more about these importan devices and how to exploit them in Chapter 6.


