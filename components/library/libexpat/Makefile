#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#

#
# Copyright (c) 2011, 2012, Oracle and/or its affiliates. All rights reserved.
# Copyright (c) 2017, Aurelien Larcher
# Copyright (c) 2019, Michal Nowak
#

BUILD_BITS= 64_and_32
USE_DEFAULT_TEST_TRANSFORMS= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		libexpat
COMPONENT_VERSION=	2.6.0
COMPONENT_VERSION_U=$(shell echo $(COMPONENT_VERSION) | tr . _)
COMPONENT_SUMMARY=	libexpat - XML parser library
COMPONENT_DESCRIPTION=	A fast, non-validating, stream-oriented XML parsing library	
COMPONENT_PROJECT_URL=	https://libexpat.github.io
COMPONENT_SRC_NAME=	expat
COMPONENT_SRC=		$(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.lz
COMPONENT_ARCHIVE_HASH=	sha256:138438bab8658b049e6eba74aac11dd71c7bdd6bb80b3bc4c18bfa5a65f08249
COMPONENT_ARCHIVE_URL=	https://github.com/libexpat/libexpat/releases/download/R_$(COMPONENT_VERSION_U)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		library/expat
COMPONENT_CLASSIFICATION=	System/Libraries
COMPONENT_LICENSE=	expat license
COMPONENT_LICENSE_FILE=	COPYING

include $(WS_MAKE_RULES)/common.mk

CFLAGS += $(CPP_LARGEFILES)

# Deliver only 64-bit binary
CONFIGURE_OPTIONS.64 += --bindir=/usr/bin
CONFIGURE_OPTIONS += --disable-static

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
