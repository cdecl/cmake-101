cmake_minimum_required(VERSION 3.5)

project(main)

#add_subdirectory(/subdir)

add_compile_options( -Wall -std=c++14 -O2 )

# include_directories( )
# link_directories( )
# link_libraries( pthread )
# link_libraries( -static -static-libstdc++ )
# link_libraries( -Wl,--whole-archive -lpthread -Wl,--no-whole-archive )

# set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

file(GLOB src "*.cpp")
#set(src xxx.cpp)

add_executable(main ${src})
# add_library(libname SHARED ${src})

# set(CMAKE_INSTALL_PREFIX ..)
# install (TARGETS main)
