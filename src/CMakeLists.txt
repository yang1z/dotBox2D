cmake_policy(SET CMP0167 NEW)
find_package(Boost 1.75 REQUIRED)

# aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} DOT_BOX2D_SOURCE_FILES)
file(GLOB DOT_BOX2D_SOURCE_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/*/*.cpp
)

add_library(dot-box2d ${DOT_BOX2D_SOURCE_FILES})

target_include_directories(dot-box2d
  PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
    # PRIVATE ${BOX2D_SOURCE_DIR}/include
)

target_link_libraries(dot-box2d box2d)

set_target_properties(dot-box2d PROPERTIES
    LINKER_LANGUAGE CXX
    CXX_STANDARD 20
    CXX_STANDARD_REQUIRED YES
    CXX_EXTENSIONS NO
    # VERSION ${PROJECT_VERSION}
    # SOVERSION ${PROJECT_VERSION_MAJOR}
)
