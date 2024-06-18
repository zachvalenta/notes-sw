# ⛩️

## 参考

📚
* Arpaci
* Bryant
* Galvin
* ✅ Gleick information
* ✅ Hillis pattern in the stone
* Hyde great code
* Matthews dive https://diveintosystems.org/
* MacCormick computed
* MacCormick nine algorithms
* Nisan elements https://github.com/zachvalenta/nand2tetris
* Petzold annotated turing https://www.amazon.com/gp/product/1400075998
* Petzold code
* Shibuya microprocessors
* Tanenbaum
* Upton rapsberry pi

## 进步

* _14_: 📙 Gleick the information
* _11_: 📙 Hillis pattern in the stone

# 🪨 FOUNDATIONS

📙 Conery ch. 1-4

> A computer is a clock with benefits. They all work the same, doing second-grade math, one step at a time - Ford what is code?
> Everything ultimately has to get down to things in little boxes pointing to each other. That's just how things work. - Ford what is code?

```python
def computation():
    return human_significance(data=hw_automate_math_op(num_sys, logic_gate), encoding)
```

* _lambda calculus_: Conery chapter 3 https://www.youtube.com/watch?v=pkCLMl0e_0k https://news.ycombinator.com/item?id=27648871 https://www.youtube.com/watch?v=QuXJ3kXUCiU
* _non-determinism_: https://ahelwer.ca/post/2020-04-15-probabilistic-distsys/

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

COMPRESSION
* _lossy_: data removed in way mostly unnoticed by end user e.g. mp3
* _lossless_: no data rm, original data can be reconstructed e.g. JS minification 📙 Shibuya 1.33
* https://www.destroyallsoftware.com/screencasts/catalog https://go-compression.github.io/ Grudzinski 40
* MacCormick chapter 7
* https://tech.marksblogg.com/minimalist-guide-compression.html
* video streaming https://news.ycombinator.com/item?id=40408515

ENTROPY
> got here from "how to create session ID in Python?" 🗄 `http.md` https://stackoverflow.com/questions/817882/unique-session-id-in-python https://unix.stackexchange.com/a/361789
* https://victorzhou.com/blog/information-gain/
* https://aatishb.com/entropy/
* https://www.youtube.com/results?search_query=khan+academy+entropy
* _entropy_: 
* used to build decision trees https://www.freecodecamp.org/news/a-no-code-intro-to-the-9-most-important-machine-learning-algorithms-today/
* _information gain_: 
* _decision tree_: 

## logic gates

🗄 `philosophy.md` logic
📚
* Nisan nand2tetris ch. 1-3
* Petzold code ch. 10-11, 14
* Shibuya microprocessors ch. 1

todo
* Crash Course computer science https://www.youtube.com/playlist?list=PLH2l6uzC4UEW0s7-KewFLBC1D0l6XRfye @ 4 6:45
* https://reasonablypolymorphic.com/book/preface
* Ben Eater https://eater.net/8bit + 📚 Petzold code 17

BASICS
* _wire_: carries inputs and outputs https://reasonablypolymorphic.com/book/machine-diagrams
* _machine_: transform input to output https://reasonablypolymorphic.com/book/machine-diagrams

GATES
* gate/relay - abstraction for controlling current that can implement boolean logical operations
* transistor - gate impl; wire
* _gate_: control path of current https://www.youtube.com/watch?v=gI-qXk7XojA 4:40 🗄 `science.md` engineering / valve
* physical implementation of boolean logic 
* components: wires (input, output)
* _transistor_: current from control wire connects current from two electrodes https://www.youtube.com/watch?v=gI-qXk7XojA 3:10 input (control wire) output (current) germanium  https://www.youtube.com/watch?v=LUXR8UnYhzc 📚 Petzold code 18

OPERATIONS
* _not_: move output in front of control wire, so input turned on (i.e. control wire touching electrodes) the current will flow to ground and not to output https://www.youtube.com/watch?v=gI-qXk7XojA 4:05
* _and_: two transistors in a row https://www.youtube.com/watch?v=gI-qXk7XojA 5:20
* _or_: two transistors in a parallel https://www.youtube.com/watch?v=gI-qXk7XojA 6:15

## machines

📚
* MacCormick ch. 10
* Petzold annotated turing

---

ZA
* _stack machine_: used in VM design along w/ register machine https://tech.davis-hansson.com/p/congress-is-a-vm/
* _halting problem_: a program which could analyse an arbitrary other program and tell if it would halt / stop running cannot exist https://blog.robertelder.org/computer-science-for-engineers/ https://tigyog.app/d/C:tWWwvJDWlo/r/busy-beavers
* _incompleteness theorem_: https://tigyog.app/d/C:tWWwvJDWlo/r/busy-beavers
* _Von Neumann architecture_: model for hardware that allowed for data input via memory vs. rewiring hardware itself https://blog.robertelder.org/computer-science-for-engineers/

