CC = gcc
LD = gcc
MODULES = Compute
OBJS = $(MODULES:%=%.o)
TESTS = $(MODULES:%=Test%.c)
TESTS_OBJS = $(MODULES:%=Test%.o)
LIBS = 
CCOPTS = -c -I/Users/arunshanmugamkumar/Documents/software/cut-2.4/include
DEBUG = 

# default target
help:
	echo "Type 'make application' to build the application."
	echo "Type 'make check' to build the application."

# top level target to create production application
application: $(OBJS) Main.o
	$(LD) $(LDOPTS) $(MODULES:%=%.o) Main.o $(LIBS) -o app

# top level target to run test cases
test: cutcheck
	./cutcheck

# top level target to clean up the project directory
clean:
	-rm *.o app cutcheck

cutcheck.c: $(TESTS)
	cutgen -o cutcheck.c $(TESTS)

cutcheck: $(OBJS) $(TESTS_OBJS) cutcheck.o
	$(LD) $(LDOPTS) $(OBJS) $(TESTS_OBJS) $(LIBS)\
		 cutcheck.o -o cutcheck

.c.o:
	$(CC) $(CCOPTS) $(DEBUG) -o $@ $<
