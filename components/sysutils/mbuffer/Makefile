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
# Copyright 2011 EveryCity Ltd. All rights reserved.
# Copyright 2013, Jon Tibble.  All rights reserved.
# Copyright 2016, Jim Klimov
# Copyright 2021 Andreas Grueninger, Grueninger GmbH, (grueni). All rights reserved.
#

BUILD_BITS= 64

include ../../../make-rules/shared-macros.mk

GCC_VERSION= 10

COMPONENT_NAME=		mbuffer
COMPONENT_VERSION=	20210829
COMPONENT_FMRI=		shell/mbuffer
COMPONENT_CLASSIFICATION=	Applications/System Utilities
COMPONENT_SUMMARY=	mbuffer - tool for buffering data streams
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tgz
COMPONENT_ARCHIVE_HASH=	sha256:74e6f01c716147128d1c7ba0a8f01bf3df67415d67d90ac8c39892514cbc69ae
COMPONENT_ARCHIVE_URL=	https://www.maier-komor.de/software/mbuffer/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL=	https://www.maier-komor.de/mbuffer.html
COMPONENT_LICENSE=	GPLv3

COMPONENT_PRE_CONFIGURE_ACTION =	( $(CLONEY) $(SOURCE_DIR) $(@D) )

CONFIGURE_OPTIONS +=	--sysconfdir=/etc

include $(WS_MAKE_RULES)/common.mk

# build dependency
REQUIRED_PACKAGES += developer/gcc-10

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