TURING MACHINE
* https://snarky.ca/mvpy-minimum-viable-python/
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

STATE MACHINE
* _finite state machine (FSM)_: machine w/ fixed set of possible states 📙 Conery 66 https://nullprogram.com/blog/2020/12/31/ https://arpitbhayani.me/blogs/fsm
* input not idempotent e.g. ball point pen https://www.youtube.com/watch?v=4rNYAvsSkwk https://arpitbhayani.me/blogs/fsm https://www.youtube.com/watch?v=nG_ZsNxRz0o
* Jira ticket stages would be another example https://news.ycombinator.com/item?id=24409556 https://github.com/alysivji/finite-state-machine https://github.com/statelyai/xstate
* DFA https://en.wikipedia.org/wiki/Deterministic_finite_automaton
* state machine replication https://signalsandthreads.com/state-machine-replication-and-why-you-should-care/

# 💻 HARDWARE

🗄 `science.md` electricity
📚
* Matthews dive https://diveintosystems.org/
* Shibuya microprocessors
* Upton rapsberry pi

firmware
* _firmware_: software tied to hardware
* _BIOS (basic IO)_: firmware that gives option of where to boot from; can boot from vinyl https://news.ycombinator.com/item?id=25177045
* _UEFI_: newer version of BIOS that's apparently more of a pain https://www.youtube.com/watch?v=mxA9Gyyu6Rg 5:45
* _boot_: BIOS -> bootloader (GRUB) -> OS
* _CMOS_: chip that holds BIOS

za
* _acceleration_: hw for specialized tasks e.g. TPU https://en.wikipedia.org/wiki/Hardware_acceleration https://danluu.com/learning-to-program/
* _embedded system_: os for larger mechanical device, probably doesn’t have file system or long-term storage
* _ESP8266_: system on a chip, MicroPython, PikaScript https://news.ycombinator.com/item?id=31433815
* _FPGA_: things you can program with Verilog, VHDL https://danluu.com/why-hardware-development-is-hard/
* _laptop_: non-unibody (easier to repair) unibody (Macbook; harder to switch battery, repair) https://www.netbooknews.com/tips/what-is-a-unibody-laptop/
* _microcontroller_: special-purpose computer, often embedded in another device 📙 Shibuya chapter 6
* _quantum_: used for physics simulations; qubit (like traditional bit 0/1 when observed, but when not observed represents probability of 0/1) https://news.ycombinator.com/item?id=22994468 📚 Gleick 13 https://quantum.country/ https://academy.meetiqm.com/curriculum/index.html
* _transparent_: not visible/controllable e.g. L1 cache transparent to compiler https://www.reddit.com/r/compsci/comments/95ns21/what_is_difference_between_register_and_l1_cache/ confusing terminologically https://en.wikipedia.org/wiki/Transparency_(human%E2%80%93computer_interaction)
* _UPS_: uninterruptible power supply (backup juice for proper shutdown)
* circuits, branch prediction https://danluu.com/branch-prediction/

## form factors

📚
* Conery ch. 5

chips
* _silica_: mineral extracted from sand
* _silicon_: element formed by rm oxygen from silica; btw aluminum and phosphorus; by itself only a semiconductor
* _wafer_: larger piece of processed silicon
* _diode_: is a conductor that allows current flow in one direction
* _semiconductor_: https://www.youtube.com/watch?v=qCSIGejNT4M https://twitter.com/szeloof/status/1280249239495479297 https://blog.robertelder.org/semiconductor-example-uses/

chip manufacturing https://doxa.substack.com/p/why-a-chinese-invasion-of-taiwan
* _fabless_: you design, someone else manufacturers (AMD, Nvidia, Qualcomm, Apple) https://www.youtube.com/watch?v=Jyp6jFCzW44
* _foundry_: manufacturing (TSMC, Intel, Samsung, GlobalFoundries) https://stratechery.com/2020/chips-and-geopolitics Intel one of the few that does both design and manufacturing https://stratechery.com/2022/the-intel-split/
* _HDL_: software for designing chips
* ARM has more balance btw battery life and perf, x86 more perf https://diff.substack.com/p/taiwan-and-supply-chain-frenmity
* cloud computing kept Intel going after they lost smartphones https://stratechery.com/2021/intel-problems/
> Intel both designs and makes chips, whereas TSMC mostly makes other people's designs for them - hence it makes Apple's custom ARM-based CPUs for iPhones and now Macs. - Evans 2020.07.28
> After all, nearly all mobile chips are centered on the ARM architecture...It is manufacturing capability, on the other hand, that is increasingly rare...In fact, today there are only four major foundries: Samsung, GlobalFoundries, Taiwan Semiconductor Manufacturing Company (TSMC), and Intel. Only four companies have the capacity to build the chips that are in every mobile device today, and in everything tomorrow. https://stratechery.com/2021/intel-problems/

