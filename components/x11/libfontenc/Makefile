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
# Copyright 2016-2019 Aurelien Larcher
#

X11_CATEGORY=LIB
include ../../../make-rules/shared-macros.mk
include $(WS_MAKE_RULES)/x11.mk

COMPONENT_NAME=     libfontenc
COMPONENT_VERSION=  1.1.7
COMPONENT_FMRI=     x11/library/libfontenc
COMPONENT_SUMMARY=  libfontenc - font encoding table parser and mapping library
COMPONENT_ARCHIVE_EXTENSION= .tar.xz
COMPONENT_ARCHIVE_HASH= sha256:c0d36991faee06551ddbaf5d99266e97becdc05edfae87a833c3ff7bf73cfec2

include $(WS_MAKE_RULES)/common.mk

CONFIGURE_DEFAULT_DIRS=no
CONFIGURE_OPTIONS+= --disable-static
CONFIGURE_OPTIONS+= --enable-shared
CONFIGURE_OPTIONS+= --libdir=$(XORG_LIBDIR)

REQUIRED_PACKAGES += library/zlib
REQUIRED_PACKAGES += system/library
