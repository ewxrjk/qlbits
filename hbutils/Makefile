#
# Hotkey & button utilities
#
# (c) 1993 Richard Kettlewell
#

OBJECT = main_rel hotdate_rel clock_rel time_rel free_rel cbut_rel button_rel thg_rel memview_rel getpos_rel data_rel load_rel

SOURCE = main_asm hotdate_asm clock_asm time_asm free_asm cbut_asm button_asm thg_asm memview_asm getpos_asm data_asm load_asm

MISC = hbutils_txt hbutils_rext string_mac Makefile

#

hbutils_rext : $(OBJECT)
	lnk -o$@ -zNms $< -lmc

#

clean :
	rm -f $(OBJECT) hbutils_rext_map

archive : hbutils_rext
	zip -u win1_src_store_hbutils $(SOURCE) $(MISC)

tidy : archive
	rm -f $(OBJECT) hbutils_rext_map $(SOURCE) $(MISC)
