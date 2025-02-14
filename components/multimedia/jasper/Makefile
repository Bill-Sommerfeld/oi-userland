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
# Copyright 2023 Niklas Poslovski
#

BUILD_STYLE= cmake
USE_DEFAULT_TEST_TRANSFORMS= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= jasper
COMPONENT_VERSION= 4.2.0
COMPONENT_SUMMARY= A free software-based reference implementation of the JPEG-2000 Part-1 CODEC
COMPONENT_SRC= $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:69f0b08a0cc281a06eaf7feed510736854bbff9af89ab1d01b77382ad57ec957
COMPONENT_PROJECT_URL=	https://www.ece.uvic.ca/~frodo/jasper
COMPONENT_ARCHIVE_URL=	https://github.com/jasper-software/$(COMPONENT_NAME)/releases/download/version-$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI= codec/jasper
COMPONENT_CLASSIFICATION= System/Multimedia Libraries
COMPONENT_LICENSE= BSD-like
COMPONENT_LICENSE_FILE= LICENSE.txt

include $(WS_MAKE_RULES)/common.mk

# build with the distribution preferred libjpeg implementation
CFLAGS   += $(JPEG_CPPFLAGS) $(JPEG_CFLAGS)
CXXFLAGS += $(JPEG_CPPFLAGS) $(JPEG_CXXFLAGS)
LDFLAGS  += $(JPEG_LDFLAGS)

# jpeg-turbo is not detected without this.
CMAKE_OPTIONS += -DJPEG_LIBRARY=$(JPEG_LIBDIR)/libjpeg.so

unexport SHELLOPTS

COMPONENT_TEST_TRANSFORMS += '-e "/Output/p" '

# Auto-generated dependencies
REQUIRED_PACKAGES += $(JPEG_IMPLEM_PKG)
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += x11/library/freeglut
REQUIRED_PACKAGES += x11/library/glu
