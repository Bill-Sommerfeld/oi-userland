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
# Copyright 2016 Aurelien Larcher.  All rights reserved.
# Copyright 2019 Alexander Pyhalov
# Copyright 2019 Michal Nowak
# Copyright 2019 Till Wegmüller
# Copyright 2022 Klaus Ziegler
# Copyright 2023 Friedrich Kink
#

BUILD_BITS= 64
BUILD_STYLE= cmake
include ../../../make-rules/shared-macros.mk

COMPONENT_MJR_VERSION=	15
COMPONENT_BASE_VERSION=	$(COMPONENT_MJR_VERSION).0
COMPONENT_NAME=	clang-$(COMPONENT_MJR_VERSION)
COMPONENT_VERSION=		$(COMPONENT_BASE_VERSION).7
COMPONENT_REVISION=		1
COMPONENT_SUMMARY=		LLVM tools and Clang compiler
COMPONENT_PROJECT_URL=	https://llvm.org/
COMPONENT_SRC=		$(LLVM_NAME)-$(COMPONENT_VERSION).src
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= sha256:4ad8b2cc8003c86d0078d15d987d84e3a739f24aae9033865c027abae93ee7a4
COMPONENT_ARCHIVE_URL=  https://github.com/llvm/llvm-project/releases/download/llvmorg-$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=		developer/$(COMPONENT_NAME)
COMPONENT_CLASSIFICATION=	Development/C
COMPONENT_LICENSE=	BSD
COMPONENT_LICENSE_FILE=	LICENSE.TXT

LLVM_NAME= llvm
CLANG_NAME= clang

COMPONENT_ARCHIVE_1=    $(CLANG_NAME)-$(COMPONENT_VERSION).src.tar.xz
COMPONENT_ARCHIVE_HASH_1= sha256:a6b673ef15377fb46062d164e8ddc4d05c348ff8968f015f7f4af03f51000067
COMPONENT_ARCHIVE_URL_1=  https://github.com/llvm/llvm-project/releases/download/llvmorg-$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE_1)

COMPONENT_ARCHIVE_2=    cmake-$(COMPONENT_VERSION).src.tar.xz
COMPONENT_ARCHIVE_HASH_2= sha256:8986f29b634fdaa9862eedda78513969fe9788301c9f2d938f4c10a3e7a3e7ea
COMPONENT_ARCHIVE_URL_2=  https://github.com/llvm/llvm-project/releases/download/llvmorg-$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE_2)

include $(WS_MAKE_RULES)/common.mk

CMAKE_PREFIX= /usr/clang/$(COMPONENT_BASE_VERSION)

PKG_MACROS += GCC_VERSION=$(GCC_VERSION)

COMPONENT_POST_UNPACK_ACTION += \
  $(UNPACK) $(USERLAND_ARCHIVES)$(COMPONENT_ARCHIVE_1) && \
	mv $(CLANG_NAME)-$(COMPONENT_VERSION).src $(COMPONENT_SRC)/tools/clang && \
  $(UNPACK) $(USERLAND_ARCHIVES)$(COMPONENT_ARCHIVE_2) && \
	mv cmake-$(COMPONENT_VERSION).src/Modules/* $(COMPONENT_SRC)/cmake/modules && \
  $(RM) -r cmake-$(COMPONENT_VERSION).src

COMPONENT_PRE_CONFIGURE_ACTION = ( $(CLONEY) $(SOURCE_DIR) $(@D); )

COMPONENT_POST_INSTALL_ACTION =  \
        for file in `echo $(PROTO_DIR)/$(CMAKE_PREFIX)/bin/*`; do \
                /usr/bin/elfedit -e 'dyn:runpath $(GCC_LIBDIR):$(CMAKE_PREFIX)/lib' $$file ; \
        done && \
        for file in \
                `ggrep -rlh '^\#!*/usr/bin/env python' $(PROTO_DIR)/$(CMAKE_PREFIX)`; do \
          sed -i -e 's:\#!/usr/bin/env.*:\#!$(PYTHON):' $$file; \
        done

COMPONENT_TEST_CMD = $(GMAKE)
COMPONENT_TEST_TARGETS = check-all
COMPONENT_TEST_ENV += PATH=$(PATH.gnu)

# Do not change the order of these regexp transforms.
COMPONENT_TEST_TRANSFORMS += \
    '-e "/^Testing Time: .*$$/d" ' \
    '-e "/^make.*$$/d" ' \
    '-e "/^Failed Tests /,/Unexpected Passed:/p" ' \
    '-e "" ' \
    '-e "/.*/d" '

TESTSUITE_MAKE = $(GMAKE)

CMAKE_OPTIONS += -DCMAKE_C_COMPILER=$(CC)
CMAKE_OPTIONS += -DCMAKE_CXX_COMPILER=$(CXX)
CMAKE_OPTIONS += -DGCC_INSTALL_PREFIX=$(GCC_ROOT)
CMAKE_OPTIONS += -DCMAKE_CXX_LINK_FLAGS="-L$(GCC_LIBDIR) -Wl,-rpath,$(GCC_LIBDIR)"
CMAKE_OPTIONS += -DCMAKE_BUILD_TYPE=Release
CMAKE_OPTIONS += -DCLANG_DEFAULT_LINKER="/usr/bin/ld"
CMAKE_OPTIONS += -DLLVM_ENABLE_EH=ON
CMAKE_OPTIONS += -DLLVM_ENABLE_RTTI=ON
CMAKE_OPTIONS += -DLLVM_LINK_LLVM_DYLIB=ON
CMAKE_OPTIONS += -DLLVM_INCLUDE_BENCHMARKS=OFF
CMAKE_OPTIONS += -DLLVM_INSTALL_UTILS=ON
CMAKE_OPTIONS += -DCLANG_DEFAULT_RTLIB=libgcc
CMAKE_OPTIONS += -DCLANG_DEFAULT_CXX_STDLIB=libstdc++
CMAKE_OPTIONS += -DPYTHON_EXECUTABLE="$(PYTHON)"

# Auto-generated dependencies
PYTHON_REQUIRED_PACKAGES += runtime/python
REQUIRED_PACKAGES += $(GCC_RUNTIME_PKG)
REQUIRED_PACKAGES += $(GXX_RUNTIME_PKG)
REQUIRED_PACKAGES += SUNWcs
REQUIRED_PACKAGES += compress/zstd
REQUIRED_PACKAGES += library/libedit
REQUIRED_PACKAGES += library/libxml2
REQUIRED_PACKAGES += library/zlib
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
