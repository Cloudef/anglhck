CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
project(anglhck)

list(APPEND CMAKE_CXX_FLAGS -std=c++11)

add_subdirectory(lib)

set(AS_ADDONS ${Angelscript_SOURCE_DIR}/../../../add_on/)

add_subdirectory(src)
add_subdirectory(test)
