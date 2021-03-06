#
# Copyright (C) 2011-2019 Intel Corporation. All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
#
#   * Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#   * Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in
#     the documentation and/or other materials provided with the
#     distribution.
#   * Neither the name of Intel Corporation nor the names of its
#     contributors may be used to endorse or promote products derived
#     from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#
#

include scripts/installConfig

SOURCE_FOLDER=package

ECL_INC_PATH=$(SOURCE_FOLDER)/$(INC_DIR)
USR_INC_PATH=$(addprefix $(DESTDIR)/usr/, $(INC_DIR))
USR_LIB_PATH=$(shell readlink -m $(addsuffix /$(shell dpkg-architecture -qDEB_HOST_MULTIARCH 2> /dev/null), $(addprefix $(DESTDIR)/usr/, $(notdir $(shell gcc -print-multi-os-directory)))))

SPLIT_VERSION=$(word $2,$(subst ., ,$1))

ECL_VER=1.0.0
LCH_VER=1.0.0
PLF_VER=1.0.0
EPID_VER=1.0.0
QEX_VER=1.0.0

default:

install:
	install -d $(USR_INC_PATH)
	install $(ECL_INC_PATH)/* $(USR_INC_PATH)
	install -d $(USR_LIB_PATH)
	cd $(USR_LIB_PATH) && \
	ln -fs libsgx_enclave_common.so.$(call SPLIT_VERSION,$(ECL_VER),1) libsgx_enclave_common.so && \
	ln -fs libsgx_epid.so.$(call SPLIT_VERSION,$(EPID_VER),1) libsgx_epid.so && \
	ln -fs libsgx_launch.so.$(call SPLIT_VERSION,$(LCH_VER),1) libsgx_launch.so && \
	ln -fs libsgx_platform.so.$(call SPLIT_VERSION,$(PLF_VER),1) libsgx_platform.so && \
	ln -fs libsgx_quote_ex.so.$(call SPLIT_VERSION,$(QEX_VER),1) libsgx_quote_ex.so
