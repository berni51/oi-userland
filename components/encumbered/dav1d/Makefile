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
# Copyright 2021 (c) Tim Mooney. All rights reserved.
#
BUILD_BITS=		64
BUILD_STYLE=		meson
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=         dav1d
COMPONENT_VERSION=      0.9.2
COMPONENT_REVISION=     1
COMPONENT_FMRI=         codec/dav1d
COMPONENT_SUMMARY=      A fast, cross-platform AV1 decoder
COMPONENT_CLASSIFICATION=System/Multimedia Libraries
COMPONENT_PROJECT_URL=  https://code.videolan.org/videolan/dav1d
COMPONENT_SRC=          $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=      $(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_URL=  \
	$(COMPONENT_PROJECT_URL)/-/archive/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= \
	sha256:59a5fc9cc5d8ea780ad71ede6d589ed33fb5179d87780dcf80a00ee854952935
COMPONENT_LICENSE=      BSD 2-Clause Simplified License

include $(WS_MAKE_RULES)/encumbered.mk
include $(WS_MAKE_RULES)/common.mk

CONFIGURE_OPTIONS += -Denable_asm=true

unexport SHELLOPTS
# (first) delete the timing information from any line
# delete the "exit status N", it can cause issues too
# print lines that start with " N/NNN"
# print everything between "^Ok:" and "^Timeout:"
# delete the ninja log-related stuff at the end
COMPONENT_TEST_TRANSFORMS += \
	'-n ' \
	'-e "s/[ 	]*[0-9][0-9]*\.[0-9][0-9]s//" ' \
	'-e "s/[ 	]*exit status [0-9][0-9]*//" ' \
	'-e "/^[ 	]*[0-9][0-9]*\/[0-9][0-9]* /p" ' \
	'-e "/^Summary of/p" ' \
	'-e "/^Ok:/,/^Timeout:/p" ' \
	'-e "/^Full log written.*/,/^ninja: build stopped.*/d" '

# build requirement
REQUIRED_PACKAGES += developer/assembler/nasm

# Auto-generated dependencies
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
