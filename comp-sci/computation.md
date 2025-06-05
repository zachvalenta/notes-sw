# ⛩️

## 参考

📚
* Arpaci
* Bryant
* Galvin
* Hyde great code
* Tanenbaum
* ⭐️ MacCormick computed

## 进步

https://littleosbook.github.io/

circuits, branch prediction, speculative execution https://danluu.com/branch-prediction/ https://pythonspeed.com/articles/speeding-up-numba/
++ like verilog? sequential logic https://github.com/cjdrake/seqlogic

* Verilog, VHDL https://danluu.com/why-hardware-development-is-hard/ https://news.ycombinator.com/item?id=42156516
* XLS, HardCaml https://rachit.pl/

---

https://www.youtube.com/watch?v=lX4CrbXMsNQ
https://github.com/hackclub/RAM-a-thon
https://www.youtube.com/playlist?list=PL77441A2ED0D0B6A8
https://www.youtube.com/playlist?list=PLH2l6uzC4UEW0s7-KewFLBC1D0l6XRfye
https://github.com/lusingander/enigma

* _14_: 📙 Gleick the information
* _11_: 📙 Hillis pattern in the stone

# 🪨 FOUNDATIONS

📚
* Conery ch. 1-4
* ✅ Gleick information
* ✅ Hillis pattern in the stone
* Justice how computers really work https://nostarch.com/how-computers-really-work Steinhart https://www.amazon.com/dp/1593279701
* MacCormick computed https://canvas.harvard.edu/courses/34992/assignments/syllabus
* MacCormick nine algorithms
* Nisan elements https://github.com/zachvalenta/nand2tetris https://news.ycombinator.com/item?id=42793597
* Petzold code; second edition https://www.amazon.com/Code-Language-Computer-Hardware-Software/dp/0137909101
* Petzold annotated turing

> A computer is a clock with benefits. They all work the same, doing second-grade math, one step at a time - Ford what is code?
> Everything ultimately has to get down to things in little boxes pointing to each other. That's just how things work. - Ford what is code?

```python
def computation():
    return human_significance(data=hw_automate_math_op(num_sys, logic_gate), encoding)
```

* _lambda calculus_: Conery chapter 3 https://www.youtube.com/watch?v=pkCLMl0e_0k https://news.ycombinator.com/item?id=27648871 https://www.youtube.com/watch?v=QuXJ3kXUCiU https://www.youtube.com/watch?v=ViPNHMSUcog https://news.ycombinator.com/item?id=42679191
* _non-determinism_: https://ahelwer.ca/post/2020-04-15-probabilistic-distsys/

TIME
* 📚 Kleppmann chapter 8 https://www.youtube.com/watch?v=U612mx16j7U
> Time is nature's way to keep everything from happening all at once - John Wheeler https://lwn.net/Articles/827180/

## gates

🗄 `philosophy.md` logic
📚
* Nisan nand2tetris ch. 1-3
* Petzold code ch. 10-11, 14
* Shibuya microprocessors ch. 1

---

todo
* https://reasonablypolymorphic.com/book/preface
* Ben Eater https://eater.net/8bit + 📚 Petzold code 17

BASICS
* _wire_: carries inputs and outputs https://reasonablypolymorphic.com/book/machine-diagrams
* _machine_: transform input to output https://reasonablypolymorphic.com/book/machine-diagrams

GATES
* gate/relay - abstraction for controlling current that can implement boolean logical operations
* transistor - gate impl; wire
* _gate_: controls path of current https://www.youtube.com/watch?v=gI-qXk7XojA 4:40 🗄 `science.md` engineering / valve
* physical implementation of boolean logic 
* components: wires (input, output)
* _transistor_: current from control wire connects current from two electrodes https://www.youtube.com/watch?v=gI-qXk7XojA 3:10 input (control wire) output (current) germanium  https://www.youtube.com/watch?v=LUXR8UnYhzc 📚 Petzold code 18

OPERATIONS
* _not_: move output in front of control wire, so input turned on (i.e. control wire touching electrodes) the current will flow to ground and not to output https://www.youtube.com/watch?v=gI-qXk7XojA 4:05
* _and_: two transistors in a row https://www.youtube.com/watch?v=gI-qXk7XojA 5:20
* _or_: two transistors in a parallel https://www.youtube.com/watch?v=gI-qXk7XojA 6:15

