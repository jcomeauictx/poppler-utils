SHELL := /bin/bash
PREFIX ?= /usr/local/poppler
OPTIONS += -DCMAKE_INSTALL_PREFIX=$(PREFIX)
OPTIONS += -DCMAKE_BUILD_TYPE=debug
OPTIONS += -DENABLE_GPGME=OFF
OPTIONS += -DTESTDATADIR=$(PWD)/../poppler-test
OPTIONS += -DENABLE_QT6=OFF
OPTIONS += -DENABLE_BOOST=OFF
OPTIONS += -DENABLE_LIBOPENJPEG=unmaintained
OPTIONS += -DENABLE_LCMS=OFF
all: build/Makefile
	$(MAKE) -C $(<D)
build/Makefile: build
	cd $< && cmake .. $(OPTIONS)
build:
	mkdir build
install: build/bin/pdftotext
	cd $$(dirname ($$dirname $<)) && $(MAKE) install
