
# hamlibtcl, hamlibperl, etc. are temproray modules names
# They will be generated in separate subdirs in the future


#lib_LTLIBRARIES = @BINDING_LA@
#EXTRA_LTLIBRARIES = hamlibperl.la hamlibtcl.la
lib_LTLIBRARIES = hamlibperl.la hamlibtcl.la

INCLUDES =  @INCLUDES@ -Dbool=char -I/usr/lib/perl/5.6.1/CORE -I@TCL_SRC_DIR@/generic

# Perl binding
#hamlibperl_la_INCLUDES = @INCLUDES@ -Dbool=char -I/usr/lib/perl/5.6.1/CORE

hamlibperl_la_SOURCES = hamlibperl_wrap.c
hamlibperl_la_LDFLAGS = -no-undefined -module
hamlibperl_la_LIBADD = ../src/libhamlib.la

hamlibperl_wrap.c: hamlib.swg
	swig -perl5 -shadow @INCLUDES@ -o $@ $<


# Tcl binding
#hamlibtcl_la_INCLUDES = @INCLUDES@ -I@TCL_SRC_DIR@/generic

hamlibtcl_la_SOURCES = hamlibtcl_wrap.c
hamlibtcl_la_LDFLAGS = -no-undefined -module @TCL_LIB_SPEC@
hamlibtcl_la_LIBADD = ../src/libhamlib.la

hamlibtcl_wrap.c: hamlib.swg
	swig -tcl @INCLUDES@ -o $@ $<


rig.swg: ../include/hamlib/rig.h ../include/hamlib/riglist.h
rotator.swg: ../include/hamlib/rotator.h ../include/hamlib/rotlist.h

hamlib.swg: ignore.swg rig.swg rotator.swg

EXTRA_DIST = hamlib.swg ignore.swg rig.swg rotator.swg

CLEANFILES = hamlibperl_wrap.c hamlib.pm hamlibtcl_wrap.c