ccmodulesdir = $(EXTENSIONDIR)
ccmodules_LTLIBRARIES = libapp.la

libapp_la_SOURCES = \
	app-module.c \
	app-cc-panel.h \
	app-cc-panel.c

libapp_la_LIBADD = $(CAPPLET_LIBS)
libapp_la_LDFLAGS = --avoid-version --module
libapp_la_CFLAGS = $(CAPPLET_CFLAGS) \
		   -DPLUGIN_LOCALEDIR=\"$(localedir)\" \
		   -Wall -Wmissing-declarations