## information theory

🗄 `sociology.md` linguistics
📚
* MacCormick 9 algorithms
* Gleick information
* https://www.khanacademy.org/computing/computer-science/informationtheory

SIGNAL/NOISE 📙 Gleick ch. 7-8
* _digital_: discrete values for signal representation e.g. light switch 📙 Shibuya 1.31
* _analog_: continuous values for signal representation e.g. light dimmer 📙 Kozeriok 4.62
* _noise_: more important than / independent from bias https://conversationswithtyler.com/episodes/daniel-kahneman/ 🗄 `psychology.md` bias

### compression

🗄️ `serde.md` Parquet

---

* _zstandard_: https://peps.python.org/pep-0784/
* https://blog.startifact.com/posts/succinct/
* _lzma_: 
* _lossy_: data removed in way mostly unnoticed by end user e.g. mp3
* _lossless_: no data rm, original data can be reconstructed e.g. JS minification 📙 Shibuya 1.33
* https://www.destroyallsoftware.com/screencasts/catalog https://go-compression.github.io/ Grudzinski 40
* MacCormick chapter 7
* https://tech.marksblogg.com/minimalist-guide-compression.html
* video streaming https://news.ycombinator.com/item?id=40408515

COMPRESSION
```txt
SNAPPY
* Faster compression/decompression
* Worse compression ratio (~2-3x reduction)
* Default in many systems because it prioritizes speed
* Good for data that needs frequent access

ZSTD
* Better compression ratio (~4-5x reduction)
* Slightly slower compression/decompression
* Configurable compression levels (1-22)
* Good for data that's accessed less frequently

Both are significantly better than gzip/bzip2 for typical data workloads. They fit into a broader family:
* lz4: Even faster than Snappy, worse compression
* brotli: Better compression than zstd, much slower
* gzip: Legacy option, generally worse at both speed and size
```

### entropy

https://news.ycombinator.com/item?id=43684560

> Entropy is a measure of disorderliness, and the declaration that entropy is always on the rise — known as the second law of thermodynamics — is among nature’s most inescapable commandments. https://www.quantamagazine.org/what-is-entropy-a-measure-of-just-how-little-we-really-know-20241213/

* https://github.com/Racum/uuinfo
* https://math.ucr.edu/home/baez/what_is_entropy.pdf https://johncarlosbaez.wordpress.com/2024/07/20/what-is-entropy/
* entropy per word https://entropicthoughts.com/reading-slightly-more-incrementally
> got here from "how to create session ID in Python?" 🗄 `http.md` https://stackoverflow.com/questions/817882/unique-session-id-in-python https://unix.stackexchange.com/a/361789
* https://victorzhou.com/blog/information-gain/
* https://aatishb.com/entropy/
* https://www.youtube.com/results?search_query=khan+academy+entropy
* used to build decision trees https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/

## logic

📚
* Villa https://www.manning.com/books/causal-inference-for-data-science
* Wayne logic for programmers

---

* _conjunction_: https://en.wikipedia.org/wiki/Logical_conjunction

https://blog.danielh.cc/blog/sat https://news.ycombinator.com/item?id=42261166
* https://en.wikipedia.org/wiki/Conjunctive_normal_form
https://chatgpt.com/c/6752e532-0960-8004-8d1e-766cda9729f4
https://blog.danielh.cc/blog/numbers
https://blog.danielh.cc/blog/classes
> I wish I went to school for English and CS

### SAT

> In logic and computer science, the Boolean satisfiability problem (sometimes called propositional satisfiability problem and abbreviated SATISFIABILITY, SAT or B-SAT) is the problem of determining if there exists an interpretation that satisfies a given Boolean formula. In other words, it asks whether the variables of a given Boolean formula can be consistently replaced by the values TRUE or FALSE in such a way that the formula evaluates to TRUE. If this is the case, the formula is called satisfiable. On the other hand, if no such assignment exists, the function expressed by the formula is FALSE for all possible variable assignments and the formula is unsatisfiable. https://en.wikipedia.org/wiki/Boolean_satisfiability_problem

