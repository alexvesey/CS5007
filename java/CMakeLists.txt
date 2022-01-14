cmake_minimum_required(VERSION 3.15)
project(CS5007)

find_package(Java REQUIRED COMPONENTS Runtime Development)
include(UseJava)

SET(SUB_DIRS 
    homework1)

foreach(dir ${SUB_DIRS})
    
add_custom_target(
    my_custom_target_that_always_runs ALL
    DEPENDS ${CMAKE_CURRENT_LIST_FILE}/../../build_java/${dir}.class
    DEPENDS ${CMAKE_CURRENT_LIST_FILE}/../../install/${dir}.class
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_LIST_FILE}/../../build_java/${dir}.class
    COMMAND "${Java_JAVAC_EXECUTABLE}" -d .  ../java/homework1/${dir}.java
)

add_custom_command(
    OUTPUT ${CMAKE_CURRENT_LIST_FILE}/../../install/${dir}.class
    COMMAND ${CMAKE_COMMAND} -E copy  ${dir}.class ../install
)

endforeach(dir ${SUB_DIRS})