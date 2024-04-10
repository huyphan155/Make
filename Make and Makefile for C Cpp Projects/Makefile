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

build: main.o lib.o
	g++ main.o lib.o -o main

main.o:
	g++ src/main.cpp -c main.o

lib.o:
	g++ src/lib.cpp -c lib.o

execute: 
	.\main.exe
	
clean:
	rm -f *.exe
	rm -f *.o
