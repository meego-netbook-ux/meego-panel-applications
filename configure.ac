AC_PREREQ(2.53)
AC_INIT(meego-panel-applications, 0.2.8)
AC_CONFIG_AUX_DIR([build])
AC_CONFIG_MACRO_DIR([build])
AM_INIT_AUTOMAKE([1.10 foreign -Wno-portability no-define])
AM_CONFIG_HEADER(config.h)
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES])

AC_CANONICAL_HOST
IT_PROG_INTLTOOL([0.35.0])

GETTEXT_PACKAGE=meego-panel-applications
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED([GETTEXT_PACKAGE],
                   ["$GETTEXT_PACKAGE"],
                   [Gettext domain name])
AM_GLIB_GNU_GETTEXT

AC_PROG_CC
AC_PROG_CC_STDC
AC_PROG_INSTALL
AC_PROG_LIBTOOL
AC_ISC_POSIX
AC_HEADER_STDC
AM_PROG_CC_C_O

AS_ALL_LINGUAS

CFLAGS="$CFLAGS -Wall"

# control center capplet
AC_ARG_ENABLE([capplet],
              [AC_HELP_STRING([--enable-capplet=@<:@no/yes@:>@],
                              [Enable control center capplet default=no])],
              [],
              [enable_capplet=no])

AM_CONDITIONAL([ENABLE_CAPPLET], [test "x$enable_capplet" = "xyes"])

AS_IF([test "x$enable_capplet" = "xyes"],
       [PKG_CHECK_MODULES(CAPPLET,
                         gconf-2.0
                         gtk+-2.0 >= 2.14
                         mx-gtk-1.0
                         gmodule-export-2.0
                         libgnome-control-center-extension
                         clutter-gtk-0.12)
       EXTENSIONDIR=$($PKG_CONFIG libgnome-control-center-extension --variable=extensiondir)
       AC_SUBST(EXTENSIONDIR)],[])

AM_CONDITIONAL([ENABLE_CAPPLET], [test "x$enable_capplet" = "xyes"])

PKG_CHECK_MODULES(MPL, meego-panel >= 0.76.3)

MEEGO_PANELS_DIR=`$PKG_CONFIG --variable=meego_panel_panels_dir meego-panel`
AC_SUBST(MEEGO_PANELS_DIR)

AC_PATH_PROG(GCONFTOOL, gconftool-2, no)
if test x"$GCONFTOOL" = xno; then
	AC_MSG_ERROR([gconftool-2 not found])
fi

AM_GCONF_SOURCE_2

PKG_CHECK_MODULES(APPLICATIONS,
                  clutter-x11-1.0
                  gdk-x11-2.0
                  gio-unix-2.0
                  gtk+-2.0
                  libgnome-menu
                  mx-1.0 >= 1.4.0
                  gconf-2.0)

AC_ARG_ENABLE([cache],
              [AC_HELP_STRING([--enable-cache],
                              [Enable Mx image cache generation])],
              [],
              [enable_cache=no])

AS_IF([test "x$enable_cache" = "xyes"],
      [
      AC_CHECK_PROG([MX_CREATE_IMAGE_CACHE],
                [mx-create-image-cache],
                [$(which mx-create-image-cache)])
])

AM_CONDITIONAL([ENABLE_CACHE],   [test "x$enable_cache" = "xyes"])

AC_ARG_ENABLE([meego-desktop-file],
              [AC_HELP_STRING([--disable-meego-desktop-file],
                              [Disable installation of meego desktop file])],
              [enable_mdesktop=$enableval],
              [enable_mdesktop=yes])

AM_CONDITIONAL([ENABLE_MEEGO_DESKTOP_FILE], [test "x$enable_mdesktop" = "xyes"])

AC_OUTPUT([
        Makefile
        build/Makefile
        capplet/Makefile
        capplet/data/Makefile
        capplet/src/Makefile
        src/Makefile
        data/Makefile
        data/theme/Makefile
        tests/Makefile
        po/Makefile.in
])
