.PHONY: all clean

SRC := $(wildcard *.cc)
OBJ := $(patsubst %.cc,%.o,${SRC})
TARGET := $(patsubst %.cc, %, $(filter %_unittest.cc,${SRC}))

CXXFLAGS += -Wall -g
LDFLAGS += -pthread

all: ${TARGET}

${TARGET}: %_unittest: %_unittest.o
	${CXX} ${CXXFLAGS} -o $@ $^ -Wl,--start-group ${LDFLAGS} -Wl,--end-group

sample1_unittest: sample1.o
sample2_unittest: sample2.o
sample4_unittest: sample4.o
sample5_unittest: sample1.o

${OBJ}: %.o: %.cc
	${CXX} ${CXXFLAGS} -c -o $@ $<

clean:
	${RM} ${OBJ} ${TARGET}

NEED_GTEST_WITH_MAIN := 1
include /usr/local/gtest/Makefile.env
