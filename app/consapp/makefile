#
# make all cui applications by gcc
#
#export CC = clang
export CC = gcc

BINDIR = /usr/local/bin
DIRS   = pos2kml str2str rnx2rtkp convbin rtkrcv

# Get number of parallel build jobs

ifneq ($(shell which nproc 2> /dev/null),)
  NJOBS = $(shell nproc)
else
  NJOBS = 1
endif

# Enable parallel make

PMAKE = make -j $(NJOBS)

all:
	@for i in $(DIRS); do $(PMAKE) -C $$i/gcc; done

install:
	@echo installing...
	@for i in $(DIRS); do cp $$i/gcc/$$i $(BINDIR); done

clean:
	@echo cleaning up...
	@for i in $(DIRS); do $(PMAKE) -C $$i/gcc clean; done