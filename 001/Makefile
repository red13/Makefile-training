CC=gcc
AR=ar cq
RANLIB=ranlib

OUTPUTDIR=output
TARGET=$(OUTPUTDIR)/libxxx.a

INCLUDES=-I. -Iout_inc -Iin_inc
DEFINES= $(INCLUDES) -DXXX
CFLAGS=-g $(DEFINES) -Wall -O2 -MMD

SRCS= $(wildcard src/aaa/*.c) $(wildcard src/bbb/*.c) $(wildcard src/ccc/*.c)

OBJDIRS= $(sort $(foreach file, $(dir $(SRCS)), $(OUTPUTDIR)/$(file)))
OBJS= $(foreach file, $(patsubst %.c,%.o,$(SRCS)), $(OUTPUTDIR)/$(file))
DEPENDS= $(OBJS:%.o=%.d)

$(OUTPUTDIR)/%.o:
	$(CC) $(CFLAGS) -o $(OUTPUTDIR)/$*.o -c $*.c


all: obj-dir $(TARGET)

obj-dir:
	-@mkdir -p $(OUTPUTDIR) $(OBJDIRS)

$(TARGET): $(OBJS)
	-@rm -f $@
	$(AR) $@ $(OBJS)
	$(RANLIB) $@

clean:
	-@rm -f $(TARGET)
	-@rm -fr $(OBJDIRS)

-include $(DEPENDS)
