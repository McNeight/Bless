dist_noinst_DATA=bless-about.png bless-48x48.png bless.desktop.in \
		bless-default.layout bless-16-bytes-per-row.layout \
		bless-all-number-bases.layout help_script.tmpl.in \
		default-preferences.xml bless.glade

noinst_SCRIPTS=help_script.sh

CLEANFILES=help_script.sh.install help_script.sh

PWD=$(shell pwd)

help_script.sh: help_script.tmpl
	sed -e 's,@blessdocdir\@,$(PWD)/../doc,g' help_script.tmpl > help_script.sh
	chmod +x help_script.sh
	sed -e 's,@blessdocdir\@,$(datadir)/doc/$(PACKAGE_NAME),g' help_script.tmpl > help_script.sh.install

install-data-local:
	$(INSTALL) -d $(DESTDIR)$(datadir)/$(PACKAGE_NAME)
	$(INSTALL_DATA) bless-about.png	bless-48x48.png     \
			bless-default.layout 		    \
                        bless-16-bytes-per-row.layout	    \
			bless-all-number-bases.layout 	    \
	    		default-preferences.xml bless.glade \
	    		$(DESTDIR)$(datadir)/$(PACKAGE_NAME)
	$(INSTALL) -d $(DESTDIR)$(datadir)/applications
	$(INSTALL_DATA) bless.desktop $(DESTDIR)$(datadir)/applications
	$(INSTALL) -d $(DESTDIR)$(datadir)/pixmaps
	$(INSTALL_DATA) bless-48x48.png $(DESTDIR)$(datadir)/pixmaps
	$(INSTALL_SCRIPT) help_script.sh.install $(DESTDIR)$(datadir)/$(PACKAGE_NAME)/help_script.sh

uninstall-local:
	rm -rf $(DESTDIR)$(datadir)/$(PACKAGE_NAME)
	rm -f $(DESTDIR)$(datadir)/applications/bless.desktop
	rm -f $(DESTDIR)$(datadir)/pixmaps/bless-48x48.png
