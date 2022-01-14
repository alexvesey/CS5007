cmake_minimum_required(VERSION 3.15)
project(CS5007 VERSION 0.0.1 LANGUAGES CXX)

set(SUBDIRS
    homework1)

foreach(subdir ${SUBDIRS})
  file(GLOB TMP_SOURCES ${subdir}/*.?pp)
  add_executable("${subdir}_cpp" ${TMP_SOURCES})
  install(TARGETS "${subdir}_cpp" RUNTIME DESTINATION ${CMAKE_CURRENT_LIST_DIR}/../install/)
endforeach()