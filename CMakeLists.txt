project(Enca)
cmake_minimum_required(VERSION 2.8)

include(CheckIncludeFile)
check_include_file(memory.h HAVE_MEMORY_H)
check_include_file(strings.h HAVE_STRINGS_H)
check_include_file(string.h HAVE_STRING_H)

include (CheckFunctionExists)
check_function_exists(strstr HAVE_STRSTR)
check_function_exists(strcpy HAVE_STRCPY)

add_definitions(-DHAVE_CONFIG_H)
configure_file(config.h.in config.h)

aux_source_directory(lib LIB_SRC)
include_directories(. lib ${CMAKE_BINARY_DIR})
add_library(enca SHARED ${LIB_SRC})

install(TARGETS enca DESTINATION lib)
install(FILES lib/enca.h DESTINATION include)
