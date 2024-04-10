## VARIABLE
# Note : only has 1 variable type is STRING

DEBUG_MODE = 1
EXECUTE_NAME = main 

## CC : Program for compiling C++ program, default g++
## CXXFLAGS : Extra flags to give to the C++ compiler
## LDFLAGS : Extra flags to give to the linker


## over write default variable
CXX = g++
LDFLAGS = 

## New Variable
CXX_WARNING =  -Wall -Wextra -Wpedantic 
CXXFLAGS = $(CXX_WARNING)

## CHOSE DEBUG MODE OR RELEASE MODE, 
## DEBUG_MODE Can change from cmd aggrument . Ex : make build DEBUB_MODE=0
ifeq ($(DEBUG_MODE),1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif 

COMPILER_CALL = $(CXX) $(CXXFLAGS)

OBJECT_LIST = main.o lib.o

build: $(OBJECT_LIST)
	$(COMPILER_CALL) $(OBJECT_LIST) -o $(EXECUTE_NAME)

execute: 
	.\main.exe
	
clean:
	rm -f *.exe
	rm -f *.o


##PATTERNS
# $@ : the file name of the target
# $< : the name of the first dependency
# $^ : the names of all prerequisites

### Makefile format 
# target : dependency
# 	command 
%.o: src/%.cpp
	$(COMPILER_CALL) -c $< -o $@
