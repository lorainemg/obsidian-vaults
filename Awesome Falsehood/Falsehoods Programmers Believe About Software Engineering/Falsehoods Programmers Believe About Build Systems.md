# Falsehoods Programmers Believe About Build Systems
Creado: 2022-06-21 18:00
Tags: #every-programmer-should-know, #falsehoods, #software-engineering
Topic: [[Falsehoods Programmers Believe About Software Engineering]]

----

- Build graphs are trees.
- Build graphs are acyclic.
- Every build step updates at most one file.
- Every build step updates at least one file.
- Compilers will always modify the timestamps on every file they are expected to output.
- It's possible to tell the compiler which file to write its output to.
- It's possible to tell the compiler which directory to write its output to.
- It's possible to predict in advance which files the compiler will update.
- It's possible to narrow down the set of possibly-updated files to a small hand-enumerated set.
- It's possible to determine the dependencies of a target without building it.
- Targets do not depend on the rules used to build them.
- Targets depend on every rule in the whole build system.
- Detecting changes via file hashes is always the right thing.
- Detecting changes via file hashes is never the right thing.
- Nobody will ever want to rebuild a subset of the available dirty targets.
- People will only want to build software on Linux.
- People will only want to build software on a Unix derivative.
- Nobody will want to build software on Windows.
- People will only want to build software on Windows.
  (Thanks to David MacIver for spotting this omission.)
- Nobody will want to build on a system without `strace` or some equivalent.
- `stat` is slow on modern filesystems.
- Non-experts can reliably write portable shell script.
- Your build tool is a great opportunity to invent a whole new language.
- Said language does not need to be a full-featured programming language.
- In particular, said language does not need a module system more sophisticated than `#include`.
- Said language should be based on textual expansion.
- Adding an Nth layer of textual expansion will fix the problems of the preceding N-1 layers.
- Single-character magic variables are a good idea in a language that most programmers will rarely use.
- System libraries and globally-installed tools never change.
- Version numbers of system libraries and globally-installed tools only ever increase.
- It's totally OK to spend over four hours calculating how much of a 25-minute build you should do.
- All the code you will ever need to compile is written in precisely one language.
- Everything lives in a single repository.
- Files only ever get updated with timestamps by a single machine.
- Version control systems will always update the timestamp on a file.
- Version control systems will never update the timestamp on a file.
- Version control systems will never change the time to one earlier than the previous timestamp.
- Programmers don't want a system for writing build scripts; they want a system for writing systems that write build scripts.

## Referencias