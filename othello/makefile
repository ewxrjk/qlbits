#
# Othello
#
# (c) 1992 Richard Kettlewell
#

cflags = -Qnowarn

object = main_o display_o move_o brain_o

Othello: $(object)
	$(ld) $(lflags) $(object) -oOthello

clean:
	$(rm) $(rflags) *_o *_i *_s
