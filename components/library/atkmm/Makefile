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
# Copyright 2016 Alexander Pyhalov
# Copyright 2018 Michal Nowak
# Copyright 2023 Andreas Wacknitz
#

BUILD_BITS= 64_and_32
BUILD_STYLE= meson
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		atkmm
COMPONENT_VERSION=	2.28.3
COMPONENT_REVISION=	1
COMPONENT_SUMMARY=	atkmm - C++ Wrapper for the atk Library
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH=  sha256:7c2088b486a909be8da2b18304e56c5f90884d1343c8da7367ea5cd3258b9969
COMPONENT_ARCHIVE_URL=  https://download.gnome.org/sources/atkmm/2.28/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=	https://www.gtkmm.org/
COMPONENT_FMRI=		library/desktop/c++/atkmm
COMPONENT_CLASSIFICATION=Desktop (GNOME)/Libraries
COMPONENT_LICENSE=	LGPLv2.1
COMPONENT_LICENSE_FILE=	COPYING

# There are no tests available.
TEST_TARGET= $(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk

CXXFLAGS += -std=c++17

PATH= $(PATH.gnu)

# Build dependency
REQUIRED_PACKAGES += developer/build/pkg-config
REQUIRED_PACKAGES += developer/documentation-tool/doxygen
REQUIRED_PACKAGES += developer/macro/gnu-m4
REQUIRED_PACKAGES += image/graphviz
REQUIRED_PACKAGES += library/desktop/c++/mm-common
REQUIRED_PACKAGES += library/libxslt

# Auto-generated dependencies
REQUIRED_PACKAGES += $(GCC_RUNTIME_PKG)
REQUIRED_PACKAGES += $(GXX_RUNTIME_PKG)
REQUIRED_PACKAGES += library/c++/glibmm
REQUIRED_PACKAGES += library/c++/sigcpp
REQUIRED_PACKAGES += library/desktop/atk
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += system/library
