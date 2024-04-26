# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

set(SDK_ROOT_PATH   ${CMAKE_CURRENT_SOURCE_DIR}/../../../)
# set(BOARD_ROOT      ${SDK_ROOT_PATH})
# set(SNIPPET_ROOT    ${SDK_ROOT_PATH}/boards)

list(APPEND ZEPHYR_EXTRA_MODULES ${SDK_ROOT_PATH}/TinyMaix)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(hello_world)

target_sources(app PRIVATE src/main.c)
