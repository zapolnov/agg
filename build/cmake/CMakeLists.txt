cmake_minimum_required(VERSION 3.30)

if(NOT IGAGIS_CMAKE_COMMON_INCLUDED)
    set(dir "${CMAKE_CURRENT_SOURCE_DIR}/../tool-configs/cmake")
    if(NOT EXISTS "${dir}/common.cmake")
        file(MAKE_DIRECTORY "${dir}")
        file(DOWNLOAD "https://github.com/zapolnov/tool-configs/raw/refs/heads/main/cmake/common.cmake"
            "${dir}/common.cmake")
    endif()
    include("${dir}/common.cmake")
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
