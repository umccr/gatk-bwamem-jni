ifeq ($(JAVA_HOME),)
$(error $$(JAVA_HOME) is not defined)
endif

JNI_INCLUDE_DIRS=$(addprefix -I,$(shell find $(JAVA_HOME)/include -type d))
CFLAGS=-ggdb -O2 -Wall -std=gnu99  -D_DEFAULT_SOURCE -fPIC $(JNI_INCLUDE_DIRS) -I simde-no-tests/
CC=gcc

#OS-dependent extension lookup
UNAME := $(shell uname)
ifeq ($(UNAME),Darwin)
LIB_EXT=Darwin.dylib
else
LIB_EXT=Linux.so
endif

JNI_BASE_NAME=org_umccr_java_hellbender_utils_bwa_BwaMemIndex

all: libbwa.$(LIB_EXT)

libbwa.$(LIB_EXT): $(JNI_BASE_NAME).o init.o jnibwa.o bwa/libbwa.a
	$(CC) -ggdb -dynamiclib -shared -o $@ $^ -lm -lz -lpthread

bwa:
	$(info "No patching anymore here")

bwa/libbwa.a: bwa
	$(MAKE) CFLAGS="$(CFLAGS)" -C bwa libbwa.a

$(JNI_BASE_NAME).o: $(JNI_BASE_NAME).c jnibwa.h bwa

jnibwa.o: jnibwa.c jnibwa.h init.h bwa

init.o: init.c init.h

clean:
	rm -rf *.o *.$(LIB_EXT)

.PHONY: all clean
