cmake_minimum_required(VERSION 3.5)

add_compile_options(-Wall -Wextra -Wpedantic -Wno-unknown-pragmas -Wno-unused-parameter -Iinclude -O3 -ffast-math -flto)

project(out)

set(CMAKE_CXX_STANDARD 17)

set(INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include/)

set(EXECUTABLE_NAME "out")
set(SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src)

file(GLOB_RECURSE SRCS
    "src/*.cpp"
    RELATIVE_PATH
)




#-- Add SFML ---#
# Link SFML statically
set(SFML_STATIC_LIBRARIES TRUE)
# Where SFML is located
# set(SFML_DIR "./dep/SFML/lib/cmake/SFML")
# set(SFML_DIR ${CMAKE_CURRENT_SOURCE_DIR}/dep/SFML/cmake)

# find_package(SFML COMPONENTS graphics window system REQUIRED)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/dep/SFML)

#--- Compile Output ---#
add_executable(out ${SRCS})
target_include_directories(out PUBLIC ${INCLUDE_DIR})
target_link_libraries(out sfml-graphics sfml-window sfml-system)
