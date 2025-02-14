#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL)". You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2016 Alexander Pyhalov
# Copyright 2018 Michal Nowak
# Copyright 2023 Friedrich Kink
#

USE_DEFAULT_TEST_TRANSFORMS= yes
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		freetds
COMPONENT_VERSION=	1.4.10
COMPONENT_SUMMARY=	FreeTDS command-line utilities
COMPONENT_PROJECT_URL=	https://www.freetds.org
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:4f58ee544c94a75263c9e71449ec9cf50be45c899243a4bdb73ba4cb96b8f038
COMPONENT_ARCHIVE_URL=	$(COMPONENT_PROJECT_URL)/files/stable/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		database/freetds
COMPONENT_CLASSIFICATION=	System/Databases
COMPONENT_LICENSE=	GPLv2
COMPONENT_LICENSE_FILE=	COPYING.txt

include $(WS_MAKE_RULES)/common.mk

COMPONENT_PRE_CONFIGURE_ACTION += ( $(CLONEY) $(SOURCE_DIR) $(@D) )

CONFIGURE_OPTIONS += --sysconfdir=/etc
CONFIGURE_OPTIONS += --disable-static
CONFIGURE_OPTIONS += --enable-krb5
CONFIGURE_OPTIONS += --enable-msdblib
CONFIGURE_OPTIONS += --with-gnutls

COMPONENT_TEST_ARGS += -k

COMPONENT_TEST_ENV += LC_ALL=C.UTF-8

# Auto-generated dependencies
REQUIRED_PACKAGES += library/gmp
REQUIRED_PACKAGES += library/gnutls-3
REQUIRED_PACKAGES += library/nettle
REQUIRED_PACKAGES += library/readline
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
