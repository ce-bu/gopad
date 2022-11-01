EXTRA_DIST = cmd go.mod go.sum m4 package scripts

gopad_sources = cmd/gopad/main.go
all_progs = $(abs_builddir)/gopad

all-local: $(all_progs)

GOBUILD = cd $(abs_srcdir) && $(GOCMD) build
GOGET = cd $(abs_srcdir) && $(GOCMD) get

$(abs_builddir)/gopad: $(gopad_sources) go.sum
	$(GOBUILD) -o $@ $(gopad_sources)

install-exec-local:
	@test -z "$(bindir)" || $(MKDIR_P) "$(DESTDIR)$(bindir)"
	@$(INSTALL_PROGRAM) gopad "$(DESTDIR)$(bindir)"

install-data-local:
	@test -z "$(sysconfdir)/systemd" || $(MKDIR_P) "$(DESTDIR)$(sysconfdir)/systemd/system"
	@test -z "$(datarootdir)/${PACKAGE_NAME}" || $(MKDIR_P) "$(DESTDIR)$(datarootdir)/${PACKAGE_NAME}"

uninstall-local:
	rm -f "$(DESTDIR)$(bindir)/gopad"

clean-local: 
	rm -f gopad

go.sum:
	$(GOGET) golang.org/x/net/netutil
