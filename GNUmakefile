SHELL := /bin/bash
PREFIX ?= /usr/local/poppler
OPTIONS += -DCMAKE_INSTALL_PREFIX=$(PREFIX)
OPTIONS += -DCMAKE_BUILD_TYPE=debug
OPTIONS += -DENABLE_GPGME=OFF
OPTIONS += -DTESTDATADIR=$(PWD)/../poppler-test
#OPTIONS += -DENABLE_QT6=OFF
#OPTIONS += -DENABLE_BOOST=OFF
OPTIONS += -DENABLE_LIBOPENJPEG=unmaintained
OPTIONS += -DENABLE_LCMS=OFF
BUILD := build
UTILS := $(BUILD)/utils
TARGET := $(UTILS)/pdftotext

all: $(TARGET)
$(TARGET): $(BUILD)/Makefile
	$(MAKE) -C $(<D)
$(BUILD)/Makefile: $(BUILD)
	cd $< && cmake .. $(OPTIONS)
$(BUILD):
	mkdir $<
%.writeaccess:
	[ -w $* ] || (echo 'Cannot write to $*; try sudo?' >&2; false)
$(PREFIX): $(dir $(PREFIX)).writeaccess
	mkdir -p $@
install: $(PREFIX) /etc/ld.so.cache.writeaccess | $(TARGET)
	cd $(BUILD) && $(MAKE) install
	ldconfig $(PREFIX)/lib
push:
	git push origin master
	git push github master
	git push githost master
%:
	cd $(BUILD) && $(MAKE) $*
