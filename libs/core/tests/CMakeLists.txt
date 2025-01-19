
function(fg_add_simple_test BASENAME)
    add_executable(test.core.${BASENAME} ${BASENAME}.cpp)
    target_link_libraries(test.core.${BASENAME} PRIVATE fewgon::testsuite fewgon::core)
    add_test(NAME "core:${BASENAME}" COMMAND test.core.${BASENAME})
endfunction()

fg_add_simple_test(sanity_check)
