# Make/Make files - author : Huy Phan Quang

## Basic Make command

### Makefile Syntax

A Makefile consists of a set of rules. A rule generally looks like this:

```make
  targetName: Dependecies
    Command
```

Targets can be called by the ```make``` command.

```bash
  make targetName
```

### Pattent

- ```$@```: the file name of the target
- ```$<```: the name of the first dependency
- ```$^```: the names of all dependencies

```make
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cpp
	$(COMPILER_CALL) -c $< -o $@
```
With all .o file in (BUILD_DIR) folder . Find all corresponding .cpp file in (SOURCE_DIR)

```make
main.o: src/main.cpp
	$(COMPILER_CALL) -c src/main.cpp -o main.o

##....other file
```

- ```-c src/main.cpp```: compile src/main.cpp to object file ( c mean compile only)
- ```-o main.o```      : object file name is main.o


### *Wildcard
```*```: searches your filesystem for matching filenames.
```make
SOURCE_LIST = $(wildcard $(SOURCE_DIR)/*.cpp)
```
Find all cpp file in $(SOURCE_DIR) folder.

### Patsubst
```make
OBJECT_LIST_WILDCARD = $(patsubst $(SOURCE_DIR)/%.cpp, $(BUILD_DIR)/%.o, $(SOURCE_LIST))
```

Replace all .cpp file in (SOURCE_DIR) in (SOURCE_LIST) to object file in (BUILD_DIR)

## Addtional Topics

### CPPFLAGS = -I $(INCLUDE_DIR)

Flag to tell the compiler where to include header file.

### See default value of var in make file
```make
make -p
```
### Conditions

- Check if a variable is empty
  - ifeq ($(strip $(VAR)),)
- Check if a variable is defined
  - ifdef VAR
