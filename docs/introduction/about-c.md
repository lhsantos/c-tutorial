The [C Programming Language](https://en.wikipedia.org/wiki/C_(programming_language)){ target="_blank" rel="noopener noreferrer" } was created in 1972 by Computer Science legend Dennis Ritchie at Bell Labs, and went on to become one of the most used languages of all time, while also being extremelly influential over languages that came after it.

At the time when C was created, there were very few [high level languages](about-programming.md#abstraction-levels) available. Most programs were written using _assembly language_, which is little more than a textual representation of binary code, and requires the programmer to completely control the _memory layout_ &mdash; _i.e._, how each byte of memory is used &mdash; of the program and to understand how the _machine instructions_ work in great detail. Even advanced programmers who had such skills would still suffer from the effort-intensive and error-prone process of writing down long lists of commands which are so close to the hardware. To address this issue and facilitate the development of the then emerging Unix operating system (which later would be the basis to the creation of Linux, FreeBSD and MacOS, among other modern operating systems), Dennis Ritchie created C and designed it to be a "high level assembly".

Basically, C offers features of _high level_ languages &mdash; such as built-in **_data types_** that can be composed and manipulated conveniently instead of manually organizing the memory; **_variables_** and **_expressions_** to easily express calculations; and **_functions_** (blocks of commands with a name), which enables improving the code organization by using  _modularization_ and _layers of abstractions_ &mdash;, while still offering _low level_ operations, such as referring to a memory locations directly.

## Why use C?

Its characteristics made C ideal as a language for <a href="https://en.wikipedia.org/wiki/Systems_programming" target="_blank" rel="noopener noreferrer">systems programming</a>, which is the development of software that handles the hardware directly, such as _operating systems_, _device drivers_ and _embedded software_. Writing the Unix source code in C made it much easier to _port_ it to many environments &mdash; _i.e._, as long as there is a C [translator](about-programming.md) for the target environment, the code could still work with little modification even if the machine instructions were different.

Additionally, because C syntax is so close to machine instructions, it is relatively easy to create a C translator (when compared to other languages), and it can be highly optimized to best use the resources available on the target hardware. For this reason, the other major use case of the C Language is for the development of **_software libraries_**, _i.e._ bundles of small utility code that can be integrated into new applications to speed up performance critical operations, such as _video/image processing_, _cryptography_, _networking_, calculation intensive _simulations_, among others. This is also the reason why _video games_ are usually written using C or its sister, `C++`, which has similar features.

!!! tip
    C is such a widely supported and efficient language that it is most common that higher level languages &mdash; such as `Java`, `JavaScript`, `Pyhton`, `C#`, among many others &mdash; implement their **_standard libraries_**, _i.e_, the built-in software libraries available by default to the programmer, using C, and make it available by using "wrappers" that execute the optimized C code behind the scenes. This is also a common strategy for non-standard libraries created by the community of programmers that use these high level languages.


## Developing in C

C is a [compiled language](about-programming.md#types-of-translators). This means that you need a compiler installed on your machine before you can write any programs. Although there are probably hundreds of C compilers available, there are 3 that are most commonly used:

- <a href="https://gcc.gnu.org/" target="_blank" rel="noopener noreferrer">"Gnu Compiler Collection" (GCC)</a>
- <a href="https://clang.llvm.org/" target="_blank" rel="noopener noreferrer">Clang</a>,
- <a href="https://docs.microsoft.com/en-us/cpp/" target="_blank" rel="noopener noreferrer">"Microsoft Visual C++" (MSVC)</a>.

MSVC is available for Windows only, but GCC and Clang are available for Linux, MacOS, and Windows. The [next section](setup.md) explains how to prepare your environment to use each of these compilers. In this tutorial, we will use only a <a href="https://en.wikipedia.org/wiki/C23_(C_standard_revision)" target="_blank" rel="noopener noreferrer">standard version of C</a>, so there is no practical difference between these compilers with regards to the code, but there is a different way of _invoking_ the compiler, _i.e_, actually executing it to read source code and generate executable files. Select your compiler's tab on each code example, and the proper command will be shown.

For the simplest case, when we have a _single source file_ that we want to compile, the compilation process is quite simple (**Fig. 1**). However, as applications become more complex, it becomes necessary to split our code into _multiple source files_, and to use third-party _libraries_ that provide some functionalities that we cannot or do not want to implement ourselves. In that case, the compilation process becomes increasingly more complex, and takes many steps (**Fig. 2**). Right now, we won't worry about this case. Much later in the tutorial, we will explain how you can organize your code to use many files, and how to compile it correctly in this scenario.

For now, move on to the [next section](setup.md), set up your environment, and have a nice journey!

<figure style="width:45%" markdown="span">
  ![](../assets/compile-c-simple.drawio)
  <figcaption>Fig. 1 - Compiling a C program (simple case).</figcaption>
</figure>

<figure style="width:60%" markdown="span">
  ![](../assets/compile-c-complex.drawio)
  <figcaption>Fig. 2 - Compiling a C program (complex case).</figcaption>
</figure>
