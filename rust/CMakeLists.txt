cmake_minimum_required(VERSION 3.15)
project(CS5007)

SET(SUB_DIRS 
    homework1)

foreach(dir ${SUB_DIRS})    

add_custom_target(
    my_custom_target_that_always_runs ALL
    DEPENDS ${CMAKE_CURRENT_LIST_FILE}/../install/bin/${dir}_rust.exe
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_LIST_FILE}/../install/bin/${dir}_rust.exe
    COMMAND cargo install --path . --root ../../install --no-track --force
    WORKING_DIRECTORY ${CMAKE_CURRENT_LIST_FILE}/../${dir}/
)

endforeach()