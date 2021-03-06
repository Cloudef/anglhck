CMAKE_MINIMUM_REQUIRED(VERSION 2.8)
project(anglhck-tests)

include_directories(
  ${kazmath_SOURCE_DIR}/src
  ${glhck_SOURCE_DIR}/include
  ${Angelscript_SOURCE_DIR}/../../include
  ${Angelscript_SOURCE_DIR}/../../../add_on
  ${GLFW_SOURCE_DIR}/include
  ${anglhck_SOURCE_DIR}/include
)

add_subdirectory(lib)

include_directories(
  ${consolehck_SOURCE_DIR}/include
)

add_library(utf8 utf8.c)

add_executable(simple
    simple.cpp
    ${AS_ADDONS}/scriptbuilder/scriptbuilder.cpp
    ${AS_ADDONS}/scripthandle/scripthandle.cpp
    ${AS_ADDONS}/scriptstdstring/scriptstdstring.cpp
)
target_link_libraries(simple anglhck glfw ${GLFW_LIBRARIES})

add_executable(anglhck_run
    anglhck_run.cpp
    ${AS_ADDONS}/scriptbuilder/scriptbuilder.cpp
    ${AS_ADDONS}/scripthandle/scripthandle.cpp
    ${AS_ADDONS}/scriptstdstring/scriptstdstring.cpp
    ${AS_ADDONS}/scriptarray/scriptarray.cpp
    ${AS_ADDONS}/scripthelper/scripthelper.cpp
)
target_link_libraries(anglhck_run anglhck consolehck utf8 glfw ${GLFW_LIBRARIES})


file(COPY scripts DESTINATION .)
file(COPY textures DESTINATION .)
file(COPY models DESTINATION .)
file(COPY fonts DESTINATION .)
