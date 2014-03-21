project(Enca)
cmake_minimum_required(VERSION 2.8)
aux_source_directory(lib LIB_SRC)
include_directories(. lib)
add_library(enca SHARED ${LIB_SRC})

install(TARGETS enca DESTINATION lib)
install(FILES lib/enca.h DESTINATION include)
