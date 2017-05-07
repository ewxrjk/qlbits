/*
 * MAKE
 * 
 * (c) 1992 Richard Kettlewell
 *
 * Adjust configuraton section below and do
 *
 *	make install
 *
 * to install program and documentation. If you don't have a make which
 * can hack this Makefile, you'll have to rewrite it or do it by hand.
 */

/*
 * Configuration
 */

UTILS = flp1_				// where to install MAKE
DOCS = flp1_docs_			// where to put manual
LANGUAGE = english			// language to use for messages

/*
 * Source macros
 */

SOURCE = make_c macros_c main_c templates_c io_c targets_c\
	analyse_c globals_c english_c system_c memory_c

HEADERS = make_h types_h debug_h

MISC = make copying_txt make_txt history_txt Makefile env_bin environ_doc

/*
 * Object macros
 */

MAKEOB = make_o macros_o main_o templates_o io_o targets_o\
	analyse_o globals_o memory_o

OBJECT = $(MAKEOB) system_o $(LANGUAGE)_o

/*
 * Principal targets
 */

make: $(OBJECT)
	$(LD) $(LDFLAGS) -omake $(OBJECT)

install : $(UTILS)make $(DOCS)make_txt

$(UTILS)make: make
	copy make $(UTILS)make

$(DOCS)make_txt : make_txt
	copy make_txt $(DOCS)make_txt

/*
 * Clean-up targets
 *
 * NB do
 *
 *	make install tidy
 *
 * rather than
 *
 *	make tidy install
 *
 * as the latter will not work!
 */

clean:
	$(RM) $(RFLAGS) $(OBJECT)

archive: make
	zip -u -b ram1_tmp_ flp2_store_make $(SOURCE) $(HEADERS) $(MISC)

tidy: archive
	$(RM) $(RFLAGS) $(SOURCE) $(HEADERS) $(MISC) $(OBJECT)

/*
 * Header dependencies
 */

$(MAKEOB) : types_h debug_h		// change a type and variables change size
					// debug stuff changes everything to

main_o globals_o : make_h		// other changes affect only these
