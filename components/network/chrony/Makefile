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
# Copyright (c) 2023, Andreas Wacknitz
#

BUILD_BITS= 64
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		chrony
COMPONENT_VERSION=	4.5
COMPONENT_SUMMARY=	network time services
COMPONENT_DESCRIPTION=	A versatile implementation of the Network Time Protocol (NTP)
COMPONENT_PROJECT_URL=	https://chrony-project.org
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/releases/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= sha256:19fe1d9f4664d445a69a96c71e8fdb60bcd8df24c73d1386e02287f7366ad422
COMPONENT_SIG_URL=	$(COMPONENT_PROJECT_URL)/releases/$(COMPONENT_SRC)-tar-gz-asc.txt
COMPONENT_FMRI=	service/network/$(COMPONENT_NAME)
COMPONENT_CLASSIFICATION=	System/Services
COMPONENT_LICENSE=	GPLv2
COMPONENT_LICENSE_FILE=	COPYING

ASLR_MODE= $(ASLR_ENABLE)

include $(WS_MAKE_RULES)/common.mk

COMPONENT_PRE_CONFIGURE_ACTION= ( $(CLONEY) $(SOURCE_DIR) $(@D) )

CFLAGS += $(XPG6MODE)

CONFIGURE_OPTIONS += --libexecdir=$(USRLIBDIR)/inet
CONFIGURE_OPTIONS += --sysconfdir=$(ETCDIR)/inet
CONFIGURE_OPTIONS += --disable-shared
CONFIGURE_OPTIONS += --enable-ntp-signd
CONFIGURE_OPTIONS += --with-user=chrony

unexport SHELLOPTS

COMPONENT_TEST_TRANSFORMS += \
	' -n ' \
	' -e "/Testing/p" '

# Auto-generated dependencies
REQUIRED_PACKAGES += SUNWcs
REQUIRED_PACKAGES += library/gnutls-3
REQUIRED_PACKAGES += library/libedit
REQUIRED_PACKAGES += library/nettle
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
