# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.1)

if (CONFIG_TINY_MAXI)
        zephyr_library_named(tinymaix)
        add_subdirectory(../)
endif()
