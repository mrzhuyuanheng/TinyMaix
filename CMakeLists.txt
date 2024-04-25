cmake_minimum_required(VERSION 3.10)

# set(CMAKE_C_COMPILER "gcc")
# set(CMAKE_CXX_COMPILER "g++")

project(tinymaix)

# set(CMAKE_AR "ar")
# set(CMAKE_RANLIB "ranlib")
# set(CMAKE_STRIP "strip")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3 " CACHE STRING "c flags")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3 " CACHE STRING "c++ flags")
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR}/src lib_tinymaix) 
include_directories( . ${CMAKE_CURRENT_SOURCE_DIR}/include)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
add_library(${PROJECT_NAME} STATIC ${lib_tinymaix})
# zephyr_library_named(tiny_maix)
zephyr_library_sources(
    ./src/tm_layers_fp8.c
    ./src/tm_layers_O1.c
    ./src/tm_layers.c
    ./src/tm_model.c
    ./src/tm_stat.c
)

zephyr_include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
zephyr_include_directories(${CMAKE_CURRENT_SOURCE_DIR}/tools/tmdl)