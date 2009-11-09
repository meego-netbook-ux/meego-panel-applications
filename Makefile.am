
ACLOCAL_AMFLAGS = -I build

SUBDIRS = build src tests data po

EXTRA_DIST = \
	AUTHORS \
	autogen.sh \
	ChangeLog \
	COPYING \
	NEWS \
	README

# Only need to re-create changelog after version bump.
ChangeLog: configure.ac
	@echo Creating ChangeLog ...
	$(top_srcdir)/build/gen-changelog.pl > $@

