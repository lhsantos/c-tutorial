## What is a programming language?

A computer cannot directly execute commands in *natural languages*, such as English or Spanish. In fact, inside the computer's memory and processor (CPU), all **instructions** are represented as sequences of *bits*, *i.e.*, values that can be either **0** or **1** (or, electrically, **low** voltage *vs* **high voltage**). This representation is called the **binary code** or **machine code** and is very specific for each type of processor family.

!!! tip
    The instructions "understood" by the CPU describe *very* simple tasks, such as *read value A from memory location X* and *add values B and C and store the result in A*. A computer program combines sequences of these very simple instructions to finally perform complex tasks.

Although it is *possible* write instructions to the computer directly in machine code, this task would be extremelly difficult and error prone, and unattainable for people who value their own sanity. Instead, we use **programming languages** to describe commands using a **grammar** that is similar to a natural languages (but not as flexible):

- first, we must create a _plain text file_, called the **source code**, containing a program written following the grammar and conventions of a specific programming language that we choose (there are many!);
- then, we use a special computer program (already in binary form), called a **translator**, that reads the source file as input, and converts it into machine code that can be directly executed by the CPU (**Fig. 1**).

<figure style="width:100%" markdown="span">
  ![](../assets/translation.drawio)
  <figcaption>Fig. 1 - Source code to binary code translation.</figcaption>
</figure>

Since the translator itself is a computer program and not a human:

- it cannot guess what we mean if we make _syntax errors_ (grammar mistakes) &mdash; thus, we must respect the language rules very strictly;
- it simply converts the code that we wrote, being unable to guess our _intentions_  &mdash; thus, if we make _logical errors_ in our program, there's nothing the translator can do for us;

!!! note
    Because programming languages, unlike natural languages, are very precise and unambiguous (there is only one possible interpretation for each command), they are a type of **formal language**. Other examples of formal languages include _Mathematics_ notation and _Propositional Logic_.

## Types of translators

There are two main types of translators:

- **_interpreters_** are programs that _execute source code on the fly_, _i.e_, every time you run the interpreter, the source code is processed from scratch and each line is validated and executed according to the rules of the language, one by one (**Fig. 2-a**);
- **_compilers_** are programs that _convert source code to an executable form_, _i.e._, they read the source code once and generate a new file that contains binary instructions in a format that can be loaded by the operating sytem, this file is called an **executable file** (**Fig. 2-b _STEP 1_**); in order to run the program, the operating system loads the executable file into memory, and the CPU executes the binary code directly  (**Fig. 2-b _STEP 2_**) &mdash; at this point, the compiler is no longer necessary;

<figure style="width:100%" markdown="span">
  ![](../assets/interpreter-compiler.drawio)
  <figcaption>
  Fig. 2 - (a) interpreters process and execute source code directly; (b) compilers generate an optimized binary format that can be efficiently executed by the CPU.
  </figcaption>
</figure>

But why use different strategies? Like most things in Computer Science, the choice is a _trade-off_:

- Since interpreters directly process the source code, it is simple to change the program and immediately test it, or to describe complex operations using simple commands; however, interpreting the source code line by line is usually _many orders of magnitude_ slower than executing binary code;
- Since compilers generate binary instructions that are optimized to be run by the CPU, compiled programs are very fast and efficient; however, every time the source code changes, a new compilation is necessary, which can be a slow process for large and/or complex programs;

Language implementers choose the best strategy based on the characteristics and goals of the language. Typically, languages with easier to use grammar and/or simple instructions that perform very complex operations are _interpreted_, while languages that have more detailed instructions and allow the programmer to control more aspects of the program execution are _compiled_.

**Table 1** below illustrates the main advantages and disadvantages of each strategy:

