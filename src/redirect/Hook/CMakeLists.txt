# Copyright (C) 2010 CactusEMU <http://www.cactusemu.com/>
#
# This file is free software; as a special exception the author gives
# unlimited permission to copy and/or distribute it, with or without
# modifications, as long as this notice is preserved.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

file(GLOB sources_localdir *.cpp *.h)

set(CactusRedirect_SRCS
  ${CactusRedirect_SRCS}
  ${sources_localdir}
)

set(CactusRedirect_LINK_FLAGS "/LIBPATH:\"${CMAKE_CURRENT_SOURCE_DIR}\"")

add_library(CactusRedirect SHARED ${CactusRedirect_SRCS})

set_target_properties(CactusRedirect PROPERTIES LINK_FLAGS "${CactusRedirect_LINK_FLAGS}")

if( UNIX )
  install(TARGETS CactusRedirect DESTINATION bin)
elseif( WIN32 )
  install(TARGETS CactusRedirect DESTINATION "${CMAKE_INSTALL_PREFIX}")
endif()
