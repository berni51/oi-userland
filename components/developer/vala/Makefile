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
# Copyright (c) 2013 David Hoeppner. All rights reserved.
# Copyright (c) 2017, 2020 Andreas Wacknitz
# Copyright (c) 2019 Jason Martin
# Copyright (c) 2021 Tim Mooney.  All rights reserved

BUILD_BITS=64_and_32
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=     vala
COMPONENT_VERSION_MJR=  0.54
COMPONENT_VERSION=	$(COMPONENT_VERSION_MJR).6
COMPONENT_SUMMARY=  Vala programming language
COMPONENT_PROJECT_URL=  https://wiki.gnome.org/Vala
COMPONENT_SRC=      $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=  $(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= sha256:49d60d96a3fdf6c4287397442bc6d6d95bf40aa7df678ee49128c4b11ba6e469
COMPONENT_ARCHIVE_URL=	https://download.gnome.org/sources/vala/$(COMPONENT_VERSION_MJR)/$(COMPONENT_ARCHIVE)
COMPONENT_FMRI=     developer/vala
COMPONENT_CLASSIFICATION=   Development/Other Languages
COMPONENT_LICENSE=  LGPL2.1

include $(WS_MAKE_RULES)/common.mk

PATH=$(PATH.gnu)

COMPONENT_PRE_CONFIGURE_ACTION = ($(CLONEY) $(SOURCE_DIR) $(@D))

CONFIGURE_SCRIPT = $(@D)/configure

CONFIGURE_OPTIONS  +=  --disable-static
CONFIGURE_OPTIONS  +=  --enable-shared

COMPONENT_TEST_ENV += LANG=C
COMPONENT_TEST_ENV += CC="$(CC)"
COMPONENT_TEST_ENV += CXX="$(CXX)"
COMPONENT_TEST_ENV += FC="$(FC)"
COMPONENT_TEST_ENV += CFLAGS="$(CFLAGS)"
COMPONENT_TEST_ENV += CXXFLAGS="$(CXXFLAGS)"
COMPONENT_TEST_ENV += FCFLAGS="$(FCFLAGS)"
COMPONENT_TEST_ENV += LDFLAGS="$(LDFLAGS)"

unexport SHELLOPTS
COMPONENT_TEST_MASTER = $(COMPONENT_TEST_RESULTS_DIR)/results-all.master
COMPONENT_TEST_ARGS += -k -i
COMPONENT_TEST_TRANSFORMS += \
	'-n ' \
	'-e "/^PASS: /p" ' \
	'-e "/^FAIL: /p" ' \
	'-e "/^SKIP: /p" '

# Auto-generated dependencies
REQUIRED_PACKAGES += image/graphviz
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += shell/ksh93
REQUIRED_PACKAGES += system/library
