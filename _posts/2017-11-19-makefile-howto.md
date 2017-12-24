---
layout: post
title:  "Makefile study"
date:   2017-11-19 15:50:00 +0900
category: gpp
---


### Macro

```
TARGET = run

$(TARGET) : main.o solution.o
    g++ -o $(TARGET) ...
```

### Macro substitution

```
SRCS = main.cpp solution.cpp
OBJS = $(SRCS: .cpp=.o) # main.o, solution.o

$(subst from, to, text) # text : hello world, from: hello, to: Hello, Hello world
$(wildcard src/*.cpp) # ./src/main.cpp, ./src/solution.cpp ....

$(patsubst pattern,replacement,text) # $(patsubst %.c,%.o,foo.c bar.c), -> foo.o bar.o

$(notdir forge/target.c name.c pms/fiya.mp3) # target.c name.c fiya.mp3



$@ is the name of the file to be made.

$? is the names of the changed dependents.

$< the name of the related file that caused the action.

$* the prefix shared by target and dependent files.
```
https://www.tutorialspoint.com/makefile/makefile_macros.htm
