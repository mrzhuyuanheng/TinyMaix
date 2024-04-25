# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20)

if(CONFIG_TINY_MAIX)
    zephyr_library_named(tinymaix)
    # add_subdirectory(../)

    set(TINY_MAIX tinymaix)
    add_library(${TINY_MAIX} STATIC)
    
    target_sources(${TINY_MAIX} PRIVATE
        ${ZEPHYR_TINY_MAIX_MODULE_DIR}/src/tm_layers_fb8.c
        ${ZEPHYR_TINY_MAIX_MODULE_DIR}/src/tm_layers_01.c
        ${ZEPHYR_TINY_MAIX_MODULE_DIR}/src/tm_layers.c
        ${ZEPHYR_TINY_MAIX_MODULE_DIR}/src/tm_model.c
        ${ZEPHYR_TINY_MAIX_MODULE_DIR}/src/tm_stat.c
    )
    target_include_directories(${TINY_MAIX} 
        PRIVATE
        ${ZEPHYR_TINY_MAIX_MODULE_DIR}/include/
    )
endif()
