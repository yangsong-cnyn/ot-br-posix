#
#  Copyright (c) 2020-2021, The OpenThread Authors.
#  All rights reserved.
#
#  Redistribution and use in source and binary forms, with or without
#  modification, are permitted provided that the following conditions are met:
#  1. Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#  2. Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in the
#     documentation and/or other materials provided with the distribution.
#  3. Neither the name of the copyright holder nor the
#     names of its contributors may be used to endorse or promote products
#     derived from this software without specific prior written permission.
#
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
#  AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
#  IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
#  ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE
#  LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
#  CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
#  SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
#  INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
#  CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
#  ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
#  POSSIBILITY OF SUCH DAMAGE.
#

add_subdirectory(agent)
if(OTBR_BORDER_AGENT)
    add_subdirectory(border_agent)
endif()
add_subdirectory(common)
if(OTBR_DBUS OR OTBR_FEATURE_FLAGS OR OTBR_TELEMETRY_DATA_API)
    add_subdirectory(proto)
endif()
add_subdirectory(host)

if(OTBR_DBUS)
    add_subdirectory(dbus)
endif()

if(OTBR_MDNS)
    add_subdirectory(mdns)
    if(NOT OTBR_MDNS STREQUAL "openthread")
        add_subdirectory(sdp_proxy)
        add_subdirectory(trel_dnssd)
    endif()
endif()

add_subdirectory(utils)

if(OTBR_OPENWRT)
    add_subdirectory(openwrt)
endif()

if(OTBR_WEB)
    add_subdirectory(web)
endif()

if(OTBR_REST)
    add_subdirectory(rest)
endif()

if (OTBR_BACKBONE_ROUTER)
    add_subdirectory(backbone_router)
endif()
