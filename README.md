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

# [1.4 Processors Read and Interpret instructions Stored in Memory]()

At this point, our hello.c source program has been translated by the compilation system into an executable object file called hello that is stored on disk. To run the executable file on a Unix System, we type its name to an application program known as a **shell**:

```console
./hello
hello, world
```

The shell is a command-line intpreter that prints a prompt, waits for you to type a command line, and then performs the command. If the first word of the command line does not correspond to a built-in shell commands, then the shell assumes that it is the name of an executable file that it should load and run. So in this case, the shell loads and runs the hello program and then waits for it to terminate. The hello program prints its messages to the screen an the terminates. The shell then prints a prompt and waits for the next input command line.

# [1.4.1 Hardware Organization of a System]()

To understand what happens to our hello program when we run it, we nee to understand the hardware organization of a typical system, which is shown in Figure 1.4. This particular picture is modeled after the family of Intel Pentium systems, but all systems have a similar look and feel. Don't worry about the complexity of this figure just now. We will get to its various details in stages throughout the course of the book.

# [Buses]()
# [I/O Devices]()
# [Main Memory]()

The main memory is a Temporary storage device ta holds both a program and the data it manipulates while the processor is executing the program. Physically, main memory consists of a collection of **dynamic random access memory** (DRAM) chips. Logically, memory is organized as a linear array of bytes, each with its own unique address (array index) starting at zero. In general, each of the machine instructions that constitute a program can consist of a variable number of bytes. The sizes of data items that correspond to C program variables vary according to type. For example, on an IA32 machine running Linux, data of type short requires two bytes, types int, float, and long four bytes, and type double eight bytes. Chapter 6 has more to say about how memory technologies such as DRAM chips work, and how they are combined to form main memory.

# [Processor]()

# [1.4.2 Running the hello Program]()

Using a technique knows as **direct memory access** (DMA), the data travels directly from disk to main memory, without passing through the processor. 

Once the code and data in the hello object file are loaded into memory, the processor begins executing the machine-language instructions in the hello program's main routine. These instructions copy the bytes in the "Hello, world\n" string from memory to the register file, and from there to the display device, where they are displayed on the screen

