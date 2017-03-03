.PHONY: default help object executable all clean
CXX = g++
CC = gcc
LD = $(CC)

SOURCE_CXX = $(wildcard *.cpp)
OBJECTS_CXX = $(patsubst %.cpp, %_cpp.o, $(SOURCE_CXX))
SOURCE_C = $(wildcard *.c)
OBJECTS_C = $(patsubst %.c, %_c.o, $(SOURCE_C))

EXECUTABLE = c-main.e

default: help

help:
	@echo "\
Options:\n\n\
  make objects:       compiler makes objects for every *.c and *.f90\n\
  make executable:    compiler makes executable\n\
  make all:           build all previous\n\
  make clean:         delete output files\n\
  make help:          display this help"

objects: $(OBJECTS_F) $(OBJECTS_C)

executable: $(EXECUTABLE)

all: objects executable

%_c.o: %.c
	$(CC) -c $^ -o $@

%_cpp.o: %.cpp
	$(CXX) -c $^ -o $@

%.e: $(OBJECTS_C) $(OBJECTS_CXX)
	$(LD) $^ -o $@

clean:
	rm -rfv $(OBJECTS_C) $(OBJECTS_CXX) $(EXECUTABLE)
