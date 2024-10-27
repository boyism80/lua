cmake_minimum_required(VERSION 3.28)

if (POLICY CMP0048)
  cmake_policy(SET CMP0048 NEW)
endif (POLICY CMP0048)

project(boyism80/lua,
        VERSION 1.0.0
        DESCRIPTION "lua 5.3.5 with cmake"
        HOMEPAGE_URL "https://github.com/boyism80/lua"
        LANGUAGES C
)

option(BUILD_SHARED_LIBS "Build as shared library" OFF)
add_definitions(-DREDISCPP_HEADER_ONLY)

include(GNUInstallDirs)
include_directories("${PROJECT_SOURCE_DIR}/upstream")
file(GLOB_RECURSE SOURCE_FILES "${PROJECT_SOURCE_DIR}/upstream/*.c")
add_library(lua ${SOURCE_FILES})
install(TARGETS lua DESTINATION ${CMAKE_INSTALL_LIBDIR})

file(GLOB_RECURSE HEADER_FILES "${PROJECT_SOURCE_DIR}/upstream/*.h")
install(FILES ${HEADER_FILES} DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/lua)