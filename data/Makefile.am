SUBDIRS=theme

schemadir = @GCONF_SCHEMA_FILE_DIR@
schema_in_files = meego-panel-applications.schemas.in
schema_DATA = $(schema_in_files:.schemas.in=.schemas)

@INTLTOOL_SCHEMAS_RULE@

if GCONF_SCHEMAS_INSTALL
install-data-local:
	GCONF_CONFIG_SOURCE=$(GCONF_SCHEMA_CONFIG_SOURCE) $(GCONFTOOL) --makefile-install-rule $(schema_DATA)
else
install-data-local:
endif

@INTLTOOL_DESKTOP_RULE@

desktopfiles_in_files=meego-panel-applications.desktop.in
desktopfiles_files=$(desktopfiles_in_files:.desktop.in=.desktop)

if ENABLE_MEEGO_DESKTOP_FILE
desktopfilesdir=$(MEEGO_PANELS_DIR)/
desktopfiles_DATA = $(desktopfiles_files)
endif

%.desktop.in: %.desktop.in.in Makefile
	$(AM_V_GEN)sed -e "s|\@libexecdir\@|$(libexecdir)|" $< > $@

EXTRA_DIST = meego-panel-applications.desktop.in.in $(schema_in_files)
CLEANFILES = meego-panel-applications.desktop meego-panel-applications.desktop.in $(schema_DATA)


























	
