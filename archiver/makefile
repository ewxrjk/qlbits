#
# Archiver makefile
#
# (c) 1992 Richard Kettlewell
#

cflags = -warn=6
lflags = -bufp150K

archive = arcio_o archive_o archuff_o arclzw_o arccrc_o arcmatch_o arcpack_o

Archive: $(archive)
	$(ld) $(lflags) -oArchive $(archive)

arccrc_o: arccrc_x
	cpp -P arccrc_x arccrc_s
	as68 arccrc_s arccrc_o
	del -l arccrc_s

crcgen: crcgen_o
	$(ld) $(lflags) -ocrcgen crcgen_o
