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
# Copyright 2021 Jake Goerzen
#

BUILD_BITS= 64

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		freeciv
COMPONENT_VERSION=	2.6.6
COMPONENT_REVISION=	1
COMPONENT_SUMMARY=	Free and Open Source empire-building strategy game inspired by the history of human civilization.
COMPONENT_PROJECT_URL=	http://www.freeciv.org
COMPONENT_FMRI=		games/freeciv
COMPONENT_CLASSIFICATION=	Applications/Games
COMPONENT_SRC_NAME=	freeciv
COMPONENT_SRC=          $(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH=	\
	sha256:7bcfe5dd3c081122e7cde7cdb24f57c3681d6a9667496faed207a91ac3165811
COMPONENT_ARCHIVE_URL=  http://prdownloads.sourceforge.net/freeciv/$(COMPONENT_SRC).tar.bz2?download
COMPONENT_LICENSE=	GPLv2.0
COMPONENT_LICENSE_FILE=	COPYING

TEST_TARGET= $(NO_TESTS)

include $(WS_MAKE_RULES)/common.mk

CONFIGURE_OPTIONS += --disable-sdl-mixer
CONFIGURE_OPTIONS += --disable-dependency-tracking

# Auto-generated dependencies
REQUIRED_PACKAGES += compress/bzip2
REQUIRED_PACKAGES += compress/xz
REQUIRED_PACKAGES += image/imagemagick
REQUIRED_PACKAGES += library/desktop/cairo
REQUIRED_PACKAGES += library/desktop/gdk-pixbuf
REQUIRED_PACKAGES += library/desktop/gtk3
REQUIRED_PACKAGES += library/desktop/pango
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += library/readline
REQUIRED_PACKAGES += library/zlib
REQUIRED_PACKAGES += runtime/lua-53
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += web/curl
