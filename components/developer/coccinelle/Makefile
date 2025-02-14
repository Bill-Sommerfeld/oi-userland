#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"). You may
# only use this file in accordance with the terms of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source. A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2020 Aurelien Larcher
#

BUILD_BITS=64
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= coccinelle
COMPONENT_VERSION= 1.1.1
COMPONENT_SUMMARY= coccinelle - program matching and transformation engine which provides the language SmPL
COMPONENT_PROJECT_URL=	https://coccinelle.gitlabpages.inria.fr/website/
COMPONENT_FMRI= developer/coccinelle
COMPONENT_CLASSIFICATION= Development/C 
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_URL=	https://github.com/coccinelle/coccinelle/archive/$(COMPONENT_VERSION).tar.gz
COMPONENT_ARCHIVE_HASH=	sha256:095919e129ac563586d880ebbc5aac829fec224177090aebe34dc34ed5f142bf
COMPONENT_LICENSE= GPLv2

include $(WS_MAKE_RULES)/common.mk

PYTHON_VERSION=3.9

PATH=$(PATH.gnu)

COMPONENT_PREP_ACTION= ( cd $(@D) && ./autogen; )

COMPONENT_PRE_CONFIGURE_ACTION  +=  $(CLONEY) $(SOURCE_DIR) $(@D) ;

COMPONENT_BUILD_ARGS=-j1

CONFIGURE_OPTIONS+= --with-python=$(PYTHON)
CONFIGURE_OPTIONS+= --with-bash-completion=$(USRSHAREDIR)/bash-completion/completions


# Build dependencies
REQUIRED_PACKAGES+= library/ocaml/ocaml-findlib
REQUIRED_PACKAGES+= library/ocaml/ocaml-num
REQUIRED_PACKAGES+= library/ocaml/parmap
REQUIRED_PACKAGES+= library/ocaml/pyml
REQUIRED_PACKAGES+= library/ocaml/stdcompat
REQUIRED_PACKAGES+= runtime/python-35

# Auto-generated dependencies
REQUIRED_PACKAGES += library/pcre
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
