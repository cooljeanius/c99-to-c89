ACLOCAL_AMFLAGS = -I m4 --install

EXT =

all: c99conv$(EXT) c99wrap$(EXT)

OBJS = convert.o

CC_REQUIRED=/opt/local/bin/clang-mp-18
CC=@CC@
LD=$(CC)
AM_WARNFLAGS=-Wmissing-include-dirs @MAINT@ -Wc++-compat -Wwrite-strings
AM_CFLAGS=-I/opt/local/libexec/llvm-18/include -g $(AM_WARNFLAGS)
AM_LDFLAGS=-L/opt/local/libexec/llvm-18/lib -g
LIBS=-lclang
DISTCLEANFILES = *~ *.log

clean-local:
	rm -f c99conv$(EXT) c99wrap$(EXT) $(OBJS) compilewrap.o
	rm -f unit.c.c unit2.c.c

distclean-local:
	rm -rf autom4te.cache || rmdir autom4te.cache

test1: c99conv$(EXT)
	$(CC) -E unit.c -o unit.prev.c
	./c99conv unit.prev.c unit.post.c
	diff -u unit.{prev,post}.c || echo "$@: diff failed"

test2: c99conv$(EXT)
	$(CC) -E unit2.c -o unit2.prev.c
	./c99conv unit2.prev.c unit2.post.c
	diff -u unit2.{prev,post}.c || echo "$@: diff failed"

test3: c99conv$(EXT)
	$(CC) $(CFLAGS) $(AM_CFLAGS) -E -o convert.prev.c convert.c
	./c99conv convert.prev.c convert.post.c
	diff -u convert.{prev,post}.c

c99conv$(EXT): $(OBJS)
	$(CC) -o $@ $< $(AM_LDFLAGS) $(LDFLAGS) $(LIBS)

c99wrap$(EXT): compilewrap.o
	$(CC) -o $@ $< $(AM_LDFLAGS) $(LDFLAGS)

%.o: %.c
	$(CC) $(AM_CFLAGS) $(CFLAGS) -o $@ -c $<
