ALLINC = -I../libdie
ALLLIB = -L../libdie -ldie

DEPLIB = ../libdie/libdie.a

PROG = generate-bitmask-images
OBJS = generate-bitmask-images.o nanosvg.o nanosvgrast.o
SRCS = generate-bitmask-images.cc nanosvg.c nanosvgrast.c
JUNK =

OBJS2 = main.o asrlib.o
JUNK2 = main.s main.luac asrlib.s asrlib.luac

OPT=-O9

CC=gcc
CXX=g++
CFLAGS=-g -Wall ${OPT}

all: ${PROG}

.SUFFIXES: .cc .hh .o .a .ui .m.cc .m.o .y .lua .luac .s
.PRECIOUS: ${JUNK} ${JUNK2}

${PROG}: ${OBJS}  ${DEPLIB}
	${CXX} ${CFLAGS} ${OBJS} ${ALLINC} ${ALLLIB} -o ${PROG}

.cc.o:
	${CXX} -c ${CFLAGS} ${DEFS} ${ALLINC} $<

.c.o:
	${CC} -c ${CFLAGS} ${DEFS} ${ALLINC} $<

.y.c:
	bison -d -o $@ $<

.y.h:
	bison -d -o $@ $<

clean:
	rm -f ${OBJS} ${PROG}

distclean:
	rm -f ${OBJS} ${PROG}

###
generate-bitmask-images.o: nanosvg.h nanosvgrast.h
nanosvg.o: nanosvg.h
nanosvgrast.o: nanosvg.h nanosvgrast.h
