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
# This file was automatically generated using the following command:
#   $WS_TOOLS/perl-integrate-module Module::ScanDeps
#

BUILD_STYLE = makemaker

include ../../../make-rules/shared-macros.mk

COMPONENT_PERL_MODULE =		Module::ScanDeps
HUMAN_VERSION =			1.35
COMPONENT_SUMMARY =		Module::ScanDeps - Recursively scan Perl code for dependencies
COMPONENT_CPAN_AUTHOR =		RSCHUPP
COMPONENT_ARCHIVE_HASH =	\
	sha256:e5beb3adf55be3dab71f9a1416d4bad57b14e5e05c96370741b9d8f96a51b612
COMPONENT_LICENSE =		Artistic-1.0 OR GPL-1.0-or-later
COMPONENT_LICENSE_FILE =	LICENSE

include $(WS_MAKE_RULES)/common.mk

# remove lines that changes with every test run
COMPONENT_TEST_TRANSFORMS += "-e '/syntax OK$$/d'"

# Auto-generated dependencies
PERL_REQUIRED_PACKAGES += runtime/perl
TEST_REQUIRED_PACKAGES.perl += library/perl-5/ipc-run3
TEST_REQUIRED_PACKAGES.perl += library/perl-5/test-requires
