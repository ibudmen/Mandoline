#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_INIT([Mandoline],[1.0],[revarbat@gmail.com])
AC_PREREQ([2.68])
AM_INIT_AUTOMAKE([1.11.1 no-define foreign])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_SRCDIR([Mandoline.cc])
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_INSTALL

# allow for a variety of compile CFLAGS to be passed to gcc
AS_IF([test ".$CFLAGS"="."], [ CFLAGS="" ])
AS_IF([test ".$CXXFLAGS"="."], [ CXXFLAGS="" ])
AC_ARG_WITH([warn],
    AS_HELP_STRING(--with-warn, use -Wall preproc flag),
    [CFLAGS="$CFLAGS -Wall"; CXXFLAGS="$CXXFLAGS -Wall"])
AC_ARG_WITH([opt],
    AS_HELP_STRING(--with-opt=OPT, Specify optimization),
    [CFLAGS="$CFLAGS -${withval}"; CXXFLAGS="$CXXFLAGS -${withval}"],
    [CFLAGS="$CFLAGS -O3"; CXXFLAGS="$CXXFLAGS -O3"])
AC_ARG_WITH([gprof],
    AS_HELP_STRING(--with-gprof, use -pg preproc flag),
    [CFLAGS="$CFLAGS -pg"; CXXFLAGS="$CXXFLAGS -pg"])

# libtool
LT_INIT

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([sys/time.h])
AC_CHECK_HEADERS([inttypes.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_CONST
AC_HEADER_TIME
AC_C_VOLATILE

# Checks for library functions.
AC_CHECK_FUNCS([gettimeofday])

AC_CHECK_DECLS([optreset],,, [[#include <getopt.h>]])

# Checks for pthreads
ACX_PTHREAD(,)
LIBS="$PTHREAD_LIBS $LIBS"
CFLAGS="$CFLAGS $PTHREAD_CFLAGS"
CXXFLAGS="$CXXFLAGS $PTHREAD_CFLAGS"

AC_CONFIG_FILES([Makefile])
AC_CONFIG_SUBDIRS([BGL])
AC_OUTPUT

