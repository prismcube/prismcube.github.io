#!/usr/bin/make -f
# 
# Version 1.1
# Copyright(c) 2013 Prismcuge Project Team. (kos <oskwon@marusys.com>)
#

# Target platform:
# elmo
#
# This only sets the default value. All platforms now use a shared build directory.
# Run "TARGET=elmo make" to build an image for the elmo, if it is not the default.
# 
TARGET?=elmo

SILENT?=@
SUPPORT=elmo
BRANCH?=angstrom-v2012.12-yocto1.3
REPOSITORY?=git://github.com/prismcube/setup-script.git

RM=rm -Rf
GIT=git
TOPDIR=$(PWD)
ECHO=$(SILENT)echo
BUILDSCRIPT?=./oeruby.sh

.PHONY=all clean clone build update help

all: clone build

clone:
	$(ECHO) '[*] Cloning Base Repositories...'
	$(SILENT)$(GIT) clone $(REPOSITORY)
	$(SILENT)cd $(TOPDIR)/setup-script && \
		$(GIT) checkout -b $(BRANCH) remotes/origin/$(BRANCH) && \
		$(BUILDSCRIPT) config $(TARGET) 

build:
	$(ECHO) '[*] Building Image for $(TARGET)'
	$(SILENT)cd $(TOPDIR)/setup-script && \
		$(BUILDSCRIPT) build $(TARGET) $(TARGET)-nand-image

update:
	$(ECHO) '[*] Updating SDK Repositories...'
	$(SILENT)cd $(TOPDIR)/setup-script && \
		$(BUILDSCRIPT) update

clean:
	$(ECHO) '[*] Deleting Build Directory...'
	$(SILENT)$(RM) $(TOPDIR)/setup-script

help:
	$(ECHO)
	$(ECHO) "Your Options:"
	$(ECHO) 
	$(ECHO)  "  * Update the SDK"
	$(ECHO)  "      $$ $(MAKE) update"
	$(ECHO) 
	$(ECHO)  "  * Build a firmware image for the selected target:"
	$(ECHO)  "      $$ $(MAKE)"
	$(ECHO) 
	$(ECHO)  "  * Build a firmware image for a different target:"
	$(ECHO)  "      $$ TARGET=elmo $(MAKE)"
	$(ECHO)  "    [Valid values: $(SUPPORT)]"
	$(ECHO) 
	$(ECHO)  "Your current settings:"
	$(ECHO)  "  TARGET = $(TARGET)"
	$(ECHO) 

