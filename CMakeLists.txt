cmake_minimum_required(VERSION 2.8)

cmake_policy(SET CMP0048 NEW)
file(STRINGS ${CMAKE_SOURCE_DIR}/VERSION PROJECT_VERSION)

project(learn-cpp VERSION ${PROJECT_VERSION})

enable_testing()

set(CMAKE_VERBOSE_MAKEFILE)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(CTest)
include(ExternalProject)
include(ProcessorCount)
include(CheckSymbolExists)

ProcessorCount(NUM_CORES)

find_program(MAKE_EXE NAMES gmake nmake make)

if (CMAKE_BUILD_TYPE STREQUAL "Release")
  add_definitions(-DNDEBUG)
endif()

find_package(Boost REQUIRED)
find_package(ZLIB REQUIRED)
find_package(Threads REQUIRED)
find_package(nlohmann_json REQUIRED CONFIG)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

add_subdirectory(cpp_primer)
add_subdirectory(learn_boost)
add_subdirectory(learn_features)
add_subdirectory(learn_fmt)
add_subdirectory(learn_gtest)
add_subdirectory(learn_json)
add_subdirectory(learn_qt)
add_subdirectory(learn_range)
add_subdirectory(learn_seqan)
add_subdirectory(learn_stl)
add_subdirectory(learn_taskflow)
