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
BUILD_STYLE=justmake
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= pyml
COMPONENT_VERSION= 20211015
COMPONENT_SUMMARY= pyml - OCaml bindings for Python
COMPONENT_PROJECT_URL= https://github.com/thierry-martinez/pyml/
COMPONENT_FMRI= library/ocaml/pyml
COMPONENT_CLASSIFICATION= Development/Other Languages
COMPONENT_SRC=		$(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_ARCHIVE_URL=	https://github.com/thierry-martinez/pyml/archive/$(COMPONENT_VERSION).tar.gz
COMPONENT_ARCHIVE_HASH= sha256:4ef930b3ff8c7c4115b87eabd194795fa1da3aedbebbdcddf82af84eadbb94ab
COMPONENT_LICENSE= BSD 2-Clause

TEST_TARGET=$(NO_TESTS)
include $(WS_MAKE_RULES)/common.mk
include $(WS_MAKE_RULES)/ocaml.mk

PATH=$(PATH.gnu)

PYTHON_VERSION= 3.9

COMPONENT_BUILD_ARGS=-j1

COMPONENT_PRE_CONFIGURE_ACTION  +=  $(CLONEY) $(SOURCE_DIR) $(@D) ;

COMPONENT_PRE_INSTALL_ACTION += ( $(RM) -r $(PROTO_DIR)$(OCAML_LIBDIR) && \
                                $(MKDIR) $(PROTO_DIR)$(OCAML_LIBDIR)/stublibs; )

# Build dependencies
REQUIRED_PACKAGES+= library/ocaml/ocamlbuild
REQUIRED_PACKAGES+= library/ocaml/ocaml-findlib
REQUIRED_PACKAGES+= library/ocaml/stdcompat
REQUIRED_PACKAGES+= runtime/ocaml

# Auto-generated dependencies
