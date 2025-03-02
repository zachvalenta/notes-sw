# ⛩️

## 参考

🔗 https://en.wikipedia.org/wiki/Execution_(computing)
🔍 https://softwareengineering.stackexchange.com/questions/tagged/compiler
🗄️ `algos.md` data structures / tree
📚
* Ball interpreter https://vgel.me/posts/c500/
* Keleshev compiling assembly https://keleshev.com/compiling-to-assembly-from-scratch/
* Nystrom crafting https://craftinginterpreters.com
* Sandler https://nostarch.com/writing-c-compiler

## 进步

* _24_: own file

ASSEMBLY
Some compilers translate high-level code into assembly language as an intermediate step. This assembly code is then passed to an assembler, which converts it into machine code (binary instructions that the CPU can execute directly).
Examples: GCC/Clang for C/C++: These compilers can generate assembly code using flags like -S. For instance, gcc -S example.c produces an example.s assembly file.
Rust Compiler (rustc): Can emit assembly code for inspection or further processing.

BINARY
This is the set of binary instructions that a computer's CPU executes directly. Compilers like GCC, Clang, and MSVC can compile source code all the way to machine code, producing executable files (like .exe on Windows or binary binaries on Unix/Linux systems).
Examples: C/C++ Compilers: gcc example.c -o example generates an executable binary. Go Compiler (go build): Compiles Go programs directly into machine code executables.

BYTECODE
Bytecode is an intermediate, platform-independent code that is executed by a virtual machine (VM) or an interpreter. It is more abstract than machine code but less so than high-level source code. Bytecode allows for portability across different hardware and operating systems, as the same bytecode can run on any platform that has the appropriate VM.
Examples: Java Compiler (javac): Compiles Java source files into .class files containing Java bytecode, which the Java Virtual Machine (JVM) executes. C# Compiler (csc): Produces Microsoft Intermediate Language (MSIL) bytecode, which runs on the .NET Common Language Runtime (CLR). Python (with certain implementations): CPython compiles Python code to bytecode (.pyc files) executed by the Python virtual machine.

INTERMEDIATE REPRESENTATION
Some compilers use their own intermediate representations during the compilation process, which are not necessarily the final output but are crucial for optimizations and transformations. IRs like LLVM's Intermediate Representation are used within compiler toolchains to enable optimizations and support multiple target architectures.
Examples: LLVM Compiler Infrastructure: Uses LLVM IR as a common language for various front-end languages, allowing the backend to generate machine code for different architectures.

SOURCE TO SOURCE
* TypeScript Compiler (tsc): Translates TypeScript code into JavaScript.
* Babel: Transpiles modern JavaScript (ES6+) into backward-compatible versions.

# 🦠 COMPILE

```python
x = y + 5
```
```txt
Reads source code
Handles parsing, syntax checking
Does semantic analysis
Creates AST (Abstract Syntax Tree)
```

---

> Because it'll take two seconds to run in Rust or in Python or a few hundred milliseconds to run in Python and 10 seconds to compile in Rust. So it is not universally the case that the development cycle is faster in Rust. https://talkpython.fm/episodes/show/487/building-rust-extensions-for-python

https://www.pixelstech.net/article/1728356198-Why-is-Golang-s-Compilation-Speed-So-Fast

* https://lwn.net/Articles/997784/
* 📙 Conery 216
* _assemble_: convert from HLA to assembly
* _disassemble_: show assembly for HLA https://realpython.com/python311-new-features/#faster-code-execution https://florian-dahlitz.de/blog/disassemble-your-python-code 
```python
import dis
dis.dis(fn)
```
* _optimization_: most of diff btw compilers is here [Conery 216] https://signalsandthreads.com/compiler-optimization/ https://www.hytradboi.com/2025/2db17db8-855a-4baf-84eb-0e7c29d7c9a1-debugging-compiler-optimized-code-how-it-works-and-doesnt

## lex

```txt
Lexer (Tokenizer):
Breaks source into tokens
x = y + 5 becomes [IDENT(x), EQUALS, IDENT(y), PLUS, NUMBER(5)]
```

* _lex_: tokenize [Conery 218] https://www.aaronraff.dev/blog/how-to-write-a-lexer-in-go
* why it's split from parse https://news.ycombinator.com/item?id=35798829
* _lexical analysis_: https://docs.python.org/3/reference/lexical_analysis.html