```python
def validate_config(config):
    """
    >>> config = {
    ...     'debug_mode': True,
    ...     'production_mode': True,
    ...     'logging_level': 'DEBUG'
    ... }
    >>> validate_config(config)
    False

    A config that requires mutually exclusive conditions:
    1. debug_mode must be True
    2. If debug_mode is True, production_mode must be False
    3. If logging_level is DEBUG, production_mode must be True
    4. logging_level must be DEBUG
    """
    constraints = [
        config['debug_mode'] is True,                    # (1)
        not (config['debug_mode'] and                    # (2)
             config['production_mode']),      
        (config['logging_level'] == 'DEBUG' and         # (3)
         config['production_mode'] is True),
        config['logging_level'] == 'DEBUG'              # (4)
    ]
    
    return all(constraints)
```

* _SAT solver_: https://timefold.ai/blog/how-i-built-an-ai-company-to-save-my-open-source-project
> While a SAT solver is an algorithmic tool, it is not a single algorithm but rather an implementation of one or more solving techniques. The choice of technique (e.g., DPLL, CDCL, WalkSAT) depends on the solver's design.
> Graph Algorithms: Many SAT problems can be modeled as graph problems (e.g., coloring, cliques).
* _CNF (conjunctive normal form)_: standardized way of writing boolean formulas as a conjunction (AND) of disjunctions (OR)
* every boolean formula can be converted to cnf
* SAT solvers typically require input in CNF
* many proofs about boolean satisfiability work on CNF
* _clause_: individual con/disjunction
```python
from pysat.formula import CNF
from pysat.solvers import Glucose3

def check_config_sat():
    """
    >>> check_config_sat()
    'UNSAT'
    """
    formula = CNF()
    # 1: debug_mode (D)
    # 2: production_mode (P) 
    # 3: logging_level_debug (L)
    formula.append([1])           # D must be true
    formula.append([-1, -2])      # ¬D ∨ ¬P
    formula.append([-3, 2])       # ¬L ∨ P
    formula.append([3])           # L must be true
    solver = Glucose3()
    solver.append_formula(formula)
    if solver.solve():
        model = solver.get_model()
        return f"SAT: {model}"
    else:
        return "UNSAT"
```

USAGE
* Database constraints (circular foreign keys)
* Network configurations (routing loops)
* formal methods
* State machines (deadlocks)
* When configuring software with multiple options (e.g., enabling/disabling features), SAT solvers can validate configurations to avoid conflicts.
* In package management systems (e.g., npm, pip), SAT solvers ensure that dependencies are consistent and satisfiable. Example: Determining if a specific combination of library versions satisfies all constraints. e.g. CICD Ensuring all dependency graphs are satisfiable before deploying software updates.
* Modeling user workflows as a SAT problem to ensure all paths are tested.
* SAT solvers can generate inputs that exercise specific paths in the code, ensuring better test coverage. Example: Generating tests for edge cases that are otherwise hard to identify.
* SAT solvers can help solve scheduling problems, such as assigning tasks to machines or people while respecting constraints.
* Optimize the selection of test cases to cover all code paths or requirements with the smallest possible suite.

## machines

📚
* MacCormick ch. 10
* Petzold annotated turing

---

ZA
* _stack machine_: used in VM design along w/ register machine https://tech.davis-hansson.com/p/congress-is-a-vm/
* _halting problem_: a program which could analyse an arbitrary other program and tell if it would halt / stop running cannot exist https://blog.robertelder.org/computer-science-for-engineers/ https://tigyog.app/d/C:tWWwvJDWlo/r/busy-beavers https://buttondown.com/hillelwayne/archive/the-halting-problem-is-a-terrible-example-of-np/
* _incompleteness theorem_: https://tigyog.app/d/C:tWWwvJDWlo/r/busy-beavers
* _Von Neumann architecture_: model for hardware that allowed for data input via memory vs. rewiring hardware itself https://blog.robertelder.org/computer-science-for-engineers/

### turing machine

* https://snarky.ca/mvpy-minimum-viable-python/
* https://news.ycombinator.com/item?id=41633551
* _Turing complete_: functional parity w/ Turing machine https://www.youtube.com/watch?v=dNRDvLACg5Q
```python
if state == state359 and current_tape_location == 1:
    current_tape_location == 0
    goto(state247)
# and so on
else state == done:
    render_answer()
    goto(halting_state)
```

