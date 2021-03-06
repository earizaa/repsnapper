AC_PREREQ(2.63)
AC_INIT([repsnapper],[1.9.0],[https://github.com/timschmidt/repsnapper])

AC_CONFIG_HEADERS([config.h])
AC_CONFIG_SRCDIR([src/repsnapper.cpp])
AC_CONFIG_MACRO_DIR([m4])
dnl AC_CONFIG_AUX_DIR([config])

AM_INIT_AUTOMAKE([1.6 dist-bzip2 foreign])

m4_ifdef([AM_SILENT_RULES],[AM_SILENT_RULES([yes])])

# Checks for programs.
AC_PROG_CC
AC_PROG_CXX
# Needed for per-target cflags, like in gnomeshell-taskpanel
AM_PROG_CC_C_O

# Initialize libtool
LT_PREREQ([2.2.6])
LT_INIT([disable-static])

GETTEXT_PACKAGE=repsnapper
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE",
                   [The prefix for our gettext translation domains.])
IT_PROG_INTLTOOL(0.26)
AM_GLIB_GNU_GETTEXT

PKG_PROG_PKG_CONFIG([0.22])
PKG_CHECK_MODULES(GTKMM, [gobject-2.0 glib-2.0 gtkmm-2.4 gtkglext-1.0 gtk+-2.0])
AC_SUBST(GTKMM_CFLAGS)
AC_SUBST(GTKMM_LIBS)

dnl ------------------------------------------------------------------
dnl libreprap is (for now) built in from a copy in libraries/libreprap
dnl thus avoiding cmake, and user confusion.
dnl ------------------------------------------------------------------
dnl
dnl Look for libreprap, either in the system paths or in the path
dnl provided (defaults to --prefix)
dnl AC_ARG_WITH(libreprap,
dnl    AS_HELP_STRING([--with-libreprap],
dnl       [Extra prefix in which to look for libreprap. (default is $prefix)]),
dnl    [ LIBREPRAP_PREFIX="$withval" ], [ LIBREPRAP_PREFIX="$prefix" ])
dnl
dnl if test "x${LIBREPRAP_PREFIX}" != xNONE; then
dnl  xLIBREPRAP_CFLAGS="-I${LIBREPRAP_PREFIX}/include"
dnl  xLIBREPRAP_LIBS="-L${LIBREPRAP_PREFIX}/lib -lreprap"
dnl  DISTCHECK_LIBREPRAP_FLAGS="--with-libreprap=$LIBREPRAP_PREFIX"
dnl else
dnl  xLIBREPRAP_LIBS="-lreprap"
dnl fi
dnl
dnl OLD_CPPFLAGS="$CPPFLAGS"; CPPFLAGS="${xLIBREPRAP_CFLAGS} $CPPFLAGS"
dnl OLD_LIBS="$LIBS"; LIBS="${xLIBREPRAP_LIBS} $LIBS"
dnl AC_CHECK_HEADER(reprap/comms.h,
dnl     [LIBREPRAP_CFLAGS="${xLIBREPRAP_CFLAGS}"],
dnl     AC_MSG_ERROR([cannot find headers for libreprap]))
dnl dnl we require the 'meeks' branch of libreprap
dnl AC_CHECK_LIB(reprap, rr_dev_create,
dnl     [LIBREPRAP_LIBS="${xLIBREPRAP_LIBS}"],
dnl     AC_MSG_ERROR([cannot find binary for libreprap - check out the README]))
dnl CPPFLAGS="$OLD_CPPFLAGS"; LIBS="$OLD_LIBS"
dnl AC_SUBST(LIBREPRAP_CFLAGS)
dnl AC_SUBST(LIBREPRAP_LIBS)
dnl AC_SUBST(DISTCHECK_LIBREPRAP_FLAGS)

AC_CHECK_HEADER(GL/glut.h,
    ,
    AC_MSG_ERROR([cannot find headers for freeglut]))

AC_CONFIG_FILES([
  Makefile
  po/Makefile.in
  libraries/Makefile
  libraries/libreprap/Makefile
  libraries/polylib/Makefile
  libraries/vmmlib/Makefile
  libraries/vmmlib/include/Makefile
  libraries/vmmlib/include/vmmlib/Makefile
  src/Makefile])
AC_OUTPUT
