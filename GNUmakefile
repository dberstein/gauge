GAUGE=gauge
GAUGE_FLOAT=$(GAUGE)-float
GAUGE_DOMINO=$(GAUGE)-domino
INSTALL_DIR=/usr/local/bin
INSTALL_GAUGE=$(INSTALL_DIR)/$(GAUGE)
INSTALL_GAUGE_FLOAT=$(INSTALL_DIR)/$(GAUGE_FLOAT)
INSTALL_GAUGE_DOMINO=$(INSTALL_DIR)/$(GAUGE_DOMINO)

.PHONY: test
test: test/podman
.PHONY: test/podman
test/podman:
	@podman run --rm -v "$$PWD:/mnt:Z" koalaman/shellcheck:stable $(GAUGE) $(GAUGE_FLOAT) $(GAUGE_DOMINO) \
	&& echo "All good!"
.PHONY: test/docker
test/docker:
	@docker run --rm -v "$$PWD:/mnt" koalaman/shellcheck:stable $(SHAFE) \
	&& echo "All good!"

install:
	@install -m 755 "$(GAUGE)" "$(INSTALL_DIR)"
	@install -m 755 "$(GAUGE_FLOAT)" "$(INSTALL_DIR)"
	@install -m 755 "$(GAUGE_DOMINO)" "$(INSTALL_DIR)"

uninstall:
	@if [ -f "$(INSTALL_GAUGE)" ]; then rm -i "$(INSTALL_GAUGE)"; else echo "file not found: $(INSTALL_GAUGE)"; fi
	@if [ -f "$(INSTALL_GAUGE_FLOAT)" ]; then rm -i "$(INSTALL_GAUGE_FLOAT)"; else echo "file not found: $(INSTALL_GAUGE_FLOAT)"; fi
	@if [ -f "$(INSTALL_GAUGE_DOMINO)" ]; then rm -i "$(INSTALL_GAUGE_DOMINO)"; else echo "file not found: $(INSTALL_GAUGE_DOMINO)"; fi
