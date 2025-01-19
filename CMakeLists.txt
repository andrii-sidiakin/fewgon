cmake_minimum_required(VERSION 3.30 FATAL_ERROR)
project(FEWGON VERSION 0.0.0)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/tools/cmake)

option(FEWGON_ENABLE_TESTS "Enable tests" YES)

if(FEWGON_ENABLE_TESTS)
    include(CTest)
    add_subdirectory(extern/doctest)

    add_library(fewgon_testsuite INTERFACE)
    target_link_libraries(fewgon_testsuite INTERFACE doctest)
    add_library(fewgon::testsuite ALIAS fewgon_testsuite)
endif()

# symlink compile_commands.json
set(CMAKE_EXPORT_COMPILE_COMMANDS YES)
if(CMAKE_EXPORT_COMPILE_COMMANDS)
    add_custom_target(symlink-compile-commands ALL
        ${CMAKE_COMMAND} -E create_symlink
            ${CMAKE_BINARY_DIR}/compile_commands.json
            ${CMAKE_CURRENT_LIST_DIR}/compile_commands.json)
endif()

add_subdirectory(libs/core)
