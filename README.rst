====================
Read Lua Source Code
====================

Reading Lua_ code is fairly easy. `The language is simple`_,
`well documented`_, has a `official book`_, a `package manager`_
and plenty of resources online.

The thing is, there is not a lot of resources explaining
how to read the lua source code, which is a work of
art on its own and a great way to study low level
software design. This project attempts to put
together suggestions and material that might
help you read the lua source code in a timely
fashion.

The material available here is mostly the work and
suggestions of other people compiled in a single
place. Few free to point out if something is
mentioned without a source or send merge requests
with more material.

.. _official book: https://www.lua.org/docs.html#books
.. _The language is simple: https://devhints.io/lua
.. _well documented: https://www.lua.org/docs.html

------------------------
What Do You Need To Know
------------------------

The Lua source code is written in `ANSI C`_, a low level, statically
typed programming language very common as a base for
software that should live very close to the hardware.

So, the first thing you should learn is the C language. Below
there are some resources you could try these:

Online material
===============

- `learn-c`_
- `coursera c-programming`_
- `guru99 c-programming-tutorial`_
- `programiz c-programming`_
- `tutorialspoint c programming`_
- `ucam teaching C`_
- `ravi lua5.3 bytecode reference`_
- `ravi lua parsing and code generation`_

.. _ravi lua5.3 bytecode reference: https://the-ravi-programming-language.readthedocs.io/en/latest/lua_bytecode_reference.html
.. _ravi lua parsing and code generation: https://the-ravi-programming-language.readthedocs.io/en/latest/lua-parser.html

Books
=====

- "C Programming Absolute Beginner's Guide" by Greg Perry and Dean Mille
- "The C Programming Language" by Brain W.
- "The C Programming Language" by Kernighan
- "C Programming: A Modern Approach" by Taschenbuch

List compiled from guru99_.

.. _guru99: https://www.guru99.com

Articles
========

- `A No-Frills Introduction to Lua 5.1 VM Instructions`_
- `The Implementation of Lua 5.0`_

.. _The Implementation of Lua 5.0: https://www.researchgate.net/profile/Roberto_Ierusalimschy/publication/220349489_The_Implementation_of_Lua_50/links/02e7e52403a963d32c000000.pdf
.. _A No-Frills Introduction to Lua 5.1 VM Instructions: http://luaforge.net/docman/83/98/ANoFrillsIntroToLua51VMInstructions.pdf

--------------
Where To Start
--------------

Know where to start is very important, because you need to build the
knowledge in your mind to put all the pieces together. Mimemike
published a suggestion in `this reddit post`_ that I'll copy below:

- lmathlib.c, lstrlib.c: get familiar with the external C API. Don't bother with the pattern matcher though. Just the easy functions.
- lapi.c: Check how the API is implemented internally. Only skim this to get a feeling for the code. Cross-reference to lua.h and luaconf.h as needed.
- lobject.h: tagged values and object representation. skim through this first. you'll want to keep a window with this file open all the time.
- lstate.h: state objects. ditto.
- lopcodes.h: bytecode instruction format and opcode definitions. easy.
- lvm.c: scroll down to luaV_execute, the main interpreter loop. see how all of the instructions are implemented. skip the details for now. reread later.
- ldo.c: calls, stacks, exceptions, coroutines. tough read.
- lstring.c: string interning. cute, huh?
- ltable.c: hash tables and arrays. tricky code.
- ltm.c: metamethod handling, reread all of lvm.c now.
- You may want to reread lapi.c now.
- ldebug.c: surprise waiting for you. abstract interpretation is used to find object names for tracebacks. does bytecode verification, too.
- lparser.c, lcode.c: recursive descent parser, targetting a register-based VM. start from chunk() and work your way through. read the expression parser and the code generator parts last.
- lgc.c: incremental garbage collector. take your time.
- Read all the other files as you see references to them. Don't let your stack get too deep though.

Happy reading! Please, share your results and suggestions!

.. _ANSI C: https://en.wikipedia.org/wiki/C_(programming_language)
.. _coursera c-programming: https://coursera.org/specializations/c-programming
.. _guru99 c-programming-tutorial: https://www.guru99.com/c-programming-tutorial.html
.. _learn-c: https://www.learn-c.org/
.. _Lua: https://www.lua.org/
.. _package manager: https://luarocks.org/
.. _programiz c-programming: https://www.programiz.com/c-programming
.. _this reddit post: https://www.reddit.com/r/programming/comments/63hth/ask_reddit_which_oss_codebases_out_there_are_so/c02pxbp/
.. _tutorialspoint c programming: https://www.tutorialspoint.com/cprogramming/index.htm
.. _ucam teaching C: http://www-h.eng.cam.ac.uk/help/tpl/languages/C/teaching_C/teaching_C.html
