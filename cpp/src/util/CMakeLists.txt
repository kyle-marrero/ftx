file(GLOB SOURCES "*cc")
add_library(util STATIC ${SOURCES})
target_include_directories(util PUBLIC)

target_link_libraries(util OpenSSL::SSL OpenSSL::Crypto)

set(CMAKE_CXX_FLAGS "-Wno-unused-lambda-capture")

add_compile_options("-Wno-unused-lambda-capture")


SET(GCC_COVERAGE_COMPILE_FLAGS "-Wno-unused-lambda-capture")

add_definitions(${GCC_COVERAGE_COMPILE_FLAGS})
SET(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COVERAGE_COMPILE_FLAGS}")
