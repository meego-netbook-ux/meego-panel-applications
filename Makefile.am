
ACLOCAL_AMFLAGS = -I build

SUBDIRS = build src tests data po

EXTRA_DIST = \
	AUTHORS \
	autogen.sh \
	ChangeLog \
	COPYING \
	NEWS \
	README

dist-hook:
	prev=`$(top_srcdir)/build/git-log-extract-news.sh $(VERSION) 2>&1 > NEWS.new` && \
	`grep -A 1000000 '^$$prev' NEWS > NEWS.old` && \
	cat NEWS.old NEWS.new > NEWS && \
	rm -f NEWS.old NEWS.new

# Only need to re-create changelog after version bump.
ChangeLog: configure.ac
	@echo Creating ChangeLog ...
	$(top_srcdir)/build/gen-changelog.pl > $@