* _token_: atomic unit of significance
```python
tokens = {
    "variable": "foo",
    "operator": "=",
    "number": 10
}
```

## parse

```txt
Takes tokens
Builds tree structure
Checks syntax
Creates AST
```
```txt
- Grammar Definition
- Parse Trees
- Recursive Descent vs. LALR Parsing
```

---

* _parser_: generates AST from src https://drewdevault.com/2018/12/28/Anatomy-of-a-shell.html https://astral.sh/blog/ruff-v0.4.0 https://drewdevault.com/2021/04/22/Our-self-hosted-parser-design.html
* parser generator https://lezer.codemirror.net/
* https://ohmjs.org/ https://dubroy.com/blog/ https://registerspill.thorstenball.com/p/joy-and-curiosity-16
* date/time parser https://github.com/olebedev/when
* JSON parser https://news.ycombinator.com/item?id=38150833 https://blog.sylver.dev/building-a-json-validator-with-sylver-part13-writing-a-json-parser-in-49-lines-of-code 

## semantic analysis

type checking

```txt
- Type Checking
- Scope Resolution
- Symbol Tables
```

## AST

```txt
Tree representation of code
Loses irrelevant syntax (whitespace, comments)
```
```sh
    =
   / \
  x   +
     / \
    y   5
```

---

https://ssloy.github.io/tinycompiler/ast/

> D2 has an API built on top of its AST for programmatically creating diagrams in Go. This package is d2/d2oracle.  https://d2lang.com/tour/api

* _AST_: src as tree https://sadh.life/post/ast/ https://d2lang.com/tour/api
* translate AST from c to Golang src https://simonwillison.net/2022/Jan/30/a-cgo-free-port-of-sqlite/
```python
def area_of_circle(radius):
    pi = 3.14
    return pi * radius * radius

area_of_circle(5)

                 (program)
                /         \
  (area_of_circle r)      (main)
  /           |             |
define    calculate        run area_of_circle
  pi        area             with r = 5
           /   |
     multiply  (pi, r, r)
```

* _grammar_: rules for language's AST https://hakibenita.com/automating-the-boring-stuff-in-django-using-the-check-framework#parsing-the-code

## IR

```txt
- Analysis & Optimization
    - Data flow analysis
    - Control flow analysis
    - Constant propagation
    - Dead code elimination
- IR Transformations
```
```txt
- Abstract Syntax Tree (AST)
- Control Flow Graphs
- Static Single Assignment (SSA) https://bernsteinbear.com/blog/ssa/
```
```txt
- Peephole Optimization
- Loop Transformations
- Dead Code Elimination
```

## LLVM

📙 https://aosabook.org/en/v1/llvm.html

alternatives https://news.ycombinator.com/item?id=42782872

```sh
%1 = load i32, ptr %y
%2 = add i32 %1, 5
store i32 %2, ptr %x
```
```txt
A compiler's internal format
Language-agnostic
Optimizations happen here

Key innovation of LLVM: standardized IR that any frontend/backend can use
New language = just write frontend
New CPU = just write backend
Optimizations work for all languages and CPUs since they happen on IR
```

* _IR generator_: convert's AST to IR
* _optimizer_: Applies optimization passes
* _code generator_: Converts IR to target assembly

* _IR_: compiler's internal format for generating machine code
* _bytecode_: distributable format for running in a VM

IR is for compilers:
* Internal representation
* Gets compiled away
* Never executed directly
* Optimized for compiler transformations
* Examples: LLVM IR, GCC GIMPLE

Bytecode is for VMs:
* Shipping format
* Gets interpreted/JIT compiled
* Directly executed by VM
* Optimized for interpretation
* Examples: JVM bytecode, Python bytecode, WebAssembly

There's some middle ground:
* _WASM_: Started as bytecode for browsers but now also used as compiler target https://web.dev/blog/ruby-on-rails-on-webassembly
* _JVM_: Uses intermediates between bytecode and machine code during JIT
* _.NET_: Has both IL (bytecode) and internal compiler IR

WASM 📙 https://wasmgroundup.com/
* compilation target for browsers that supports non-JS languages https://words.steveklabnik.com/is-webassembly-the-return-of-java-applets-flash
* https://sqlite.org/wasm/doc/tip/about.md
* https://rsms.me/wasm-intro
* https://neugierig.org/software/blog/2024/04/rust-wasm-to-js.html
* https://antonz.org/go-1-24/
* https://news.ycombinator.com/item?id=41851051

