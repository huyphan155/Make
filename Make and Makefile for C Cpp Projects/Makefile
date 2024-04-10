## VARIABLE
# Note : only has 1 variable type is STRING

DEBUG_MODE = 1
INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

## CC : Program for compiling C++ program, default g++
## CXXFLAGS : Extra flags to give to the C++ compiler
## LDFLAGS : Extra flags to give to the linker


## over write default variable
CXX = g++
LDFLAGS = 

## New Variable
CXX_WARNING =  -Wall -Wextra -Wpedantic 
CXXFLAGS = $(CXX_WARNING)
## flag to tell the compiler where to include header file
CPPFLAGS = -I $(INCLUDE_DIR)

## CHOSE DEBUG MODE OR RELEASE MODE, 
## DEBUG_MODE Can change from cmd aggrument . Ex : make build DEBUB_MODE=0
ifeq ($(DEBUG_MODE),1)
CXXFLAGS += -g -O0
EXECUTE_NAME = mainDebug
else
CXXFLAGS += -O3
EXECUTE_NAME = mainRelease
endif 

COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

## OBJECT_LIST = main.o lib.o 
## OBJECT_LIST can aslo obtain this below 2 command : wildcard and patsubst
## wildcard : file all cpp file in folder src/
## patsubst : convert all .cpp file to .o in $(SOURCE_LIST)

SOURCE_LIST = $(wildcard $(SOURCE_DIR)/*.cpp)
OBJECT_LIST_WILDCARD = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(SOURCE_LIST))

folder:
	mkdir $(BUILD_DIR)

build: folder $(OBJECT_LIST_WILDCARD)
	$(COMPILER_CALL) $(OBJECT_LIST_WILDCARD) -o $(BUILD_DIR)/$(EXECUTE_NAME)

execute: 
	./$(BUILD_DIR)/$(EXECUTE_NAME).exe
	
clean:
	rm -f ./$(BUILD_DIR)/*.exe
	rm -f ./$(BUILD_DIR)/*.o
	rm -rf $(BUILD_DIR)


##PATTERNS
# $@ : the file name of the target
# $< : the name of the first dependency
# $^ : the names of all prerequisites

### Makefile format 
# target : dependency
# 	command 
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(COMPILER_CALL) -c $< -o $@
