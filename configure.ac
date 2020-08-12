AC_INIT([systemd-optional-mount-generator],[1.0])
AC_DEFINE(VERSION_TITLE,["Release Title"],[Release Title])
AC_PREREQ([2.50])
AC_CONFIG_SRCDIR(config.h.in)
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR(.)

AM_INIT_AUTOMAKE()
AC_CONFIG_HEADERS(config.h)

AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_MAKE_SET
AM_PROG_CC_C_O
LT_INIT

AC_ARG_WITH([systemd-generatorsdir],
	[AS_HELP_STRING([--with-systemd-generatorsdir=<dir>],
		[specify systemd generators directory @<:@default=${libdir}/systemd/system-generators@:>@])],
	[if test x$with_systemd_generatorsdir = xyes; then
		AC_MSG_ERROR([--with-systemd-generatorsdir needs a directory PATH])
	 else
		generatorsdir=$with_systemd_generatorsdir
	 fi],
	[generatorsdir=${libdir}/systemd/system-generators])
AC_SUBST(generatorsdir)

dnl Checks for header files.
AC_HEADER_STDC

PKG_CHECK_MODULES(UUID, uuid)
AC_SUBST(UUID_CFLAGS)
AC_SUBST(UUID_LIBS)

PKG_CHECK_MODULES(BLKID, blkid)
AC_SUBST(BLKID_CFLAGS)
AC_SUBST(BLKID_LIBS)

AC_CHECK_HEADERS(iniparser/iniparser.h, [],
	[AC_CHECK_HEADERS(iniparser.h, [], [AC_MSG_ERROR([iniparser.h not found])])])
AC_CHECK_LIB(iniparser, iniparser_load, [], [AC_MSG_ERROR([iniparser library not found])], [])

AC_CONFIG_FILES([
	Makefile
])
AC_OUTPUT