```python
from llvmlite import ir, binding
binding.initialize()
binding.initialize_native_target()
binding.initialize_all_asmprinters()
module = ir.Module(name="my_language_module")
def create_add_function():
    func_type = ir.FunctionType(ir.IntType(32), [ir.IntType(32), ir.IntType(32)])
    func = ir.Function(module, func_type, name="add")
    block = func.append_basic_block(name="entry")
    builder = ir.IRBuilder(block)
    a, b = func.args
    result = builder.add(a, b)
    builder.ret(result)
    return func
add_func = create_add_function()
print(module)
"""
; ModuleID = "my_language_module"
define i32 @add(i32 %0, i32 %1) {
entry:
  %2 = add i32 %0, %1
  ret i32 %2
}
"""
```

```txt
To make this a complete language, you'd need to:

Build a lexer/parser for your syntax (consider using ANTLR or writing custom)
Design your AST representation
Write an IR generator that walks your AST and generates LLVM IR
Handle memory management (LLVM provides garbage collection utilities)
Add a type system
Build standard library

Some key design decisions:

Static vs Dynamic typing
Memory management approach
FFI strategy (how to call C functions)
Error handling model
Concurrency model

Alternative approaches worth considering:

Using WASM as target instead of LLVM
Building on top of an existing VM (like Python's or Java's)
Direct native code generation (harder but more control)
Tree-walking interpreter (simpler but slower)
```

## backend (code gen)

Backend (IR → Target)
- Target-specific optimization
- Register allocation
- Code generation
- Linking
- Binary emission

Code Generation
- Target Architecture
- Instruction Selection
- Register Allocation

Yes - specifically within the compilation pipeline, a backend binary is a file format after the intermediate representation (IR) phase but before the final linking stage.
It contains mostly machine code targeted for a specific CPU architecture, but often also includes:

Relocation information
Symbol tables
Debug info (if enabled)
Additional metadata needed by the linker

Common formats:

ELF (Linux/Unix)
Mach-O (macOS)
COFF/PE (Windows)

The key distinguishing feature vs a final executable is that backend binaries still need linking to resolve external symbols and combine with other object files into the final program.

```sh
mov eax, [y]
add eax, 5
mov [x], eax
```
```txt
Takes IR
Maps to target CPU instructions
Handles register allocation
Outputs machine code
Example: On x86, might become:
```

What you'll see is:
* Raw binary machine code instructions
* Interleaved with data sections
* Headers that tell the OS how to load it
* Symbol tables (unless stripped)

```sh
echo 'int main() { return 42; }' > test.c
gcc -o test test.c

xxd test        # Pretty hex dump
hexdump -C test # Another format
objdump -d test # Disassembled view
```

Common file formats you'll see:
* ELF (Linux)
* Mach-O (macOS)
* PE/COFF (Windows)

Each has their own header format but they all contain the actual machine code instructions that the compiler backend generated.

For deeper inspection:
* _nm_: shows symbols
* _readelf/otool_: show headers/sections
* _gdb/lldb_: can disassemble at runtime

## linking

🗄️ `c.md` packaging

* source
```c
// foo.c
extern int b_func(void);
int a_func(void) { return b_func() + 1; }

// bar.c
int b_func(void) { return 41; }
```
* compilation
```sh
# compile separately
gcc -c foo.c    # makes foo.o
gcc -c bar.c    # makes bar.o
```
* _linking_: combine multiple object files into final binary
```sh
gcc foo.o bar.o   # links them -> final executable
```

---

- Static vs. Dynamic Linking
- Relocation
- Object Files and Libraries

* static vs. dynamic https://astral.sh/blog/python-build-standalone
* https://docs.tigerbeetle.com/quick-start/

# 🔮 RUNTIME

- Memory management
- Garbage collection
- Exception handling
- FFI/ABI
- Virtual machines (if applicable)
- JIT compilation (if applicable)

