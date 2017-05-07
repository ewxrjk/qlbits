#
# Linker --- Makefile
#
# (c) 1993 Richard Kettlewell
#
# You may want to change the install targets so that xcc gets installed
# as cc; there's a comment indicating where this should be done.
# Currently, xcc doesn't get installed (it's slightly bigger than lnk.)
#

UTILS = flp1_
DOCS = flp1_docs_
LIB = flp1_lib_

#

#uncomment the following if you use LD to compile:
#(only necessary if LNK won't run on your system and you're debugging)
#LDFLAGS = -bufp100K

#

OBJECT = load_o output_o resolve_o sym_o globals_o list_o cmdexpand_o \
	readqdir_o cmdparams_o
SOURCE = load_c output_c resolve_c sym_c globals_c list_c cmdexpand_c \
	readqdir_c cmdparams_c main_c cc_c xcc_c ccmain_c \
	ccusage_c lnkmain_c lnkusage_c cclnk_c config_asm lnk_h types_h \
	machine_h Makefile
LDOBJECT = main_o $(OBJECT)
XCCOBJECT = xcc_o $(OBJECT)
CCOBJECT = cc_o config_rel cmdexpand_o readqdir_o cmdparams_o
XOBJECT = main_o cc_o rtm_rel usedemo_rel demo_rel dem2_rel $(OBJECT)
MISC = sections_bas bugs_txt lnk_txt cc_txt history_txt readme_txt lnk cc xcc
RTM = insrtm_asm insrtm_rel rtm_asm rtm_rext rtm_txt ncrt_s ncrt_o
DEMO = demo_asm libdemo libdemo_rtm dem2_asm libdem2 libdem2_rtm usedemo_asm \
	usedemo

#

all : lnk xcc cc

lnk : $(LDOBJECT)
	$(LD) $(LDFLAGS) -o$@ $< -lm

xcc : $(XCCOBJECT)
	$(LD) $(LDFLAGS) -o$@ $< -lm

cc : $(CCOBJECT)
	$(LD) $(LDFLAGS) -o$@ $< -lm

cc_o : main_c ccmain_c ccusage_c cclnk_c

xcc_o : main_c ccmain_c ccusage_c lnkmain_c

main_o : lnkmain_c lnkusage_c

$(OBJECT) cc_o xcc_o : types_h

install : $(UTILS)cc $(UTILS)lnk $(DOCS)lnk_txt $(DOCS)cc_txt

#

#
# The following targets use LNK explicitly because LD simply can't
# do the required tricks (yet...)
#
# -v : verbose
# -x : generate _rtm file
# -z : non-executable output
# -s : set startup file
#
MAKERTM = -vxz -s insrtm_rel

rtm_rext : rtm_rel
	lnk $(LDFLAGS) -zvN $< -o $@

libdemo : demo_rel
	lnk $(LDFLAGS) $(MAKERTM) $< -o $@

libdemo : insrtm_rel

libdemo - libdemo_rtm

libdem2 : dem2_rel
	lnk $(LDFLAGS) $(MAKERTM) $< -o $@

libdem2 : insrtm_rel

libdem2 - libdem2_rtm

#
# -N --- don't include crt_o, libc_a, libc_rtm
#

usedemo : usedemo_rel
	lnk $(LDFLAGS) -v -N $< -o $@ -rdemo -rdem2

#

$(UTILS)lnk : lnk
	copy lnk $(UTILS)lnk 

$(UTILS)cc : cc
	copy cc $(UTILS)cc 

# to install xcc as cc, comment out the above target and uncomment this one:
#
#$(UTILS)cc : xcc
#	copy xcc $(UTILS)cc

$(DOCS)lnk_txt : lnk_txt
	copy lnk_txt $(DOCS)lnk_txt 

$(DOCS)cc_txt : cc_txt
	copy cc_txt $(DOCS)cc_txt 

#

clean:
	$(RM) $(XOBJECT)

archive : xcc cc lnk rtm_rext insrtm_rel usedemo libdemo libdem2 ncrt_o
	zip -u flp2_store_lnk $(SOURCE) $(MISC) $(RTM) $(DEMO)

tidy : archive
	$(RM) $(XOBJECT) $(SOURCE) $(MISC) $(RTM) $(DEMO)
	
