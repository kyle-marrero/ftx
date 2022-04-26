cmake_minimum_required(VERSION 3.10)
project(ftxclient)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "-Wall -Werror -Wfatal-errors -Wpedantic -Wextra -Wmissing-include-dirs -Wconversion -Wsign-conversion -pthread")

add_compile_options(-Wall -Werror -Wfatal-errors -Wpedantic -Wextra -Wmissing-include-dirs -Wconversion -Wsign-conversion -pthread)

set(CMAKE_CXX_FLAGS_DEBUG "-O0 -march=native -g")

SET(GCC_COVERAGE_COMPILE_FLAGS "-Wno-unused-lambda-capture")

add_definitions(${GCC_COVERAGE_COMPILE_FLAGS})
SET(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}")

add_compile_options(-Wno-unused-lambda-capture)

set(Boost_USE_STATIC_LIBS OFF)
set(Boost_USE_STATIC_RUNTIME OFF)
set(Boost_USE_MULTITHREADED OFF)
set(Boost_INCLUDE_DIR "/usr/local/Cellar/boost/1.78.0_1/include")
find_package(Boost 1.71 REQUIRED)
link_directories(${Boost_LIBRARY_DIRS})
include_directories(SYSTEM ${Boost_INCLUDE_DIR})

find_package(OpenSSL 1.1 REQUIRED)
include_directories(SYSTEM ${OPENSSL_INCLUDE_DIR})

include_directories(src)
include_directories(SYSTEM src/external)

add_subdirectory(src/rest)
add_subdirectory(src/ws)
add_subdirectory(src/util)
add_subdirectory(src/example)