* _abstract machine_: C's version of a virtual machine https://words.steveklabnik.com/should-you-learn-c-to-learn-how-the-computer-works
* _undefined behavior_: when an error happens but it's not thrown i.e. `TypeError` in Python might be mean the compiler just chugging along in C https://blog.regehr.org/archives/213 https://news.ycombinator.com/item?id=24363573
> Rust also keeps track of the original data: when it goes out of scope, any references to it are no longer valid. So the compiler can detect many kinds of dangling pointer bugs where you try to use a reference to a value that doesn’t exist any more. That results in undefined behaviour, which is a nice way of saying that something horrible will happen, and part of Rust’s value proposition is “no undefined behaviour—ever”. https://bitfieldconsulting.com/posts/rust-and-go
* _bitfield_: https://danluu.com/algorithms-interviews/
* _compilation_: https://jvns.ca/blog/2019/10/28/sqlite-is-really-easy-to-compile/
* _garbage collection_: (kinda) possible https://stackoverflow.com/a/5009966/6813490

## minimal

* C
* Rust https://lwn.net/Articles/997784/

## VMs

https://www.jmeiners.com/lc3-vm/

INTERPRETERS
* Python
* Ruby

JIT
* JVM
* v8

- Stack-based vs. Register-based
- Just-in-Time (JIT) Compilation
- Garbage Collection

## ABI

* https://en.wikipedia.org/wiki/Application_binary_interface
* https://news.ycombinator.com/item?id=24140848
* https://gankra.github.io/blah/c-isnt-a-language/
* https://hpyproject.org/
* https://news.ycombinator.com/item?id=41992899

- Calling Conventions
- Data Layout
- System Interfaces

## FFI

* _FFI_: how to call C https://scottlocklin.wordpress.com/2021/04/01/obvious-and-possible-software-innovations-nobody-does/ https://www.youtube.com/watch?v=-1_FDp84PDE JNI https://news.ycombinator.com/item?id=31353740 https://github.com/replit/ruspty
* _CFFI_: call C from Python https://pypi.org/project/cffi/ https://talkpython.fm/episodes/show/481/python-opinions-and-zeitgeist-with-hynek parser for C https://github.com/eliben/pycparser
* https://github.com/electronstudio/raylib-python-cffi
* call Python from C http://eradman.com/posts/extending-c-python.html

- Interoperability with Other Languages
- Library Binding

# 🔬 STATIC CODE ANALYSIS

## lint (ruff)

## type check (pyright)

https://github.com/microsoft/pyright

Primary Focus: Verifying that the types in your code match the declared or inferred expectations.
What It Does: Checks for type mismatches, enforces type annotations (or infers types), and ensures that function calls and operations are used in a type-safe manner.
Example: Pyright is primarily designed to catch type errors without running your code.

## symbol index (ctags)

📙 Neil practical ch. 16

* extracts symbols (functions, classes, variables) from code to build an index (tag file)
* tags used by editors for goto def

---

