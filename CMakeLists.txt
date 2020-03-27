#***************************************************************************
# Copyright (C) 2020 Robbert E. Peters (GizMoCuz)
#***************************************************************************
cmake_minimum_required(VERSION 3.0.2)

project("minizip" C)

# Set cmake debug postfix to d
set(CMAKE_DEBUG_POSTFIX "d")

set(PROJECT_NAME minizip)

INCLUDE(FindZLIB)

IF(NOT ZLIB_FOUND)
	message(FATAL_ERROR "zlib library is required for libminizip!")
ENDIF(NOT ZLIB_FOUND)

include_directories(${ZLIB_INCLUDE_DIR})
link_directories(${ZLIB_LIBRARIES})

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

add_library(${PROJECT_NAME} ioapi.c unzip.c zip.c)

target_link_libraries(${PROJECT_NAME} ${ZLIB_LIBRARIES})