materials https://www.youtube.com/watch?v=LN0ucKNX0hc
* _relay_: 
* _vacuum tubes_: shift from electro-mechanical to electronic (i.e. no moving parts)
* _transistor_: switch controlled by electricity; like spigot on a tap https://www.youtube.com/watch?v=gI-qXk7XojA 3:00 invented at Bell Labs [Manga 1.32]
* _electrode_: conductor that makes contact w/ nonmetallic part of circuit (like a transistor) https://en.wikipedia.org/wiki/Electrode

timeline
* _1830_: Babbage analytical engine https://www.youtube.com/watch?v=O5nskjZ_GoI 8:45 differential analyzer https://twobithistory.org/2020/04/06/differential-analyzer.html
* _1890_: Hollerith machine (punch cards) for US census (https://en.wikipedia.org/wiki/Domesday_Book) -> became IBM in 1924 https://www.youtube.com/watch?v=O5nskjZ_GoI 10:55
* _1945_: Colussus - first programmable (configured w/ plugs) https://www.youtube.com/watch?v=LN0ucKNX0hc 6:10
* _1946_: ENIAC https://www.youtube.com/watch?v=LN0ucKNX0hc 6:45
* _1950_: IBM mainframes
* _1975_: Altair 8080 https://twobithistory.org/2018/07/22/dawn-of-the-microcomputer.html
* _1984_: Mac https://en.wikipedia.org/wiki/Macintosh#1984:_Debut

## memory

📚
* Arpaci ch. 13-23
* Bryant ch. 6
* Petzold code ch. 16
* Galvin ch. 8-9
🗄
* `language.md` memory
* `linux.md` processes

RAM
* _RAM (random access memory)_: holds program/data until needed by CPU 📙 Manga [19] Kerrisk [2.1]
* aka memory, working memory https://www.interviewcake.com/article/python/data-structures-coding-interview
> RAM is just bigger-but-slower CPU cache. https://news.ycombinator.com/item?id=25056588
* _address_: location in RAM holding single byte
* untyped (unlike ALU register) https://www.interviewcake.com/article/python3/data-structures-coding-interview#ram
* _memory controller_: thing that reads/writes from memory addresses
* when CPU reads from controller also prefetches from nearby addresses https://www.interviewcake.com/article/python/data-structures-coding-interview
* _swap file_: free up mem via temp write to disk
> Swapfile is just bigger-but-slower RAM. https://news.ycombinator.com/item?id=25056588

VIRTUAL https://questions.wizardzines.com/virtual-memory.html
* _virtual memory_: disk used as memory when you run out of actual memory 📙 Evans linux [24] 📙 Bryant [9] https://questions.wizardzines.com/virtual-memory.html
* _page_: chunk of virtual memory
* _page table_: map of page to physical address
* every process has its own 📙 Evans linux [16]
* _page fault_: attempt to read data from memory but instead forced to go to disk 📙 Evans linux [24]
* _swap area_: park of disk used as virtual memory https://serverfault.com/a/48487

---

bits
* _bit depth_: [Franz 38, 226] bounce (mv from one bit depth to another) [Franz 226] https://reverb.com/news/home-recording-basics-ii-choosing-your-first-audio-interface-and-daw https://www.youtube.com/watch?v=JTtSihQ8QX0 2:45
* _word_: data unit used by architecture, aka digital word [Franz 38] registers and memory are word-sized e.g. 32-bit (90s, x86) 64-bit (00s, ARM64) https://stackoverflow.com/a/9287273 https://www.youtube.com/watch?v=IknbgnJLSRY 1:05 Upton raspberry pi 149 people still use 32-bit on 64-bit https://gankra.github.io/blah/c-isnt-a-language/ https://news.ycombinator.com/item?id=30704642 byte, word https://jvns.ca/blog/2023/03/06/possible-reasons-8-bit-bytes/
> Yet, Python integers are interesting because they are not just 32-bit or 64-bit integers that CPUs work with natively. Python integers are arbitrary-precision integers, also known as bignums. This means that they can be as large as we want, and their sizes are only limited by the amount of available memory. https://tenthousandmeters.com/blog/python-behind-the-scenes-8-how-python-integers-work/
* _bit field_: access individual bits in order to save space i.e. instead of normal disregard for storage size of, say, an int, you go and fiddle with how int stored so it doesn't take up as much space as bits normally take in your language (32, 64, whatever) https://www.youtube.com/watch?v=aMAM5vL7wTs
* _bit mask_: pattern of bits that updates another pattern of bits https://www.youtube.com/watch?v=Ew2QnDeTCCE
* _endianness_: order of byte storage https://www.youtube.com/watch?v=OoHich9BPxg https://www.youtube.com/watch?v=NcaiHcBvDR4
* _big endian_: most significant byte at smallest memory address and vice versa https://perldoc.perl.org/perlglossary#big-endian
* _little endian_: least significant byte at smallest memory address https://corecursive.com/066-sqlite-with-richard-hipp/
* _endian_: put most significant bit first or last

* _mmap_: Linux program that maps disk to memory https://brunocalza.me/discovering-and-exploring-mmap-using-go/ 📙 `evans-linux.pdf` 24

* _ROM_: measured in megahertz
* _buffer overflow_: buffer writes to adjacent memory instead of intended location; useful to escalate privilege e.g. Morris worm
* _continguous_: buffer https://docs.python.org/3/glossary.html#term-contiguous

## processor

🔗 https://cpu.land/
📚
* Christian chapter 5
* Galvin chapter 6
* Tanenbaum chapter 8

---

speculative execution, branch prediction https://pythonspeed.com/articles/speeding-up-numba/

ALU
* _ALU_: executes on opcode [Manga 1.23] https://en.wikipedia.org/wiki/Arithmetic_logic_unit#Implementation
* _opcode_: operator and operand https://hacks.mozilla.org/2017/02/a-crash-course-in-assembly/ https://tech.marksblogg.com/faster-python.html
* _data path_: how much data moves around circuit e.g. computer data pathes generally 1 byte wide [Petzold 180]
* _cache_: caches RAM for processor, needs a few more cycles to read than registers https://www.reddit.com/r/compsci/comments/95ns21/what_is_difference_between_register_and_l1_cache/e3u4tlt e.g. L1 cache https://www.ardanlabs.com/blog/2023/07/getting-friendly-with-cpu-caches.html https://news.ycombinator.com/item?id=40365248
* _register_: internal to processor i.e. not memory https://stackoverflow.com/a/9287273 size can vary on data type held e.g. 80 bits for floating point https://lock.cmpxchg8b.com/zenbleed.html

ISA 📙 Bryant ch. 4 https://en.wikipedia.org/wiki/Instruction_set_architecture
* _ISA_: interface for processor 📙 Evans Linux 1, PG hackers and painters 179
* defines processor instructions, virtual memory, etc. https://en.wikipedia.org/wiki/Instruction_set_architecture
* _ARM64_: ARM for desktops
* _x86_: https://github.com/cirosantilli/x86-bare-metal-examples#china
📍 port in notes from 'memory'
* https://drewdevault.com/2021/03/19/A-new-systems-language.html
* ARM, RISC V https://riscv.org/ https://www.youtube.com/watch?v=Lo63uDIiCH0
* https://www.jeffgeerling.com/blog/2020/raspberry-pi-cluster-episode-4-minecraft-pi-hole-grafana-and-more
* https://www.jeffgeerling.com/blog/2020/what-does-apple-silicon-mean-raspberry-pi-and-arm64

scheduling 🗄 `linux.md` processes
* https://wizardzines.com/comics/cpu-scheduling/

* _processor_: aka CPU; can have n cores (i.e. parallelism) https://stackoverflow.com/q/19225859 can only add and subtract [Manga 1.15]
* _core_: main component that reads from memory, maintains execution order and state, and uses ALU to perform operations https://stackoverflow.com/a/19314303 https://testdriven.io/blog/developing-an-asynchronous-task-queue-in-python/
* _core types_: physical (what it sounds like) logical (abstraction to facilitate hyperthreading) https://stackoverflow.com/q/1715580 https://forums.tomshardware.com/threads/what-is-the-difference-between-physical-core-and-logical-core.1534416/
* _hyperthreading_: single core that can execute n instructions simultaneously
* _GPU_: https://news.ycombinator.com/item?id=23986925 https://lwn.net/Articles/827596/ https://codeconfessions.substack.com/p/gpu-computing https://codeconfessions.substack.com/p/gpu-computing
> GPUs are much less complex than CPUs; that means they can execute instructions much more quickly, but those instructions have to be much simpler. At the same time, you can run a lot of them at the same time to achieve outsized results. Graphics is, unsurprisingly, the most obvious example: every "shader" - the primary processing component of a GPU - calculates what will be displayed on a single portion of the screen; the size of the portion is a function of how many shaders you have available. If you have 1,024 shaders, each shader draws 1/1,024 of the screen. Ergo, if you have 2,048 shaders, you can draw the screen twice as fast. Graphics performance is "embarrassingly parallel", which is to say it scales with the number of processors you apply to the problem. https://stratechery.com/2023/china-chips-and-moores-law/
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
