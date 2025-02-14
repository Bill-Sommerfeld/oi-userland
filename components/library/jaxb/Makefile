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
# Copyright 2017 Alexander Pyhalov
#

BUILD_STYLE= justmake
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		jaxb-ri
COMPONENT_VERSION=	2.2.11
COMPONENT_REVISIOM=	3
COMPONENT_SUMMARY=      jaxb - Java Architecture for XML Binding
COMPONENT_PROJECT_URL=	https://jaxb.java.net/
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_NAME)-$(COMPONENT_VERSION).src.zip
COMPONENT_ARCHIVE_HASH=	sha256:eb901f010d98d8cc7115c5440016443d02e7d1452d85ff565bf20a977bd9cb4e
COMPONENT_ARCHIVE_URL=	https://pkgs.fedoraproject.org/repo/pkgs/glassfish-jaxb/$(COMPONENT_ARCHIVE)/bed496dd96e5b9efc4539fc5bdb69c69/$(COMPONENT_ARCHIVE)
COMPONENT_CLASSIFICATION= Development/Java
COMPONENT_FMRI=	library/java/jaxb
COMPONENT_LICENSE=	CDDL1.0,GPLv2.0
COMPONENT_LICENSE_FILE=	jaxb.license

include $(WS_MAKE_RULES)/common.mk

UNPACK_ARGS= -r $(COMPONENT_SRC)

COMPONENT_BUILD_ENV += JAVA_HOME=$(JAVA_HOME)
# Build fails with some locales like french
COMPONENT_BUILD_ENV += LC_ALL=C

COMPONENT_BUILD_ACTION= \
	cd $(@D); $(ENV) $(COMPONENT_BUILD_ENV) \
	mvn install

# Nothing to do here
COMPONENT_INSTALL_ACTION= true

PKG_PROTO_DIRS += $(BUILD_DIR_64)

# Manually added dependencies
REQUIRED_PACKAGES += developer/build/maven
REQUIRED_PACKAGES += developer/java/openjdk8

# Auto-generated dependencies
REQUIRED_PACKAGES += shell/ksh93
