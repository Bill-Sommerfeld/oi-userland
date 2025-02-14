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
# Copyright 2014 Alexander Pyhalov.  All rights reserved.
#

BUILD_BITS= 32_and_64
USE_DEFAULT_TEST_TRANSFORMS= yes
USE_COMMON_TEST_MASTER= no
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= gst-plugins-base
COMPONENT_VERSION= 0.10.36
COMPONENT_REVISION= 5
COMPONENT_SUMMARY= GNOME streaming media framework plugins
COMPONENT_SRC= $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_SRC).tar.bz2
COMPONENT_PROJECT_URL= https://gstreamer.freedesktop.org/
COMPONENT_ARCHIVE_URL= $(COMPONENT_PROJECT_URL)/src/$(COMPONENT_NAME)/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= sha256:2cd3b0fa8e9b595db8f514ef7c2bdbcd639a0d63d154c00f8c9b609321f49976
COMPONENT_FMRI= library/audio/gstreamer/plugin/base
COMPONENT_CLASSIFICATION= System/Multimedia Libraries
COMPONENT_LICENSE_FILE= gstreamer-plugin-base.license
COMPONENT_LICENSE= GPLv2, LGPLv2

include $(WS_MAKE_RULES)/common.mk

gcc_OPT= -O2

PATH= $(PATH.gnu)

CONFIGURE_OPTIONS += --sysconfdir=/etc
CONFIGURE_OPTIONS.32 += --libexecdir=/usr/lib
CONFIGURE_OPTIONS.64 += --libexecdir=/usr/lib/$(MACH64)
CONFIGURE_OPTIONS += --enable-external
CONFIGURE_OPTIONS += --enable-experimental
CONFIGURE_OPTIONS.32 += --enable-introspection=no
CONFIGURE_OPTIONS += --disable-alsa
CONFIGURE_OPTIONS += --with-default-audiosrc=autoaudiosrc
CONFIGURE_OPTIONS += --with-default-audiosink=autoaudiosink
CONFIGURE_OPTIONS += --with-default-videosink=autovideosink

# CFLAGS are not passed to compiler when g-ir-scanner is used
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS)"
COMPONENT_BUILD_ENV += CC="$(CC)"
COMPONENT_INSTALL_ENV += CFLAGS="$(CFLAGS)"
COMPONENT_INSTALL_ENV += CC="$(CC)"

# Build dependencies
REQUIRED_PACKAGES += library/desktop/gobject/gobject-introspection

# Auto-generated dependencies
REQUIRED_PACKAGES += codec/libtheora
REQUIRED_PACKAGES += library/audio/gstreamer
REQUIRED_PACKAGES += library/desktop/cairo
REQUIRED_PACKAGES += library/desktop/libvisual
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/gnome/gnome-vfs
REQUIRED_PACKAGES += library/libogg
REQUIRED_PACKAGES += library/libvorbis
REQUIRED_PACKAGES += library/libxml2
REQUIRED_PACKAGES += library/zlib
REQUIRED_PACKAGES += runtime/perl
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += system/library/orc
REQUIRED_PACKAGES += x11/library/libx11
REQUIRED_PACKAGES += x11/library/libxext
REQUIRED_PACKAGES += x11/library/libxv