> The previously mentioned tag mechanism also works for jumping between files. The usual approach is to generate a tags file for the whole project you are working on. You can then quickly jump between all files in the project to find the definitions of functions, structures, typedefs, etc. The time you save compared with manually searching is tremendous; creating a tags file is the first thing I do when browsing a program. https://www.moolenaar.net/habits.html
> Include files contain useful information. But finding the one that contains the declaration you need to see can take a lot of time. Vim knows about include files, and can search them for a word you are looking for. The most common action is to lookup the prototype of a function. Position the cursor on the name of the function in your file and type [I: Vim will show a list of all matches for the function name in included files. If you need to see more context, you can directly jump to the declaration. A similar command can be used to check if you did include the right header files. https://www.moolenaar.net/habits.html
* _tag_: scope-defining keywords in your programming language https://www.youtube.com/watch?v=XA2WjJbmmoM 3:50
* _ctags_: index of tags https://en.wikipedia.org/wiki/Ctags https://www.youtube.com/watch?v=JWD1Fpdd4Pc&t=338s 7:30 🗄 `db.md` index

https://github.com/iggredible/Learn-Vim/blob/master/ch16_tags.md
https://www.youtube.com/playlist?list=WL
https://dev.to/iggredible/how-to-use-tags-in-vim-to-jump-to-definitions-quickly-2g28
* exuberant
* gutentags
* recently access tags
* ctags impl https://github.com/universal-ctags/ctags
* https://www.semicolonandsons.com/episode/Fluent-File-Navigation
* JetBrains just better at refactoring? https://news.ycombinator.com/item?id=34072714
* text expander https://github.com/espanso/espanso
* LSP https://news.ycombinator.com/item?id=34070458 https://news.ycombinator.com/item?id=37020610
* YouCompleteMe https://realpython.com/vim-and-python-a-match-made-in-heaven/#auto-complete 
* https://www.youtube.com/watch?v=XA2WjJbmmoM 24:30
* https://github.com/neoclide/coc.nvim https://www.youtube.com/watch?v=gnupOrSEikQ
* https://stackoverflow.com/questions/905005/python-and-intellisense https://www.youtube.com/watch?v=2f8h45YR494 https://www.youtube.com/watch?v=2f8h45YR494 https://www.youtube.com/watch?v=ZzyY_9SMfeY https://pmihaylov.com/vim-for-go-development/
* comby, sourcegraph https://comby.dev/ https://www.thoughtworks.com/radar/tools?blipid=202110077
* https://news.ycombinator.com/item?id=30819579
* https://www.youtube.com/watch?v=4f3AENLrdYo 
* https://www.youtube.com/watch?v=XA2WjJbmmoM 16:15
* https://www.youtube.com/watch?v=MP-FxMl0frk
* https://thoughtbot.com/upcase/navigating-ruby-files-with-vim
* https://thoughtbot.com/upcase/vim
* https://vimtricks.substack.com/p/vimtrick-open-file-to-line
* https://vimtricks.substack.com/p/vimtrick-open-to-a-pattern
* https://github.blog/2021-12-09-introducing-stack-graphs/

## semantic analysis (jedi)

⭐️ ctags on steroids via full AST?

* _jedi_: https://github.com/davidhalter/jedi https://www.pythonpodcast.com/episode-113-jedi-code-completion-with-david-halter/ 

```txt
Jedi distinguishes itself from ctags by parsing Python code, constructing an AST, and performing static analysis to comprehend symbols, imports, and definitions, unlike ctags' token pattern scanning.
Jedi employs parso for Python code parsing, constructing an AST. It conducts semantic analysis, managing variable definitions, scopes, and type inference, which enhances its dynamic aspect handling beyond a simple indexer like ctags.
Jedi, integrated with editors via LSP, performs name resolution, code inspection, and AST recursion. Unlike ctags, it provides context-aware completions and type inference, showcasing its analysis depth and dynamic capability.
Jedi leverages parso for Python AST parsing

Code Intelligence: Jedi analyzes Python code to infer types, provide completions, and determine definitions and references.
Static Analysis: While not primarily a type checker, it does perform static inference to understand code structure and semantics.

Code analyzers often offer a broader range of diagnostics including style and potential bugs.
Jedi is more tuned for real-time code intelligence in editors rather than broad code quality analysis.
```

## LSP

🗄️ `vim.md` LSP

---

treesitter https://github.com/codegen-sh/codegen
https://philz.dev/blog/language-server-db/ https://www.hytradboi.com/2025/603a4562-ba4f-4150-b6d0-8c0e4c1ed5f7-rubbing-a-database-on-a-language-server

* _pylance_: closed source, uses pyright https://github.com/microsoft/pylance-release/issues/4
* _pylyzer_: pyright but better? https://github.com/mtshiba/pylyzer https://news.ycombinator.com/item?id=41305941
```txt
Code Analyzer

Primary Focus: Examining the code for a broader range of issues beyond just type consistency.
What It Does: It can include static type checking as one facet but also covers areas like stylistic issues, potential bugs, code smells, and even performance or security hints.
Example: Pylyzer brands itself as a code analyzer, implying it looks at your code’s overall structure and quality, not only its type correctness.
```

* spec is vague, not really open source and driven/controlled by Microsoft, uses RPC https://www.youtube.com/watch?v=JjWNw7aOAYU [4:30,8:30]
* https://github.com/joshuadavidthomas/django-language-server
* https://github.com/golang/tools
* https://langserver.org/
* https://rust-analyzer.github.io/ https://nickgerace.dev/posts/how-i-read-the-rust-programming-language/

* _language server_: provides editor with code completion, syntax highlighting https://github.com/echasnovski/mini.nvim#general-principles
* enables: analysis, completion, navigation, linting https://www.youtube.com/watch?v=3a1PCir_aHs 0:40
* _vanilla_: OSS https://github.com/microsoft/python-language-server
* _LSP_: protocol for language servers and editors https://en.wikipedia.org/wiki/Language_Server_Protocol 📙 Neil modern [127]
* client = editor impl LSP, server = provides language info https://www.youtube.com/watch?v=C9X5VF9ASac 2:30
* created by Microsoft and RedHat https://www.youtube.com/watch?v=C9X5VF9ASac 1:15
* used as a synonym for language server https://www.youtube.com/watch?v=OhnLevLpGB4 2:35
* JetBrains has their own version of this https://news.ycombinator.com/item?id=33211373 https://blog.jetbrains.com/platform/2023/07/lsp-for-plugin-developers/
* Sourcegraph LSP https://sourcegraph.com/blog/the-self-driving-ide-is-coming
* BYO https://www.youtube.com/watch?v=jo3IChyh09U&list=WL
* https://github.com/Canop/bacon

# 🟨 ZA

SEMANTICS
* _compiler_: src -> machine code https://www.youtube.com/watch?v=QdnxjYj1pS0
* misused http://coconut-lang.org/
* you used to have to pay for a compiler https://x.com/zack_overflow/status/1852881457037074686
* _transpile_: src -> another HLA
* e.g. Typescript to JS
* e.g. current JS version to previous ECMAScript spec for older browser e.g. Babel https://www.vrk.dev/2019/07/11/why-is-modern-web-development-so-complicated-a-long-yet-hasty-explanation-part-1/

---

start here https://www.achaq.dev/blog/artemis https://www.achaq.dev/blog/compilers https://zserge.com/posts/post-apocalyptic-programming/

GRAMMAR
* BNF, notation, grammar https://langdev.stackexchange.com/questions/2692/how-should-i-read-type-system-notation
* _grammar_: syntax for programming language https://blog.robertelder.org/computer-science-for-engineers/

http://steve-yegge.blogspot.com/2007/06/rich-programmer-food.html
* _decompile_: https://github.com/isledecomp/isle

TYPES OF COMPILATION
* _just-in-time (JIT)_: https://eli.thegreenplace.net/2013/11/05/how-to-jit-an-introduction https://pycon-archive.python.org/2024/schedule/presentation/124/index.html https://www.hytradboi.com/2025/0a4d08fd-149e-4174-a752-20e9c4d965c5-a-quick-ramp-up-on-ramping-up-quickly https://www.hytradboi.com/2025/0c355c52-8bbc-49c3-a407-faa4a45248b9-can-we-democratize-jit-compilers
* https://pypy.org/posts/2025/01/musings-tracing.html
* _ahead-of-time (AOT)_: https://news.ycombinator.com/item?id=22346540 https://www.hytradboi.com/2025/0a4d08fd-149e-4174-a752-20e9c4d965c5-a-quick-ramp-up-on-ramping-up-quickly
* _adaptive_: quickening https://realpython.com/python311-new-features/#faster-code-execution https://github.com/brandtbucher/specialist

SEMANTICS
* _hot reload_: change program while it runs http://www.jakubkonka.com/2022/03/16/hcs-zig.html
* _inline cache_: https://en.wikipedia.org/wiki/Inline_caching https://bernsteinbear.com/blog/inline-caches-in-skybison/

| impl    | target  | link                                   |
|---------|---------|----------------------------------------|
| C       | C       | https://github.com/DoctorWkt/acwj      |

* _compilation target_: compilation fmt e.g. another lang (JS https://www.youtube.com/watch?v=3LWgbjVWLug 3:00) or binary (WASM) https://steveklabnik.com/writing/is-webassembly-the-return-of-java-applets-flash

times https://stackoverflow.com/q/846103
* _compile time_: compile code; err on static err (syntax, typing)
* _run time_: exec code; err on dynamic err (zero division, run out of mem)
* _import time_: exec code; leads to suble errors
> In Java, import foo means "I depend on the `foo` module; please have the virtual machine link me to it when I run." In Python, import `foo` means "look for `foo.py` in the path, execute it, store local variables in a module object, and assign that module to the `foo` variable in my scope." The difference is that the Python version can run essentially arbitrary code, including importing other modules which then import other modules in turn. https://www.benkuhn.net/importtime/

* linker https://news.ycombinator.com/item?id=27444647 https://gankra.github.io/blah/swift-abi/ 📙 Bryant (7)
https://web.eecs.utk.edu/~azh/blog/teenytinycompiler1.html

🗣 people to ask for help https://github.com/yiblet https://notes.eatonphil.com/starting-a-minimal-common-lisp-project.html
🔗 https://news.ycombinator.com/item?id=24066570
🔗 start here https://www.destroyallsoftware.com/screencasts/catalog
* hosted language: language using 3rd-party compiler (as Clojure uses JVM)
https://keleshev.com/compiling-to-assembly-from-scratch/ https://news.ycombinator.com/item?id=24609774

translators https://en.wikipedia.org/wiki/Symbol_table https://stackoverflow.com/a/3434252
* _assembler_: transform assembly to something less abstract, sometimes machine code and sometimes something a few levels up https://stackoverflow.com/questions/3434202/what-is-the-difference-between-native-code-machine-code-and-assembly-code/3434252#comment25665803_3434252
* _interpreter_: 
* _compiler_: transform high-level language to IR; 'self-hosting' is written in language it's compiling https://robertheaton.com/2017/10/24/what-is-a-self-hosting-compiler/

instructions
> where do virtual machines fit in this taxonomy? https://www.capitalone.com/tech/software-engineering/go-is-boring/
* _symbol table_: map of idenifiers (aka symbol) to type and scope https://en.wikipedia.org/wiki/Symbol_table#Example https://eli.thegreenplace.net/2010/09/18/python-internals-symbol-tables-part-1 https://drewdevault.com/2021/03/19/A-new-systems-language.html https://www.pixelstech.net/article/1728356198-Why-is-Golang-s-Compilation-Speed-So-Fast

implementations https://github.com/marcpaq/b1fipl
* make a Lisp https://news.ycombinator.com/item?id=21670442
* _JS_: https://github.com/jamiebuilds/the-super-tiny-compiler
* _Ruby_: Ruby Under a Microscope https://codon.com/compilers-for-free from Python https://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/
* _Python_: https://bernsteinbear.com/blog/bytecode-interpreters/ https://ruslanspivak.com/lsbasi-part1/ http://www.aosabook.org/en/500L/a-python-interpreter-written-in-python.html http://www.thedigitalcatonline.com/blog/2017/05/09/a-game-of-tokens-write-an-interpreter-in-python-with-tdd-part-1/ https://github.com/danistefanovic/build-your-own-x#build-your-own-programming-language http://aosabook.org/en/500L/a-python-interpreter-written-in-python.html https://codewords.recurse.com/issues/seven/dragon-taming-with-tailbiter-a-bytecode-compiler http://www.trevorblackwell.com/#faq https://blog.miguelgrinberg.com/post/building-a-toy-programming-language-in-python https://mathspp.com/blog/building-a-python-compiler-and-interpreter
* _general_: https://www.youtube.com/watch?v=wSdV1M7n4gQ&t=157s + https://increment.com/programming-languages/crash-course-in-compilers/ + https://blog.wesleyac.com/posts/language-todos + https://blog.felixangell.com/compilers-brief-and-brisk + https://medium.com/basecs
* _Jit_ https://www.youtube.com/watch?v=2BB39q6cqPQ https://eli.thegreenplace.net/2013/11/05/how-to-jit-an-introduction
* _Ball_: src not in repo https://www.reddit.com/r/golang/comments/5eiiw6/writing_an_interpreter_in_go_now_available/ user impl https://github.com/mmyoji/go-monkey https://github.com/skatsuta/monkey-interpreter https://github.com/ELD/monkey-lang-go https://github.com/dnutiu/monkeyInterpreter
* _SQL_: http://aosabook.org/en/sqlalchemy.html

clean up
* https://conroy.org/generating-code-examples
* _compiled_: src type checked, then run
* _reference implementation_: primary implementation of language (CPython) as compared to other alternate implementations (PyPy, Jython)
* need to have same errors
> We crashed Oracle, including commercial versions of Oracle. We crashed DB2. Anything we could get our hands on, we tried it and we managed to crash it, but the point was that we wanted to make sure that SQLite got the same answers for all of these queries, or equivalent answers, because a lot of these queries, they’re indeterminate and the rows might come out in a different order because you [crosstalk 00:25:10] order by clause, so we wanted to make sure that all the database engines got equivalent answers. Mostly, we wanted to make sure that SQLite was getting the same answers everybody else is. https://corecursive.com/066-sqlite-with-richard-hipp/
* syntax trees https://eli.thegreenplace.net/2009/02/16/abstract-vs-concrete-syntax-trees https://www.pythonpodcast.com/episode-113-jedi-code-completion-with-david-halter/
* _interpreted_: src code run straight away
* _JIT_: normal interpreter but will compile hot paths https://carolchen.me/blog/jits-impls/
* _output_: assembly (for GCC) https://cs.stackexchange.com/questions/14749/why-do-compilers-produce-assembly-code
* writing language compiler in that language https://stackoverflow.com/questions/18247888/how-can-a-c-compiler-be-written-in-c
* https://github.com/aalhour/awesome-compilers https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript https://medium.com/basecs https://ruslanspivak.com/lsbasi-part1/ https://nicoleorchard.com/blog/compilers https://github.com/jamiebuilds/the-super-tiny-compiler/blob/master/README.md http://aosabook.org/en/500L/static-analysis.html https://increment.com/programming-languages/crash-course-in-compilers/ https://corecursive.com/037-thorsten-ball-compilers/ https://news.ycombinator.com/item?id=22731505 https://www.pythoninsight.com/2018/09/python-basics-bytecode 

BNF https://realpython.com/python-bnf-notation/

* JIT https://tonybaloney.github.io/posts/python-gets-a-jit.html
* Bryant (5)
* Nisan nand2tetris (4, 6-11)

* Conery ch. 10
* bytecode, control flow graphs (CFG) https://bernsteinbear.com/blog/discovering-basic-blocks/

compilation
* _output_: machine code ['Go in Practice' 18]
* _CLI options_: `Wall` warn all `-o` choose own name instead of a.out `std` spec
```sh
gcc foo.c -Wall -o my_program m -std='c99'
./my_program
```
* `.a`: lib whose code is embedded into your library
* `.so`: lib whose code is referenced by your library https://stackoverflow.com/a/9809250
* _header file_: imports

* https://drewdevault.com/2017/02/22/cozy-devnotes-machine-specs.html
* _bootstrapping_: wrote core of compiler in another language and then use that core to build the rest of the compiler in the source language i.e. self-compilation https://softwareengineering.stackexchange.com/a/76640 https://stackoverflow.com/a/18126181 https://news.ycombinator.com/item?id=42311031
* _executable_: runtime + binary compatible with user os architecture
* for user's machine vs. your server https://testandcode.com/52 @ 29:00
* aka freeze in Python land https://docs.python-guide.org/shipping/freezing/

## output

📙 Bryant computer systems (3)
🧠 https://chatgpt.com/c/675884d8-9ac8-8004-9fb2-86345bc67c84

* _machine code_: binary; handled by compiler's backend https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/ via `objdump` 📙 Erickson hacking [21]
* _instuction set_: pattern of bits/int/char that map to cmd https://en.wikipedia.org/wiki/Machine_code#Instruction_set https://steveklabnik.com/writing/is-webassembly-the-return-of-java-applets-flash
* _intermediate representation (IR)_: final step before machine code; handled by compiler's front end https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/ MIR https://softwareengineeringdaily.com/2024/10/23/rust-vs-c-with-steve-klabnik-herb-sutter/ https://mattpo.pe/posts/sql-llvm/
* _instruction_: individual line of machine code https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/
* _bytecode_: step after src but before IR? uses hex? https://www.youtube.com/watch?v=QU158nGABxI 23:55 🗄 `python.md` interpreter https://github.com/MoserMichael/pyasmtool/blob/master/bytecode_disasm.md injection https://stackoverflow.com/questions/3470949/what-is-java-bytecode-injection https://github.com/yiblet/inquest  https://docs.python.org/3/glossary.html#term-bytecode

## taxonomy

```sh
build-systems/
├── compilers/
│   ├── frontend/
│   │   ├── lexer
│   │   ├── parser
│   │   └── AST
│   ├── middle/
│   │   ├── IR
│   │   └── optimizations/
│   │       ├── machine-independent/
│   │       └── target-specific/
│   └── backend/
│       ├── instruction-selection
│       ├── register-allocation
│       └── code-generation
│
├── linking/
│   ├── static/
│   │   └── LTO (Link Time Optimization)
│   └── dynamic/
│       ├── shared-libraries
│       └── runtime-loading
│
└── runtime-systems/
   ├── minimal/
   │   ├── c-abstract-machine
   │   └── rust-runtime
   ├── language-vms/
   │   ├── interpreters/
   │   │   ├── python
   │   │   └── ruby
   │   └── jit-vms/
   │       ├── jvm
   │       └── v8
   ├── abi/
   │   ├── calling-conventions
   │   ├── data-layout
   │   └── name-mangling
   └── ffi/
       ├── raw-ffi
       ├── generated-bindings
       └── language-specific/
           ├── cffi (Python)
           ├── jni (Java)
           └── cgo (Go)
```