### state machine

🗄️ `system/distributed.md`

* start here https://www.achaq.dev/blog/distributed-systems-state-machines-special-relativity
* https://github.com/kyleconroy/lua-state-machine
* https://zackproser.com/blog/bubbletea-state-machine
* diagrams https://github.com/statecharts/statecharts.github.io/issues/44 https://en.wikipedia.org/wiki/State_diagram
* _finite state machine (FSM)_: machine w/ fixed set of possible states 📙 Conery 66 https://nullprogram.com/blog/2020/12/31/ https://arpitbhayani.me/blogs/fsm
* input not idempotent e.g. ball point pen https://www.youtube.com/watch?v=4rNYAvsSkwk https://arpitbhayani.me/blogs/fsm https://www.youtube.com/watch?v=nG_ZsNxRz0o
* Jira ticket stages would be another example https://news.ycombinator.com/item?id=24409556 https://github.com/alysivji/finite-state-machine https://github.com/statelyai/xstate
* DFA https://en.wikipedia.org/wiki/Deterministic_finite_automaton
* state machine replication https://signalsandthreads.com/state-machine-replication-and-why-you-should-care/

# 💻 HARDWARE

🗄 `science.md` electricity
🎓 computer engineering https://chatgpt.com/c/671121b1-633c-8004-88ee-bcc142ac24f5
📚
* Matthews dive https://diveintosystems.org/
* Shibuya microprocessors
* Upton rapsberry pi
* Upton rapsberry pi

FIRMWARE
* _firmware_: software embedded in and specific to its hardware host
* _BIOS (basic IO)_: firmware that gives option of where to boot from; can boot from vinyl https://news.ycombinator.com/item?id=25177045
* _UEFI_: newer version of BIOS that's apparently more of a pain https://www.youtube.com/watch?v=mxA9Gyyu6Rg 5:45 https://news.ycombinator.com/item?id=42264345
* _boot_: BIOS -> bootloader (GRUB) -> OS
> Booting an operating system consists of transferring control along a chain of small programs, each one more “powerful” than the previous one, where the operating system is the last “program” https://littleosbook.github.io/#introduction
* _CMOS_: chip that holds BIOS

za
* _acceleration_: hw for specialized tasks e.g. TPU https://en.wikipedia.org/wiki/Hardware_acceleration https://danluu.com/learning-to-program/
* _embedded system_: os for larger mechanical device, probably doesn’t have file system or long-term storage
* _ESP8266_: system on a chip, MicroPython, PikaScript https://news.ycombinator.com/item?id=31433815
* _FPGA_: things you can program with Verilog, VHDL https://www.youtube.com/watch?v=opRJLoA55bQ
* _laptop_: non-unibody (easier to repair) unibody (Macbook; harder to switch battery, repair) https://www.netbooknews.com/tips/what-is-a-unibody-laptop/
* _microcontroller_: special-purpose computer, often embedded in another device 📙 Shibuya chapter 6
* _quantum_: used for physics simulations; qubit (like traditional bit 0/1 when observed, but when not observed represents probability of 0/1) https://news.ycombinator.com/item?id=22994468 📚 Gleick 13 https://quantum.country/ https://academy.meetiqm.com/curriculum/index.html
* _transparent_: not visible/controllable e.g. L1 cache transparent to compiler https://www.reddit.com/r/compsci/comments/95ns21/what_is_difference_between_register_and_l1_cache/
* _UPS_: uninterruptible power supply (backup juice for proper shutdown)
* robots https://news.ycombinator.com/item?id=42382357

## chips

📚
* Hijink asml way https://www.amazon.com/Focus-Inside-struggle-complex-machine/dp/B0D7DRJL2W
* Miller chip war

* _silica_: mineral extracted from sand
* _silicon_: element formed by rm oxygen from silica; btw aluminum and phosphorus; by itself only a semiconductor
* _wafer_: larger piece of processed silicon
* _diode_: is a conductor that allows current flow in one direction
* _semiconductor_: https://www.youtube.com/watch?v=qCSIGejNT4M https://twitter.com/szeloof/status/1280249239495479297 https://blog.robertelder.org/semiconductor-example-uses/

