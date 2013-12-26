INCLUDES = -I$(top_srcdir)/include
bin_PROGRAMS = sipcalc
sipcalc_SOURCES = sub-func.c interface.c sub-output.c sub.c

sub-func.o: sub-func.c ../include/sub.h ../include/sub-o.h
interface.o: interface.c ../include/sub.h
sub-output.o: sub-output.c ../include/sub.h
sub.o: sub.c ../include/sub.h ../include/sub-o.h

