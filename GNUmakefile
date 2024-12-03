SHELL := /bin/bash
PREFIX ?= /usr/local/poppler
OPTIONS += -DCMAKE_INSTALL_PREFIX=$(PREFIX)
OPTIONS += -DCMAKE_BUILD_TYPE=debug
all: build/Makefile
	$(MAKE) -C $(<D)
build/Makefile: build
	cd $< && cmake .. $(OPTIONS)
build:
	mkdir build
install: build/bin/pdftotext
	cd $$(dirname ($$dirname $<)) && $(MAKE) install
