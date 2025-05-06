cmake_minimum_required(VERSION 3.30)

if(NOT IGAGIS_CMAKE_COMMON_INCLUDED)
    if(IGAGIS_CMAKE_COMMON)
        include("${IGAGIS_CMAKE_COMMON}")
    else()
        include(../tool-configs/cmake/common.cmake)
    endif()
endif()

set(name agg)

set(srcs)
add_source_directory(srcs
    "${CMAKE_CURRENT_SOURCE_DIR}/../../src/${name}/src"
    PATTERNS "*.cpp" "*.hpp"
)

declare_library(${name}
    SOURCES
        ${srcs}
    PRIVATE_INCLUDE_DIRECTORIES
        "${CMAKE_CURRENT_SOURCE_DIR}/../../src/${name}/include/${name}"
    INSTALL_INCLUDE_DIRECTORIES
        "${CMAKE_CURRENT_SOURCE_DIR}/../../src/${name}/include/${name}"
    PUBLIC_INCLUDE_DIRECTORIES
        "${CMAKE_CURRENT_SOURCE_DIR}/../../src/${name}/include"
)
