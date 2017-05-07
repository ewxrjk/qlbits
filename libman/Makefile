#
# Library utilities
#
# (c) 1993 Richard Kettlewell
#

UTILS = flp1_utils_

#

OBJECT = lsort_o lrep_o ltab_o lext_o
AOBJECT = lload_o opts_o
XOBJECT = $(OBJECT) $(AOBJECT)
SOURCE = lsort_c lrep_c lload_c ltab_c lext_c opts_c opts_h lib_h
PROGS = lsort lrep ltab lext
MISC = libman_txt Makefile

#

all : $(PROGS)

lsort : lsort_o $(AOBJECT)
	$(LD) $(LDFLAGS) -o$@ lsort_o $(AOBJECT)

lrep : lrep_o $(AOBJECT)
	$(LD) $(LDFLAGS) -o$@ lrep_o $(AOBJECT)

ltab : ltab_o $(AOBJECT)
	$(LD) $(LDFLAGS) -o$@ ltab_o $(AOBJECT)

lext : lext_o $(AOBJECT)
	$(LD) $(LDFLAGS) -o$@ lext_o $(AOBJECT)

#

$(OBJECT) : opts_h lib_h

lload_o : lib_h

opts_o : opts_h

#

install : $(UTILS)lsort $(UTILS)lrep $(UTILS)ltab $(UTILS)lext

$(UTILS)lsort : lsort
	copy lsort $(UTILS)lsort

$(UTILS)lrep : lrep
	copy lrep $(UTILS)lrep

$(UTILS)ltab : ltab
	copy ltab $(UTILS)ltab

$(UTILS)lext : lext
	copy lext $(UTILS)lext

#

clean :
	$(RM) $(XOBJECT)

archive : $(PROGS)
	zip -9u -b $(TMP) flp2_store_libman $(SOURCE) $(PROGS) $(MISC)

tidy : archive
	$(RM) $(XOBJECT) $(SOURCE) $(PROGS) $(MISC)

