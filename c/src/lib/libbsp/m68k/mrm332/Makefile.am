ACLOCAL_AMFLAGS = -I ../../../../aclocal
EXTRA_DIST =

include $(top_srcdir)/../../../../automake/compile.am
include $(top_srcdir)/../../bsp.am

include_bspdir = $(includedir)/bsp

dist_project_lib_DATA = bsp_specs

include_HEADERS = include/bsp.h
include_HEADERS += include/tm27.h

nodist_include_HEADERS = include/bspopts.h
nodist_include_bsp_HEADERS = ../../shared/include/bootcard.h
DISTCLEANFILES = include/bspopts.h

include_HEADERS += include/mrm332.h

EXTRA_DIST += times

EXTRA_DIST += start/start.S
start.$(OBJEXT): start/start.S
	$(CPPASCOMPILE) -o $@ -c $<
project_lib_DATA = start.$(OBJEXT)

dist_project_lib_DATA += startup/linkcmds

noinst_LIBRARIES = libbsp.a
libbsp_a_SOURCES =

# startup
libbsp_a_SOURCES += startup/start_c.c \
    ../../shared/bspstart.c startup/bsppredriverhook.c \
    ../../shared/bootcard.c ../../shared/sbrk.c \
    ../../shared/getentropy-cpucounter.c \
    ../../shared/bspclean.c \
    ../../shared/setvec.c \
    ../../shared/bspgetworkarea.c ../../shared/gnatinstallhandler.c 
libbsp_a_SOURCES += ../../shared/bspreset.c
# clock
libbsp_a_SOURCES += clock/ckinit.c
# console
libbsp_a_SOURCES += console/console.c console/sci.c console/sci.h
# spurious
libbsp_a_SOURCES += spurious/spinit.c
# timer
libbsp_a_SOURCES += timer/timer.c

libbsp_a_LIBADD = \
    ../../../libcpu/@RTEMS_CPU@/shared/cache.rel \
    ../../../libcpu/@RTEMS_CPU@/shared/misc.rel

include $(srcdir)/preinstall.am
include $(top_srcdir)/../../../../automake/local.am