> With computing, there have been a couple different cases of scaling breakthroughs. One of them was the discovery of the vacuum tube, where you actually have a device that can do fairly simple logical operations such that you can implement it in a machine. Then we ran into this problem of, the vacuum tubes are mechanical, they do break, and so the bigger your machine, the more likely it is that it breaks; the more complicated your algorithm is, the more likely it is that something breaks down. So you have one of those dynamics where you're scaling your inputs a lot faster than you're scaling your outputs and you're doing things less and less efficiently over time. Then transistors do not actually have moving parts, so they don't have that particular problem – but they run into their own scaling obstacle. It's really fun to read about the early days of this: one of the books that I cite in Boom has an excerpt from, not Scientific American but a magazine of that type in the 50s, where it's speculating that perhaps in the future computers could be the size of a small house, and that's how much we could shrink them. But people ran into this problem with transistors, where the more of them that you connect – and you need all of them to be connected and working for that particular cluster of them to do anything useful – the more of them you connect, the more likely it is that you have one little issue somewhere that makes the whole thing not work. Then it turned out that there was a way around that too, which is that you don't actually plug together individual discrete devices, you actually etch the entire set of connections chemically, and now with many other things – but yeah, you etch it, a one shot [process] where you create one solid thing. That turned out to be a much more scalable architecture. https://www.complexsystemspodcast.com/episodes/boom-busts-and-long-term-progress-with-byrne-hobart-2/

MANUFACTURING https://doxa.substack.com/p/why-a-chinese-invasion-of-taiwan
* https://stratechery.com/2024/intels-death-and-potential-revival
* https://news.ycombinator.com/item?id=42051968
* _fabless_: you design, someone else manufacturers (AMD, Nvidia, Qualcomm, Apple) https://www.youtube.com/watch?v=Jyp6jFCzW44
* _foundry_: manufacturing (TSMC, Intel, Samsung, GlobalFoundries) https://stratechery.com/2020/chips-and-geopolitics Intel one of the few that does both design and manufacturing https://stratechery.com/2022/the-intel-split/ Morris Chang https://news.ycombinator.com/item?id=42559052
* _HDL_: software for designing chips
* ARM has more balance btw battery life and perf, x86 more perf https://diff.substack.com/p/taiwan-and-supply-chain-frenmity
* cloud computing kept Intel going after they lost smartphones https://stratechery.com/2021/intel-problems/
> Intel both designs and makes chips, whereas TSMC mostly makes other people's designs for them - hence it makes Apple's custom ARM-based CPUs for iPhones and now Macs. - Evans 2020.07.28
> After all, nearly all mobile chips are centered on the ARM architecture...It is manufacturing capability, on the other hand, that is increasingly rare...In fact, today there are only four major foundries: Samsung, GlobalFoundries, Taiwan Semiconductor Manufacturing Company (TSMC), and Intel. Only four companies have the capacity to build the chips that are in every mobile device today, and in everything tomorrow. https://stratechery.com/2021/intel-problems/

## form factors

📚
* Conery ch. 5

materials https://www.youtube.com/watch?v=LN0ucKNX0hc
* _relay_: 
* _vacuum tubes_: shift from electro-mechanical to electronic (i.e. no moving parts)
* _transistor_: switch controlled by electricity; like spigot on a tap https://www.youtube.com/watch?v=gI-qXk7XojA 3:00 invented at Bell Labs [Manga 1.32]
* _electrode_: conductor that makes contact w/ nonmetallic part of circuit (like a transistor) https://en.wikipedia.org/wiki/Electrode

