PROG=gauge
PROGS=$(PROG) $(PROG)-float $(PROG)-domino
INSTALL_DIR=/usr/local/bin

.PHONY: test
test: test/podman

.PHONY: test/podman
test/podman:
	@podman run --rm -v "$$PWD:/mnt:Z" koalaman/shellcheck:stable $(PROGS) \
	&& echo "All good!"

.PHONY: test/docker
test/docker:
	@docker run --rm -v "$$PWD:/mnt" koalaman/shellcheck:stable $(PROGS) \
	&& echo "All good!"

.PHONY: install
install: $(PROGS)
	@VERSION_CONTROL=numbered install --backup -vm 755 $(PROGS) $(INSTALL_DIR)

.PHONY: uninstall
uninstall:
	@for P in $(PROGS); do \
	  [ -f "$(INSTALL_DIR)/$$P" ] && rm -i "$(INSTALL_DIR)/$$P"; \
	done
