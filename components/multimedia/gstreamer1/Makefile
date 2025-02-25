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
# Copyright 2016-2018 Aurelien Larcher.  All rights reserved.
# Copyright 2019 Michal Nowak
# Copyright 2021 Tim Mooney.  All rights reserved.
#

BUILD_BITS=	32_and_64
BUILD_STYLE=	meson

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		gstreamer1
COMPONENT_VERSION=	1.18.5
COMPONENT_SUMMARY=	GNOME streaming media framework
COMPONENT_PROJECT_URL=	https://gstreamer.freedesktop.org/
COMPONENT_FMRI=		library/audio/gstreamer1
COMPONENT_CLASSIFICATION= System/Multimedia Libraries
COMPONENT_SRC_NAME=	gstreamer
COMPONENT_SRC=		$(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= \
  sha256:55862232a63459bbf56abebde3085ca9aec211b478e891dacea4d6df8cafe80a
COMPONENT_ARCHIVE_URL= \
  $(COMPONENT_PROJECT_URL)/src/$(COMPONENT_SRC_NAME)/$(COMPONENT_ARCHIVE)
COMPONENT_LICENSE=	LGPLv2

include $(WS_MAKE_RULES)/common.mk

gcc_OPT = -O2

PATH = $(PATH.gnu)

CFLAGS += -I/usr/X11/include
# until meson.build searches for gmp's CFLAGS, needed for gst_utils test
CFLAGS += -I/usr/include/gmp

CONFIGURE_OPTIONS += --sysconfdir=/etc
CONFIGURE_OPTIONS += --libexecdir=$(USRLIBDIR.$(BITS))
CONFIGURE_OPTIONS += -Dexamples=disabled
CONFIGURE_OPTIONS.32 += -Dintrospection=disabled
CONFIGURE_OPTIONS.64 += -Dintrospection=enabled
#CONFIGURE_OPTIONS += --program-suffix=""
CONFIGURE_OPTIONS += -Dpackage-origin="https://github.com/OpenIndiana/oi-userland"

# CFLAGS are not passed to compiler when g-ir-scanner is used
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS)"
COMPONENT_BUILD_ENV += CC="$(CC)"
COMPONENT_INSTALL_ENV += CFLAGS="$(CFLAGS)"
COMPONENT_INSTALL_ENV += CC="$(CC)"

# (first) delete the timing information from any line
# delete the "exit status N", it can cause issues too
# print lines that start with " N/NNN"
# print everything between "^Ok:" and "^Timeout:"
# delete the ninja log-related stuff at the end
unexport SHELLOPTS
COMPONENT_TEST_TRANSFORMS += \
	'-n ' \
	'-e "s/[ 	]*[0-9][0-9]*\.[0-9][0-9]s//" ' \
	'-e "s/[ 	]*exit status [0-9][0-9]*//" ' \
	'-e "/^[ 	]*[0-9][0-9]*\/[0-9][0-9]* /p" ' \
	'-e "/^Summary of/p" ' \
	'-e "/^Ok:/,/^Timeout:/p" ' \
	'-e "/^Full log written.*/,/^ninja: build stopped.*/d" '

test: $(TEST_32_and_64)

# not picked up by REQUIRED_PACKAGES but probably still needed
# for the 64 bit build to do introspection
REQUIRED_PACKAGES += library/desktop/gobject/gobject-introspection

# gmp & gsl needed only for the test suite
REQUIRED_PACKAGES += library/gmp
REQUIRED_PACKAGES += developer/gsl

# Auto-generated dependencies
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += runtime/python-39
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
