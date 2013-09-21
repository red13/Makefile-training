CC=gcc
AR=ar cq
RANLIB=ranlib

TARGET=libxxx.a

INCLUDES=-I. -Iout_inc -Iin_inc
DEFINES= $(INCLUDES) -DXXX
CFLAGS=-g $(DEFINES) -Wall -O2

SRCS= $(wildcard src/aaa/*.c) $(wildcard src/bbb/*.c) $(wildcard src/ccc/*.c)

OBJDIRS= $(foreach file, $(dir $(SRCS)), obj/$(file))
OBJS= $(foreach file, $(patsubst %.c,%.o,$(SRCS)), obj/$(file))

obj/%.o:
	$(CC) $(CFLAGS) -oobj/$*.o -c $*.c


all: obj-dir $(TARGET)

obj-dir:
	-@mkdir -p $(OBJDIRS)

$(TARGET): $(OBJS)
	-@rm -f $@
	$(AR) $@ $(OBJS)
	$(RANLIB) $@

clean:
	-@rm -f $(TARGET)
	-@rm -fr $(OBJDIRS)
