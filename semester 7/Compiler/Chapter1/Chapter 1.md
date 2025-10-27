# 1 Compiler Design

A compiler translates high-level programs to machine code. It combines language theory, machine architecture, algorithms, and software engineering to produce correct, efficient executables.

## 1.1 Language Processors
- Compiler: converts source → target, detects syntax/semantic errors.  
- Interpreter: executes source directly (line-by-line), easier debugging, slower.  
- Hybrid (e.g., Java): compile to bytecode → JVM interprets or JITs.  
- Tool chain: Preprocessor → Compiler → Assembler → Linker → Loader.  
- Performance: compiled → faster; interpreted → better diagnostics.

## 1.2 Compiler Structure & Phases
- Two parts: Front End (analysis: lexical, syntax, semantic, IR, symbol table) and Back End (synthesis: optimization, code gen).
- Main phases:
  1. Lexical analysis — characters → lexemes → tokens; ignores whitespace/comments; uses symbol table (e.g., position = initial + rate * 60 → ⟨id,1⟩ ⟨=⟩ ...).  
  2. Syntax analysis — CFGs; builds parse/syntax tree; detects syntax errors.  
  3. Semantic analysis — type/scope checks; inserts conversions (e.g., inttofloat).  
  4. Intermediate code generation — three-address code (TAC) to ease optimization (e.g., t1=inttofloat(60) ...).  
  5. Code optimization — removes redundancies, constant folding, reuse temporaries.  
  6. Code generation — map IR → machine code (register allocation, instructions).  
  7. Symbol table management — stores name, type, scope, address, value; shared across phases.
- Phases grouping (passes) enables modular designs (example: Pass1: analysis+IR, Pass2: opt, Pass3: codegen).
- Tools: parser/scanner generators, syntax-directed translators, code-generator generators, data-flow analyzers, toolkits.  
- Diagrams: phases and translation images (media/phases_of_compiler.png, media/translation_of_assignment_statement.png).

## 1.3 Evolution of Languages & Paradigms
- History: assembly (1950s) → macros → high-level languages (Fortran, COBOL, Lisp) → many modern languages.  
- Generations: 1G machine, 2G assembly, 3G high-level, 4G domain-specific, 5G logic/constraint.  
- Paradigms: imperative, declarative, von Neumann, object-oriented, scripting.  
- Impact: language features and hardware advances drive compiler algorithms and representations.

### 1.3.2 Impacts on Compilers — Key Points
- Advances in languages affect compiler design.  
- Compilers must exploit hardware features (pipelining, caches, parallelism).  
- Compilers are complex, often support multiple sources/targets, and use heuristics since optimal generation is undecidable.  
- Compilers evaluate hardware designs and are crucial for performance.

## 1.4 Science of Building a Compiler
- Uses mathematical models and algorithms (finite automata, CFGs, trees).  
- Goals: accept all valid programs, preserve semantics, validate empirically.

## 1.5 Applications of Compiler Technology
- Implementing high-level languages: optimize abstractions to recover performance (examples: register keyword history; Java optimizations such as eliminating checks, stack-allocation, GC reduction; dynamic compilation).
- Optimizations for architectures:
  - Parallelism: ILP, VLIW, automatic or explicit parallelization.  
  - Memory hierarchies: optimize data layout, instruction ordering, cache-aware code.
- Architecture design: compilers are developed alongside processors (RISC vs CISC, specialized architectures).  
- Program translations beyond source→machine:
  - Binary translation (e.g., Transmeta), hardware synthesis (Verilog/VHDL → RTL → gates), database query compilation (SQL), compiled simulation (faster simulation code).
- Software productivity tools: data-flow analysis and type/bounds checking, memory tools (garbage collection, dynamic/static analysis) to find bugs and improve reliability.

## 1.6 Programming Language Basics — Key Concepts
- Static vs Dynamic policies: compile-time vs run-time decisions (e.g., static/lexical scope vs dynamic scope).
- Environments and states: environment maps names → locations; state maps locations → values.
- Block structure and static scope: nested blocks, nearest declaration rule; procedures as units (functions/methods).
- Access control: public/private/protected, class scopes, C++ separation of definitions/bodies.
- Dynamic scope examples: macros, runtime method selection (polymorphism).
- Parameter passing: call-by-value, call-by-reference, call-by-name (historical).  
- Aliasing: multiple names for same location affects optimizations and correctness (e.g., passing same array twice).

## Compact Examples (kept for clarity)
- Parse tree ASCII for a = id2 + id3 * 60
- TAC:
  t1 = inttofloat(60)
  t2 = id3 * t1
  t3 = id2 + t2
  id1 = t3
- Optimized:
  t1 = id3 * 60.0
  id1 = id2 + t1
- Machine code excerpt:
  LDF R2, id3
  MULF R2, R2, #60.0
  LDF R1, id2
  ADDF R1, R1, R2
  STF id1, R1

(Also refer to images: media/phases_of_compiler.png, media/memory_hierarchies.png, media/comparison_diagram_between_CISC_and_RISC_architectures.png)


