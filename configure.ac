AC_PREREQ([2.64])
AC_INIT([kalibrate], [0.4.1], [jl@thre.at], [kal])
AC_CONFIG_SRCDIR([src/fcch_detector.cc])
AM_INIT_AUTOMAKE([-Wall -Werror])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_LN_S
AC_PROG_RANLIB

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h string.h sys/time.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_INLINE

# Checks for library functions.
AC_FUNC_STRTOD
AC_CHECK_FUNCS([floor getpagesize memset sqrt strtoul strtol])

# Checks for libraries.
PKG_CHECK_MODULES(FFTW3, fftw3 >= 3.0)
AC_SUBST(FFTW3_LIBS)
AC_SUBST(FFTW3_CFLAGS)

PKG_CHECK_MODULES(UHD, uhd)
AC_SUBST(UHD_LIBS)
AC_SUBST(UHD_CFLAGS)

PKG_CHECK_EXISTS(uhd >= 003.004.000, uhd_3_4_x=yes, uhd_3_4_x=no)
if test "x$uhd_3_4_x" = "xyes"; then
	AC_DEFINE(UHD_3_4_X, 1, Define to 1 if you have UHD >= 003.004.000)
fi

# OSX doesn't support System V shared memory
AC_CANONICAL_HOST
case "$host_os" in
	darwin*)
		AC_DEFINE([D_HOST_OSX], [], [building for OSX])
		;;
esac

AC_CONFIG_FILES([Makefile
                 src/Makefile])
AC_OUTPUT