<figure>
  <table>
    <thead>
      <tr>
        <th>Criteria</th>
        <th>Interpreted languages</th>
        <th>Compiled languages</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Execution speed</td>
        <td>
          <p><span class="fail">✖</span> (Very) Slow</p>
          <p>⇒ The source code must be processed from scratch line by line, every time.</p>
        </td>
        <td>
          <p><span class="success">✔</span> Fast</p>
          <p>⇒ After compiling the code once (which can be slow), the executable file is in the optimized binary format accepted by the CPU.</p>
        </td>
      </tr>
      <tr>
        <td>Dynamic behaviour<br/>(changing aspects of the program while executing)</td>
        <td>
          <p><span class="success">✔</span> Simple</p>
          <p>⇒ Since the state of the program is created dynamically as the code is interpreted line by line, it is also simpler to dynamically change it.</p>
        </td>
        <td>
          <p><span class="fail">✖</span> Difficult</p>
          <p>⇒ Since the state of the program is represented as a memory layout during compilation, any dynamic behaviour must be designed beforehand by the programmer.</p>
        </td>
      </tr>
      <tr>
        <td>Expressivity<br/>(ability to express complex operations using simple instructions)</td>
        <td>
          <p><span class="success">✔</span> High(er)</p>
          <p>⇒ Complex operations may be implemented internallly in the interpreter; which then translates simple commands into many instructions on the fly.</p>
        </td>
        <td>
          <p><span class="fail">✖</span> Low(er)</p>
          <p>⇒ Compiled languages can only be fast if they have commands closer to the machine instructions; for this reason, expressing complex operations usually requires many programming language commands.</p>
        </td>
      </tr>
      <tr>
        <td>Portability<br/>(run the program in many different platforms)</td>
        <td>
          <p><span class="success">✔</span> Simple</p>
          <p>⇒ Since the source code is always processed directly, to support the language in a new environment (<i>e.g.</i>, another processor architecture and/or operating system), it is enough to create an interpreter that runs in the target environment.</p>
        </td>
        <td>
          <p><span class="fail">✖</span> Difficult</p>
          <p>⇒ Since it is necessary to <i>generate</i> machine code that is compatible with the new environment, the new compiler must handle all the specific machine instructions, conventions and behaviour of the new environment, which is a much more complex task.</p>
        </td>
      </tr>
      <tr>
        <td>Optimization<br/>(taking advantage of specific aspects of the environment to make the program faster)</td>
        <td>
          <p><span class="fail">✖</span> Difficult</p>
          <p>⇒ Since the source code is read directly line by line, the execution of the program is <i>necessarily</i> slower, at least on the first run; however, modern interpreters often use techniques that generate optimized machine code <i>on the fly</i> to speed up the subsequent executions of different parts of the program (this process is very complex, though).</p>
        </td>
        <td>
          <p><span class="success">✔</span> Simple(r)</p>
          <p>⇒ Since the compiler generates executable files with the machine instructions that will be directly executed by the CPU, it can greatly take advantage of the fastest execution strategies available for each processor and/or operating system.</p>
        </td>
      </tr>
    </tbody>
  </table>
  <figcaption>Table 1: Interpreted <i>vs</i> compiled languages.</figcaption>
</figure>

!!! warning
    The table above is a _generalization_. Recent technological advances in both strategies have greatly reduced their shortcomings, as briefly explained in "Other strategies" below.

!!! tip
    A given programming language is not _necessarily_ interpreted or compiled. The programming language itself is just a specification of a formal and precise way to write computer programs. There can be many _implementations_ of the same language, and each of them could theoretically be either in the form of an interpreter or of a compiler. However, most languages are _typically_ implemented using only one of these techniques.

    * Examples of (typically) **_interpreted programming languages_** include: `JavaScript`, `PHP`, `Ruby`, `Python`, `Prolog`, etc...
    * Examples of (typically) **_compiled programming languages_** include: `C`, `C++`, `Fortran`, `Rust`, `Pascal`, `Zig`, etc...


??? info "Other strategies [extra]"
    Besides "pure" compilers and interpreters &mdash; _i.e_, compilers that generate machine code or interpreters that read the source code _as-is_&mdash;, there are other "hybrid" strategies that can be used to compensate the shortcomings of each approach. Some common examples:

    - **_Intermediate representation_**: in this approach, the compiler does not generate machine code directly, but instead uses an _intermediate binary code_ that is much easier and faster to execute and/or convert to machine code _on the fly_. The intermediate code is designed to be more easily _portable_ to other environments, _i.e_, it is simpler to write a program that interprets the intermediate code, than to write a new compiler for every new system that must be supported. Examples of programming languages that use this approach are:
        * `Java`, whose compiler generates `bytecode` to be processed by the `Java Virtual Machine`;
        * `C#`, whose compiler generates code in the `Common Intermediate Language` of the `.NET` platform;
        * `Python`, whose interpreter generates a `bytecode` representation of each source file when it is first read, and later uses this optimized version to speed up execution;
    - **_Just in Time Compilation_**: also known by the acronym "JIT", this technique used in many programming language (and intermediate code) interpreters consists of generating an optimized machine code representation of small parts of the program the first time that the part is processed; later executions of that part of the program are not processed again, but instead use the previously generated optimized version, making the overall execution much faster in most scenarios;
    - **_Transpiling_**: a _transpiler_ (or _source to source translator_) is a program that processes code written in a given _source programming language_ and generates code in a different _target programming language_. Since it is usually easier to generate code in some existing programming language (instead of machine code or bytecode), this technique is useful when we want to test a new programming language idea without writing a complete new compiler, but instead using some existing compiler for a different language, and/or we want to make sure that our programs are compatible with programs written in the pre-existing language. Examples of programming languages that use transpilers are:
        * `TypeScript`, whose compiler generates `JavaScript` code;
        * the original `C++` compiler (`cfront`), generated `C` code (current `C++` compilers generate machine code directly);
        * `C++ Syntax 2`, whose `cppfront` compiler generates `C++` code;
        * `Nim`, whose compiler generates `C` code;
        * `Dart`, whose compiler can generate `JavaScript`

