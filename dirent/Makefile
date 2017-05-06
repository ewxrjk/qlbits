#
# Makefile for DIRENT routines
#
# 1/7/1993 Richard Kettlewell
#

LIB = flp1_lib_
DOCS = flp1_docs_
INCLUDE = flp1_include_

#

OBJECT = closedir_o opendir_o readdir_o rewinddir_o seekdir_o telldir_o

SOURCE = closedir_c opendir_c readdir_c rewinddir_c seekdir_c telldir_c test_c

HEADERS = dirent_h sys_dirent_h

MISC = dirent_txt readme_txt getdents_txt Makefile

#

libdir_a : $(OBJECT)
	cat -s $(OBJECT) >libdir_a

install : $(LIB)libdir_a $(DOCS)dirent_txt \
	$(INCLUDE)dirent_h $(INCLUDE)sys_dirent_h

test : install test_o
	$(LD) $(LDFLAGS) -o$@ test_o -ldir

$(LIB)libdir_a : libdir_a
	copy libdir_a $(LIB)libdir_a

$(DOCS)dirent_txt : dirent_txt
	copy dirent_txt $(DOCS)dirent_txt

$(INCLUDE)dirent_h : dirent_h
	copy dirent_h $(INCLUDE)dirent_h

$(INCLUDE)sys_dirent_h : sys_dirent_h
	copy sys_dirent_h $(INCLUDE)sys_dirent_h

#

$(OBJECT) : $(HEADERS)

#

clean :
	-$(RM) $(OBJECT)

archive : install
	zip -9u -b $(TMP) flp2_store_dirent $(SOURCE) $(HEADERS) $(MISC) libdir_a

arcmin :
	zip -9u -b $(TMP) flp2_store_dirent $(SOURCE) $(HEADERS) $(MISC) libdir_a

tidy : arcmin
	$(RM) $(SOURCE) $(HEADERS) $(MISC) libdir_a $(OBJECT)
