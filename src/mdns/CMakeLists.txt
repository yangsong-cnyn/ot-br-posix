#
#  Copyright (c) 2020, The OpenThread Authors.
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

if(OTBR_MDNS STREQUAL "avahi")
    add_library(otbr-mdns
        mdns.cpp
        mdns_avahi.cpp
    )
    target_compile_definitions(otbr-mdns PUBLIC
        OTBR_ENABLE_MDNS_AVAHI=1
    )
    target_link_libraries(otbr-mdns
        PUBLIC
            otbr-common
        PRIVATE
            otbr-utils
            avahi-client
            avahi-common
    )
endif()

if(OTBR_MDNS STREQUAL "mDNSResponder")
    add_library(otbr-mdns
        mdns.cpp
        mdns_mdnssd.cpp
    )
    target_compile_definitions(otbr-mdns PUBLIC
        OTBR_ENABLE_MDNS_MDNSSD=1
    )
    target_link_libraries(otbr-mdns
        PUBLIC
            otbr-common
        PRIVATE
            otbr-utils
            dns_sd
    )
endif()

if(OTBR_MDNS STREQUAL "openthread")
    add_library(otbr-mdns
        mdns.cpp
        mdns_openthread.cpp
    )
    target_compile_definitions(otbr-mdns PUBLIC
        OTBR_ENABLE_MDNS_OPENTHREAD=1
    )
    target_link_libraries(otbr-mdns
        PUBLIC
            otbr-common
        PRIVATE
            otbr-utils
    )
endif()
