# ACC
ACC compiler. Compiler for the Pep/9 Assembly Language. Supports C89 syntax and most features.

Compiler Structure Overview

A modern “compiler” is actually a combination of several source analysis tools which perform their own dedicated operations on source which, when combined, will produce a computer binary. These tools consist of a preprocessor, a lexical analyzer (lexer), a syntax analyzer (parser), a compiler, an assembler and a linker.
Since the Pep/9 simulator parses assembly code directly (it includes an assembler), I will not build an assembler nor linker.

Preprocessor
  - The preprocessor is a raw text substitution tool which does not operate on the code, per say, but instead on all of the non-code portions of a given source file
  The input of this file is the raw source file (*.c) and output is an intermediate, stripped source file containing code exclusively (*.ii)
  The preprocessor handles all preprocessor commands, which are used as a powerful tool in the maintenance of code.

  Issues special commands to the compiler, using a standardized method.
  The preprocessor will also strip the source file of any comments and remove remove unnecessary whitespace

Lexical analyzer
  - The lexical analyzer handles the source code and interprets any implicit statements, such as any case of operator overloading and make these statements explicit using standardized “tokens,” more or less some sort of system to make sure that there can be no confusion

Syntax analyzer
  - The syntax analyzer will generate handle the tokenized source code and check each statement against known grammers in order to determine validity. The syntax analyzer breaks down every statement to absolute core statements without any room for interpretation which are easily converted to assembly
  If the syntax analyzer can generate equal parse trees in any direction (forward and backward), the code syntax is valid and operation will continue.

Compiler
  - The compiler handles the output of the syntax analyzer, a very extended form of C code with broken down loops and absolute statements.
  The compiler simply converts each line to its assembly equivilent to produce the output assembly file, generally a (*.s) file, but in the case of Pep/9, a (*.pep) file.