![Screen Shot 2020-06-28 at 9 10 40](https://user-images.githubusercontent.com/24994818/85949952-563a2f80-b91f-11ea-9dd4-2b88d4ae4a78.png)
![Screen Shot 2020-06-28 at 9 10 53](https://user-images.githubusercontent.com/24994818/85949953-5803f300-b91f-11ea-8184-af15d9b13326.png)
![Screen Shot 2020-06-28 at 9 11 02](https://user-images.githubusercontent.com/24994818/85949954-59cdb680-b91f-11ea-8a33-054c865cfef8.png)

This is a second branch to test !

# [1.5 Caches Matters]()

Because of the physical laws, larger storage devices are slower than smaller storage devices. And faster devices are more expensive to build than their slower counterparts.

It is easier and cheaper to make processors run faster than it is to make main memory run faster.

To deal with the processor-memory gap, system designers include smaller faster storage devices called **cache memories** that serve as temporary staging areas for information that the processor is likely to need in the near future .

![Screen Shot 2020-06-24 at 17 34 54](https://user-images.githubusercontent.com/24994818/85634486-19c9b380-b641-11ea-9937-8728815f80bf.png)

An **L1 cache** on the processor chip holds tens of thousands of bytes and can be accessed nearly as fast as the register file.

An **L2 cache** with hundred of thousands to million of bytes is connected to the proccessor by a special bus, It might take 5 times longer for the process to acces the L2 cache than the L1 cache, but this is still 5 to 10 times faster than acessing the main memory. 

The L1 and L2 caches are implemented with a hardware technology known as **static random access memory** **(SRAM)**, Newer and more powerful systems even have three levels of cach: L1, L2, and L2. The idea behind caching is that a sustem can get the effect of both a very large memory and a very fast one by exploiting **locality**. the tendency for programs to access data and code in localized regions. By setting up caches to hold data that is likely to accessed often, we can perform most memory operations using the fast caches.

One of he most important lessons in this book is that applications programmers who are aware of cache memories can exploit them to improve the performance of their programs by an order of magnitude. You will learn more about these importan devices and how to exploit them in Chapter 6.

# [1.6 Storage Devices Form a Hiararchy]()

Storage devices in every computer system are organized as a **memory hierarchy** similar to the figure. 1.9.

![Screen Shot 2020-06-24 at 17 52 54](https://user-images.githubusercontent.com/24994818/85635470-8f368380-b643-11ea-9616-a68e62304e88.png)

Just as programmers can exploit knowledge of the different caches to improve performance, programmers can exploit their understanding of the entire memory hierarchy. Chapter 6 will have much more to say about this.

# [1.7 The Operating System Manages the Hardware]()

Back to our hello example. When the shell loaded and ran the hello program and when the hello program printed its messages, neither program accessed the keyboard, display, disk, or main memory directly. Rather, they relied on the services provided by the **operating system**. We can think of the operating system as a layer of software interposed between the application program ad the hardware, as shown in Figure 1.10. All attempts by an application program to manipulate the hardware must go through the operating system.

![Screen Shot 2020-06-29 at 19 16 30](https://user-images.githubusercontent.com/24994818/86068483-123d4c80-ba3d-11ea-9b8a-b7bf40116422.png)


The operating system has two primary purposes: 

1. To protect the hardware from misuse by runaway applications, and
2. to provide applications with simple and uniform mechanisms for manipulating complicated and often wildly different low-level hardware devices. The operating system achieves both goals via the fundamental abstraction shown in Figure 1.11: **Processes, virtual memory, and files**. As this figure suggest, files are abstractions for I/O devices, virtual memory is an abstraction for both the main memory and disk I/O devices, and processes are abstractions for the processor, main memory, and I/O devices. We will discuss each in turn.

![Screen Shot 2020-06-29 at 19 20 59](https://user-images.githubusercontent.com/24994818/86068701-ad362680-ba3d-11ea-868e-98618c893494.png) 

# [1.7.1 Processes]()

When a program such as **hello** runs on a modern system, the operating system **provides the illusion that the program is the only one running on the system**. The program appears to have exclusive use of both **the processor, main memory and I/O devices**. The processor appears to execute the instructions in the program, one after the other, without interruption. And the code and the data of the program appear to be the only objects in the system's memory. These illusions are provided by the notion of a process, one of the most important and successful ideas in the computer science.

A **process** is the operating system's abstraction for a running program. Multiple processes **can run concurrently** on the same system, and each process appears to have exclusive use of the hardware. By **concurretly**, we mean that the instructions of one process are interleaved with the instructions of another process.In most systems, there are more processes to run than there are CPUs to run them. Traditional systems could only execute one program at time, while newer **multicore** processors can execute several programs simultaneously by having the processor switch among them. The operating system performs this interleaving with a mechanism known as **context switching**. To simplify the rest of this discussion, we consider only a **uniprocessor system** containing a single CPU. We still return to the discussion of **multiprocessor** systems in Section 1.9.1.

The operating system keeps track of all the state information that the process needs in order to run. This state, which is known as the **context**, includes information such as the current values of the PC, the register file, and the contents of main memory. At any point in time, a uniprocessor system can only execute the code for a single process. When the operating system decides to transfer control from the current process to some new process, it performs a **context  switch** by saving the context of the current process, restoring the context of the new process, an then passing control to the new process. The new process picks up exactly where it left off. Figure 1.12 shows the basic idea for our example **hello** scenario.

![Screen Shot 2020-06-30 at 13 26 58](https://user-images.githubusercontent.com/24994818/86163144-71e73680-bad5-11ea-8463-02367a0ef0e2.png)

There are two concurrent processes in our example scenario: the shell process and the **hello** process. Initially, the shell process is running alone, waiting for input on the command line. When we ask it to run hello program, the shell carries out request by invoking a special function known as a **system call** that passes control to the operating system. The operating system saves the shell's context, creates a new hello process and its context, and then passes control to the new **hello** process. After **hello** terminates, the operating system restores the context of the shell process and passes control back to it, where it waits for the next command line input.

Implementing the process abstraction requires close operation between both the low-level hardware and the operating system software. We will explore how this works, and how applications can create and control their own processes, in Chapter 8.

# [1.7.2 Threads]()

Although we normally think of a process as having a single control flow, in modern systems a process can actually consist of multiple execution units, called **threads**, each running in the context of the process and sharing the same code and global data. Threads are an increasingly important programming model because of the requirements for concurrency in network servers, because it is easier to share data between multiple threads than between multiple processes, and because **threads are typically more efficient than processes**. Multi-threading is also one way to make programs run faster when multiple processors are available, as we will discuss in Section 1.9.1. You will learn the basic concepts of concurrency, including how to write threaded programs, in Chapter 12.

# [1.7.3 Virtual Memory]()

**Virtual memory** is an **abstraction** that provides each process with the illusion that it has exclusive use of the main memory. Each process has the same uniform view of memory, which is known as its **virtual address space**. The virtual address space for Linux processes is shown in Figure 1.13. (Other Unix systems use a similar layout.) In Linux, the topmost region of the address space is reserved for code and data in the operating system that is common to all processes. The lower region of the address space holds the code and data defined by the user’s process. Note that addresses in the figure increase from the bottom to the top.

![Screen Shot 2020-07-06 at 0 50 48](https://user-images.githubusercontent.com/24994818/86559925-c3068880-bf22-11ea-83a6-afba12b6594c.png)

**The virtual address space** seen by each process consists of a number of well- defined areas, each with a specific purpose. You will learn more about these areas later in the book, but it will be helpful to look briefly at each, starting with the lowest addresses and working our way up:

- **Heap**. The code and data areas are followed immediately by the run-time heap. Unlike the code and data areas, which are fixed in size once the process begins running, the heap expands and contracts dynamically at run time as a result of calls to C standard library routines such as malloc and free. We will study heaps in detail when we learn about managing virtual memory in Chapter 9.

- **Shared libraries**. Near the middle of the address space is an area that holds the code and data for shared libraries such as the C standard library and the math library. The notion of a shared library is a powerful but somewhat difficult concept. You will learn how they work when we study dynamic linking in Chapter 7.

- **Stack**. At the top of the user’s virtual address space is the user stack that the compiler uses to implement function calls. Like the heap, the user stack expands and contracts dynamically during the execution of the program. In particular, each time we call a function, the stack grows. Each time we return from a function, it contracts. You will learn how the compiler uses the stack in Chapter 3.

- **Kernel virtual memory**. The kernel is the part of the operating system that is always resident in memory. The top region of the address space is reserved for the kernel. Application programs are not allowed to read or write the contents of this area or to directly call functions defined in the kernel code.

For virtual memory to work, a sophisticated interaction is required between the hardware and the operating system software, including a hardware translation of every address generated by the processor. The basic idea is to store the contents For virtual memory to work, a sophisticated interaction is required between the hardware and the operating system software, including a hardware translation of every address generated by the processor. The basic idea is to store the contents

# [1.7.4 Files]()

A **file** is a sequence of bytes, nothing more and nothing less. Every I/O device, including disks, keyboards, displays, and even networks, is modeled as a file. All input and output in the system is performed by reading and writing files, using a small set of system calls known as **Unix I/O**.
This simple and elegant notion of a file is nonetheless very powerful because it provides applications with a uniform view of all of the varied I/O devices that might be contained in the system. For example, application programmers who manipulate the contents of a disk file are blissfully unaware of the specific disk technology. Further, the same program will run on different systems that use different disk technologies. You will learn about Unix I/O in Chapter 10.

