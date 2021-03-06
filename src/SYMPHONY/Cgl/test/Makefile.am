# Copyright (C) 2006 International Business Machines and others.
# All Rights Reserved.
# This file is distributed under the Eclipse Public License.

## $Id: Makefile.am 1110 2013-04-06 13:19:05Z stefan $

# Author:  Andreas Waechter           IBM    2006-04-13

AUTOMAKE_OPTIONS = foreign

########################################################################
#                          unitTest for Cgl                            #
########################################################################

noinst_PROGRAMS = unitTest

unitTest_SOURCES = unitTest.cpp

# List libraries we need to link in
unitTest_LDADD = ../src/libCgl.la $(CGLLIB_LIBS)

unitTest_DEPENDENCIES = ../src/libCgl.la $(CGLLIB_DEPENDENCIES)

# Here list all include flags, relative to this "srcdir" directory.  This
# "cygpath" stuff is necessary to compile with native compilers on Windows
AM_CPPFLAGS = \
	-I`$(CYGPATH_W) $(srcdir)/../src` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglFlowCover` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglGomory` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglKnapsackCover` \
    -I`$(CYGPATH_W) $(srcdir)/../src/CglLandP` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglOddHole` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglProbing` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglMixedIntegerRounding` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglMixedIntegerRounding2` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglResidualCapacity` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglRedSplit` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglRedSplit2` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglTwomir` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglClique` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglSimpleRounding` \
	-I`$(CYGPATH_W) $(srcdir)/../src/CglZeroHalf` \
	$(CGLLIB_CFLAGS)
if COIN_HAS_SAMPLE
AM_CPPFLAGS += -DSAMPLEDIR=\"`$(CYGPATH_W) @SAMPLE_DATA@ | sed -e 's/\\\\/\\\\\\\\/g'`\"
endif

# This line is necessary to allow VPATH compilation
DEFAULT_INCLUDES = -I. -I`$(CYGPATH_W) $(srcdir)` -I$(top_builddir)/src

# Depending of what solvers are available, we add the corresponding files,
# libraries and include dirs
# For solvers not available, the variables should just resolve to an empty string,
# so it's no harm to list them all

AM_CPPFLAGS           += $(OSICLP_CFLAGS)       $(OSICPX_CFLAGS)       $(OSIDYLP_CFLAGS)       $(OSIGLPK_CFLAGS)       $(OSIMSK_CFLAGS)       $(OSIVOL_CFLAGS)       $(OSIXPR_CFLAGS)
unitTest_LDADD        += $(OSICLP_LIBS)         $(OSICPX_LIBS)         $(OSIDYLP_LIBS)         $(OSIGLPK_LIBS)         $(OSIMSK_LIBS)         $(OSIVOL_LIBS)         $(OSIXPR_LIBS)
unitTest_DEPENDENCIES += $(OSICLP_DEPENDENCIES) $(OSICPX_DEPENDENCIES) $(OSIDYLP_DEPENDENCIES) $(OSIGLPK_DEPENDENCIES) $(OSIMSK_DEPENDENCIES) $(OSIVOL_DEPENDENCIES) $(OSIXPR_DEPENDENCIES)

test: unitTest$(EXEEXT)
	./unitTest$(EXEEXT)

.PHONY: test

########################################################################
#                          Cleaning stuff                              #
########################################################################

# Here we list everything that is not generated by the compiler, e.g.,
# output files of a program

DISTCLEANFILES =
