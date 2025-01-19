project(FEWGON_CORE VERSION 0.0.0)

add_library(fewgon_core INTERFACE)
add_library(fewgon::core ALIAS fewgon_core)

target_include_directories(fewgon_core INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_compile_features(fewgon_core INTERFACE cxx_std_23)

if(FEWGON_ENABLE_TESTS)
    add_subdirectory(tests)
endif()
