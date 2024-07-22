cmake_minimum_required(VERSION 3.10)

project(libftdi)

add_library(libftdi STATIC IMPORTED GLOBAL)

if(WIN32 AND MSVC)
    if(CMAKE_CL_64)
        set(LIBFTDI_PATH "${CMAKE_CURRENT_LIST_DIR}/lib/Win32/x86_64/ftd2xx.lib")
    else(CMAKE_CL_64)
        set(LIBFTDI_PATH "${CMAKE_CURRENT_LIST_DIR}/lib/Win32/x86/ftd2xx.lib")
    endif(CMAKE_CL_64)

    set_target_properties(
        libftdi PROPERTIES
        IMPORTED_LOCATION ${LIBFTDI_PATH}
    )

    target_compile_definitions(libftdi INTERFACE FTD2XX_STATIC)

    target_include_directories(libftdi INTERFACE ${CMAKE_CURRENT_LIST_DIR}/include)
endif(WIN32 AND MSVC)
