#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2015 Alexander Pyhalov
#

BUILD_STYLE=configure
BUILD_BITS=32
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         util-macros
COMPONENT_VERSION=      1.19.3
COMPONENT_FMRI=         developer/build/autoconf/xorg-macros
COMPONENT_SUMMARY=      GNU autoconf macros for X.Org software packages
COMPONENT_PROJECT_URL=  https://x.org
COMPONENT_CLASSIFICATION=Development/X11
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH= \
	sha256:624bb6c3a4613d18114a7e3849a3d70f2d7af9dc6eabeaba98060d87e3aef35b
COMPONENT_ARCHIVE_URL=  \
	http://ftp.x.org/pub/individual/util/$(COMPONENT_ARCHIVE)
COMPONENT_LICENSE=      MIT License
COMPONENT_LICENSE_FILE= xorg-macros.license

include $(WS_MAKE_RULES)/common.mk

COMPONENT_PREP_ACTION =        ( cd $(@D)  && autoreconf -f )

CONFIGURE_OPTIONS += --sysconfdir=/etc


