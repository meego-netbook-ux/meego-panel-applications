
@INTLTOOL_DESKTOP_RULE@

desktopfilesdir = $(datadir)/applications
desktopfiles_in_files = app-properties.desktop.in

desktopfiles_files = $(desktopfiles_in_files:.desktop.in=.desktop)
desktopfiles_DATA = $(desktopfiles_files)

CLEANFILES = $(desktopfiles_DATA)
EXTRA_DIST = $(desktopfiles_in_files)