??? info "Domain-specific languages [extra]"
    A **_domain-specific language_**, often referred to by the acronym _DSL_ is a special type of formal language, ofen containing some features found in programming languages, that is used in very restricted contexts, as opposed to _general purpose_ programming languages that can be used in a many different of contexts. They are tipically used to describe and/or manipulate specific types of data or control specific systems. It is easier to understand with examples:
    
    - The `Structured Query Language` (`SQL`), is a language used to manipulate and retrieve data from certain types of databases, allowing users to perform complex logic operations and groupings in the data, among other features;
    - The `HyperText Markup Language` (`HTML`), is used to describe the layout and contents of web pages;
    - The `JavaScript Object Notation` (`JSON`), is used to describe data in a portable format that can be easily and quickly processed by many different systems (originally, JavaScript);
    - The `bison` syntax, is the notation used to describe programming language grammars and generate syntatic analyzers using the program `bison`;

    DSL are usually _interpreted_, and their processing happens inside some bigger context, such as within a _database management system_ or a _web browser_.

## Abstraction levels

The main reason why there are so many programming languages available is that each language is designed with a certain purpose in mind. Although most languages are _general purpose_ &mdash; which means that they can be used to create applications in several diffent contexts &mdash;, the design choices made for each language reflect the type of applications for which they should ideally be used.

That said, one of the main characteristics that define a language is its **_level of abstraction_**. Although a blurry notion, generally speaking, the level of abstration defines if the commands available in the language are **_closer to machine code_**, in other words, they have a **_low level_** of abstration, or if they are **_closer to natural (human) language_**, in other words, they have a **_high level_** of abstration.

**Table 2** below illustrates this concept by giving examples of languages in different levels of abstration and what kind of commands they typically provide:

<figure>
  <table>
    <thead>
      <tr>
        <th>Level</th>
        <th style="border-left:1px solid;border-color: inherit;">Language</th>
        <th style="border-left:1px solid;border-color: inherit;">Type of commands</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td rowspan=5 style="height:1px;">
          <div style="height:100%;display:flex;flex-direction:column;align-items:center;">
            <b>HIGH</b>
            <img style="width:5em;flex-grow:1;" src="../../assets/arrow-growing.svg">
            <b>LOW</b>
          </div>
        </td>
        <td style="border-left:1px solid;border-color: inherit;">SQL</td>
        <td style="border-left:1px solid;border-color: inherit;">
         <ul>
           <li>"Get a user by name"</li>
           <li>"Count comments of a given post"</li>
         </ul>
        </td>
      </tr>
      <tr>
        <td style="border-left:1px solid;border-color: inherit;">Java</td>
        <td style="border-left:1px solid;border-color: inherit;">
         <ul>
           <li>"Define a type called <code>Player</code>, which is a subtype of <code>GameEntity</code>"</li>
           <li>"Create a list of objects of type <code>Monster</code>"</li>
           <li>"Create a variable that holds text"</li>
           <li>"Set the name of the monster"</li>
        </td>
      <tr>
        <td style="border-left:1px solid;border-color: inherit;">C</td>
        <td style="border-left:1px solid;border-color: inherit;">
         <ul>
           <li>"Create a memory location that holds a sequence of characters"</li>
           <li>"Given a sequence of integers, get element at position <code>5</code>"</li>
           <li>"Do:
             <ul>
                <li>Make <code>index</code> be <code>0</code>;</li>
                <li>while <code>index</code> is less than the length of the sequence:</li>
                <ul>
                  <li>show the element at position <code>index</code>;
                  <li>increment <code>index</code>;"</li>
                </ul>
             </ul>
            </li>
         </ul>
        </td>
      </tr>
      <tr>
        <td style="border-left:1px solid;border-color: inherit;">Assembly Language<br/>(a textual representation of machine code)</td>
        <td style="border-left:1px solid;border-color: inherit;">
         <ul>
           <li>"load a 4-byte integer value from memory address <code>0xFFFFA</code> into register <code>R1</code>;"</li>
           <li>"add integer value at register <code>R2</code> to register <code>R7</code> and put the result in register <code>R1</code>;"</li>
           <li>"jump to address <code>0xABABAB</code>;"</li>
         </ul>
        </td>
      </tr>
      <tr>
        <td style="border-left:1px solid;border-color: inherit;">Binary code<br/>(machine code)</td>
        <td style="border-left:1px solid;border-color: inherit;">The same as Assembly Language, but with each parameter encoded in binary form (sequences of <code>0</code> and <code>1</code>)</td>
      </tr>
    </tbody>
  </table>
  <figcaption>Table 2: Examples of different levels of abstraction.</figcaption>
</figure>

!!! tip
    Although "low level" languages such as C or C++ are based on very detailed commands (_i.e._, that allow to control the hardware very precisely), we will see during this tutorial that they also provide are mechanisms that allow programmers to group sequences of instructions into single blocks with a name, called `functions` (or `procedures`), or to define their own custom `data types` that can be manipulated more conveniently. Using such mechanisms, new levels of abstraction can be created _within the source code_ to allow expressing more complex operations. This process is the most fundamental aspect of writing good programs.
