#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([Belfry Geometry Library],[1.0],[revarbat@gmail.com])
AM_INIT_AUTOMAKE([1.11.1 no-define foreign color-tests])
AC_CONFIG_SRCDIR([BGL.hh])
AC_CONFIG_HEADER([config.h])
AC_CONFIG_MACRO_DIR([m4])

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_INSTALL

# Libtool
LT_INIT

# Checks for libraries.

# Checks for header files.
AC_CHECK_HEADERS([sys/param.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_CONST
AC_C_INLINE
AC_TYPE_INT16_T
AC_TYPE_INT32_T
AC_TYPE_UINT16_T
AC_TYPE_UINT32_T
AC_TYPE_UINT8_T

# allow for a variety of compile CFLAGS to be passed to gcc
AS_IF([test ".$CFLAGS"="."], [ CFLAGS="" ])
AS_IF([test ".$CXXFLAGS"="."], [ CXXFLAGS="" ])
AC_ARG_WITH([warn],
    AS_HELP_STRING(--with-warn, use -Wall preproc flag),
    [CFLAGS="$CFLAGS -Wall" ; CXXFLAGS="$CXXFLAGS -Wall"])
AC_ARG_WITH([opt],
    AS_HELP_STRING(--with-opt=OPT, Specify optimization),
    [CFLAGS="$CFLAGS -${withval}" ; CXXFLAGS="$CXXFLAGS -${withval}"],
    [CFLAGS="$CFLAGS -O2" ; CXXFLAGS="$CXXFLAGS -O2"])
AC_ARG_WITH([gprof],
    AS_HELP_STRING(--with-gprof, use -pg preproc flag),
    [CFLAGS="$CFLAGS -pg" ; CXXFLAGS="$CXXFLAGS -pg"])


( cd tests && ./mklinks.sh )

# Checks for library functions.
AC_CHECK_FUNCS([floor strcasecmp strncasecmp])

AC_CONFIG_FILES([Makefile tests/Makefile])
AC_OUTPUT
