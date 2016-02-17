# Copyright 2016 Real Logic Ltd.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

SET(SOURCE
    MediaDriver.cpp
    Receiver.cpp
    media/UdpChannel.cpp
    media/InetAddress.cpp
    uri/AeronUri.cpp
    uri/NetUtil.cpp
    media/UdpChannelTransport.cpp
    media/InterfaceLookup.cpp
    media/InterfaceSearchAddress.cpp
    media/NetworkInterface.cpp
    media/ReceiveChannelEndpoint.cpp
    media/ReceiveChannelEndpoint.h
    media/SendChannelEndpoint.cpp
    media/SendChannelEndpoint.h)

SET(HEADERS
    concurrent/OneToOneConcurrentArrayQueue.h
    uri/AeronUri.h
    uri/NetUtil.h
    media/InterfaceSearchAddress.h
    media/InterfaceLookup.h
    media/UdpChannel.h
    media/UdpChannelTransport.h
    media/NetworkInterface.h
    media/ReceiveChannelEndpoint.cpp
    media/ReceiveChannelEndpoint.h
    media/SendChannelEndpoint.cpp
    media/SendChannelEndpoint.h
    DataPacketDispatcher.cpp
    DataPacketDispatcher.h)

add_library(aeron_driver ${SOURCE} ${HEADERS})
add_executable(MediaDriver MediaDriverMain.cpp)

target_link_libraries(
    aeron_driver
    aeron_client
    ${CMAKE_THREAD_LIBS_INIT})

target_link_libraries(
    MediaDriver
    aeron_client
    aeron_driver
    ${CMAKE_THREAD_LIBS_INIT})