timeline
* _1830_: Babbage analytical engine https://www.youtube.com/watch?v=O5nskjZ_GoI 8:45 differential analyzer https://twobithistory.org/2020/04/06/differential-analyzer.html
* _1890_: Hollerith machine (punch cards) for US census (https://en.wikipedia.org/wiki/Domesday_Book https://pase.ac.uk/) -> became IBM in 1924 https://www.youtube.com/watch?v=O5nskjZ_GoI 10:55 https://www.thediff.co/archive/longreads-open-thread-85/
* _1945_: Colussus - first programmable (configured w/ plugs) https://www.youtube.com/watch?v=LN0ucKNX0hc 6:10
* _1946_: ENIAC https://www.youtube.com/watch?v=LN0ucKNX0hc 6:45
* _1950_: IBM mainframes
* _1960_: minicomputers https://en.wikipedia.org/wiki/The_Soul_of_a_New_Machine https://en.wikipedia.org/wiki/Honeywell_316
* _1975_: Altair 8080 https://twobithistory.org/2018/07/22/dawn-of-the-microcomputer.html
* _1984_: Mac https://en.wikipedia.org/wiki/Macintosh#1984:_Debut

## memory

📚
* Arpaci ch. 13-23
* Bryant ch. 6
* Petzold code ch. 16
* Galvin ch. 8-9
🗄
* `plt.md` memory
* `linux.md` processes

RAM
* _RAM (random access memory)_: holds program/data until needed by CPU 📙 Manga [19] Kerrisk [2.1]
* aka memory, working memory https://www.interviewcake.com/article/python/data-structures-coding-interview
> RAM is just bigger-but-slower CPU cache. https://news.ycombinator.com/item?id=25056588 https://www.youtube.com/watch?v=WDIkqP4JbkE
* CPU cache https://lukasatkinson.de/2024/python-cpu-caching/
* _address_: location in RAM holding single byte
* untyped (unlike ALU register) https://www.interviewcake.com/article/python3/data-structures-coding-interview#ram
* _memory controller_: thing that reads/writes from memory addresses
* when CPU reads from controller also prefetches from nearby addresses https://www.interviewcake.com/article/python/data-structures-coding-interview
* _swap file_: free up mem via temp write to disk
> Swapfile is just bigger-but-slower RAM. https://news.ycombinator.com/item?id=25056588

VIRTUAL https://questions.wizardzines.com/virtual-memory.html
* _virtual memory_: disk used as memory when you run out of actual memory 📙 Evans linux [24] 📙 Bryant [9] https://questions.wizardzines.com/virtual-memory.html https://drewdevault.com/2018/10/29/How-does-virtual-memory-work.html
* _page_: chunk of virtual memory
* _page table_: map of page to physical address
* every process has its own 📙 Evans linux [16]
* _page fault_: attempt to read data from memory but instead forced to go to disk 📙 Evans linux [24]
* _swap area_: park of disk used as virtual memory https://serverfault.com/a/48487

---

* Babbage is overrated https://lcamtuf.substack.com/p/memory-the-forgotten-history
* _zero-copy_: op in which data not copied to another memory area https://en.wikipedia.org/wiki/Zero-copy https://duckdb.org/2021/12/03/duck-arrow.html https://www.hytradboi.com/2025/df37d71b-0552-47f9-af36-f53c9ee09f8f-zero-copy-data-structures

bits
* _bit depth_: [Franz 38, 226] bounce (mv from one bit depth to another) [Franz 226] https://reverb.com/news/home-recording-basics-ii-choosing-your-first-audio-interface-and-daw https://www.youtube.com/watch?v=JTtSihQ8QX0 2:45
* _word_: data unit used by architecture, aka digital word [Franz 38] registers and memory are word-sized e.g. 32-bit (90s, x86) 64-bit (00s, ARM64) https://stackoverflow.com/a/9287273 https://www.youtube.com/watch?v=IknbgnJLSRY 1:05 Upton raspberry pi 149 people still use 32-bit on 64-bit https://gankra.github.io/blah/c-isnt-a-language/ https://news.ycombinator.com/item?id=30704642 byte, word https://jvns.ca/blog/2023/03/06/possible-reasons-8-bit-bytes/
> Yet, Python integers are interesting because they are not just 32-bit or 64-bit integers that CPUs work with natively. Python integers are arbitrary-precision integers, also known as bignums. This means that they can be as large as we want, and their sizes are only limited by the amount of available memory. https://tenthousandmeters.com/blog/python-behind-the-scenes-8-how-python-integers-work/
* _bit field_: access individual bits in order to save space i.e. instead of normal disregard for storage size of, say, an int, you go and fiddle with how int stored so it doesn't take up as much space as bits normally take in your language (32, 64, whatever) https://www.youtube.com/watch?v=aMAM5vL7wTs
* _bit mask_: pattern of bits that updates another pattern of bits https://www.youtube.com/watch?v=Ew2QnDeTCCE
* _endianness_: order of byte storage https://www.youtube.com/watch?v=OoHich9BPxg https://www.youtube.com/watch?v=NcaiHcBvDR4 https://www.ntietz.com/blog/endianness/
* _big endian_: most significant byte at smallest memory address and vice versa https://perldoc.perl.org/perlglossary#big-endian
* _little endian_: least significant byte at smallest memory address https://corecursive.com/066-sqlite-with-richard-hipp/
* _endian_: put most significant bit first or last

* _mmap_: Linux program that maps disk to memory https://brunocalza.me/discovering-and-exploring-mmap-using-go/ 📙 `evans-linux.pdf` 24

* _ROM_: measured in megahertz
* _buffer overflow_: buffer writes to adjacent memory instead of intended location; useful to escalate privilege e.g. Morris worm
* _continguous_: buffer https://docs.python.org/3/glossary.html#term-contiguous

## storage

📚
* Galvin 10
* Tanenbaum 5.4
* Arpaci ch. 36-45

* _storage_: slower access (vs. mem)
* _disk_: slower than memory, more space https://www.interviewcake.com/article/python3/data-structures-coding-interview typically cheaper than RAM [Kleppmann 88]
* _platter_: storage medium
* _head_: thing that reads/write from platter; sequential access because has to physically move across platter https://www.interviewcake.com/article/python/data-structures-coding-interview#ram
> In the ’80s and ’90s, our hard drives were essentially optimized record players, with a read head riding on top of a spinning platter. - https://www.moderndescartes.com/essays/data_oriented_python/
* _actuator_: moves about for head to read
* _sector_: 类似 attribute
* _block_: 类似 record https://ownyourbits.com/2018/05/02/understanding-disk-usage-in-linux/ aka 'cluster'
* _slack space_: unused blocks
* _how is data stored?_ don’t need to be contiguous i.e. OS keeps track of what is where [Think OS 4.2]
* _content-addressed storage (CAS)_: store using cryptographic hash as key [Itamar 'software is a means not an end']
* _defragment_: putting things in same file closer together on platter [Franz 82]

* storage medium
| type      | full name   | notes                     
| --------- | ----------- | -------------------------
| HDD       | hard disk   | slowest (2-6 ms to read   
| SSD       | solid state | faster                    
| SSHD      | hybrid      | HDD w/ 16GB of SSD        
| flash     | -           | fastest; non-volatile RAM 
| long-term | -           | https://archiveprogram.github.com/ https://spectrum.ieee.org/computing/hardware/why-the-future-of-data-storage-is-still-magnetic-tape
| --------- | ----------- | ------------------------- 

# 🌌 PROCESSORS

🔗 https://cpu.land/
📚
* Christian chapter 5
* Galvin chapter 6
* Tanenbaum chapter 8

---

https://danluu.com/new-cpu-features/

scheduling 🗄 `linux.md` processes
* https://wizardzines.com/comics/cpu-scheduling/

* _processor_: aka CPU; can have n cores (i.e. parallelism) https://stackoverflow.com/q/19225859 can only add and subtract [Manga 1.15] https://www.righto.com/2024/08/pentium-navajo-fairchild-shiprock.html
> No human can possibly hope to understand a modern high-performance CPU well enough to informally reason about its correctness. That's not only true now, it's been true for decades. It becomes true the moment someone introduces any sort of speculative execution or caching. These things are inherently stateful and complicated. They're so complicated that the only way to model performance (in order to run experiments to design high performance chips) is to simulate precisely what will happen, since the exact results are too complex for humans to reason about and too messy to be mathematically tractable. It's possible to make a simple CPU, but not one that's fast and simple. https://danluu.com/tests-v-reason/
* _core_: main component that reads from memory, maintains execution order and state, and uses ALU to perform operations https://stackoverflow.com/a/19314303 https://testdriven.io/blog/developing-an-asynchronous-task-queue-in-python/
* _core types_: physical (what it sounds like) logical (abstraction to facilitate hyperthreading) https://stackoverflow.com/q/1715580 https://forums.tomshardware.com/threads/what-is-the-difference-between-physical-core-and-logical-core.1534416/
* _hyperthreading_: single core that can execute n instructions simultaneously
* _NPU_: good for lower power consumption? https://news.ycombinator.com/item?id=41863460
* _Apple silicon_: processor that uses ARM64

❓ how do chips relate to processor
* _chip_: piece of silicon holding approx B transistor; made by Intel, ARM, AMD, Qualcomm
* _processor_: main chip https://blog.robertelder.org/how-to-make-a-cpu/
* _chip set_: other chips that help out processor
* _PCB_: holds chips and all the wiring; made of fiberglass; motherboartd is a type of https://www.youtube.com/watch?v=Z2LgmIGE2nI
* _trace_: copper wires carrying electricity around PCB

operations
* _clock speed/rate/cycle_: interval at which processor can do something; ARM (1 clock cycle per instruction; efficient) x86 (n clock cycle per instruction; performant)
* _speed_: measured in gigahertz i.e. how many billion cycles happen per second; base speed and turbo https://www.bhphotovideo.com/explora/computers/tips-and-solutions/boost-processors
* _idling_: entering a lower power stage when no instructions to execute; cost to enter/exit idle, so don't want to do for overly short periods

* modern microprocessors https://news.ycombinator.com/item?id=27014027

## ALU

---

* _ALU_: executes on opcode 📙 Shibuya [23] https://en.wikipedia.org/wiki/Arithmetic_logic_unit#Implementation
* _opcode_: operator and operand https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/ https://tech.marksblogg.com/faster-python.html
* _data path_: how much data moves around circuit e.g. computer data pathes generally 1 byte wide [Petzold 180]
* _cache_: caches RAM for processor, needs a few more cycles to read than registers https://www.reddit.com/r/compsci/comments/95ns21/what_is_difference_between_register_and_l1_cache/e3u4tlt e.g. L1 cache https://www.ardanlabs.com/blog/2023/07/getting-friendly-with-cpu-caches.html https://news.ycombinator.com/item?id=40365248
* _register_: internal to processor i.e. not memory https://stackoverflow.com/a/9287273 size can vary on data type held e.g. 80 bits for floating point https://lock.cmpxchg8b.com/zenbleed.html

## ISA

📙 Bryant ch. 4 https://en.wikipedia.org/wiki/Instruction_set_architecture

* _ISA_: interface for processor 📙 Evans Linux 1, PG hackers and painters 179
* defines processor instructions, virtual memory, etc. https://en.wikipedia.org/wiki/Instruction_set_architecture
* _ARM64_: ARM for desktops
* _x86_: https://github.com/cirosantilli/x86-bare-metal-examples#china
📍 port in notes from 'memory'
* https://drewdevault.com/2021/03/19/A-new-systems-language.html
* ARM, RISC V https://riscv.org/ https://www.youtube.com/watch?v=Lo63uDIiCH0 https://danluu.com/butler-lampson-1999/ https://www.wired.com/story/angelina-jolie-was-right-about-risc-architecture
* https://www.jeffgeerling.com/blog/2020/raspberry-pi-cluster-episode-4-minecraft-pi-hole-grafana-and-more
* https://www.jeffgeerling.com/blog/2020/what-does-apple-silicon-mean-raspberry-pi-and-arm64

## GPU

---

* _CUDA_: GPUs aaS https://www.youtube.com/watch?v=hh0hK6UDQw0 https://www.pyspur.dev/blog/introduction_cuda_programming
* not always faster https://news.ycombinator.com/item?id=42389383
* https://github.com/taichi-dev/taichi
* _GPU_: https://news.ycombinator.com/item?id=23986925 https://lwn.net/Articles/827596/ https://codeconfessions.substack.com/p/gpu-computing https://codeconfessions.substack.com/p/gpu-computing https://news.ycombinator.com/item?id=42042016
> GPUs are much less complex than CPUs; that means they can execute instructions much more quickly, but those instructions have to be much simpler. At the same time, you can run a lot of them at the same time to achieve outsized results. Graphics is, unsurprisingly, the most obvious example: every "shader" - the primary processing component of a GPU - calculates what will be displayed on a single portion of the screen; the size of the portion is a function of how many shaders you have available. If you have 1,024 shaders, each shader draws 1/1,024 of the screen. Ergo, if you have 2,048 shaders, you can draw the screen twice as fast. Graphics performance is "embarrassingly parallel", which is to say it scales with the number of processors you apply to the problem. https://stratechery.com/2023/china-chips-and-moores-law/
