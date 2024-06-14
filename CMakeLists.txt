cmake_minimum_required(VERSION 3.10)
project(vulkan_testing VERSION 0.0)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

file(GLOB_RECURSE sources ONFIGURE_DEPENDS "${CMAKE_SOURCE_DIR}/src/*.cpp")

find_library(vulkan_testing glfw vulkan)
link_directories(/usr/local/lib)

add_executable(vulkan_testing ${sources})

if(CMAKE_BUILD_TYPE STREQUAL Release)
    target_compile_definitions(vulkan_testing PRIVATE NDEBUG)
endif()

target_include_directories(vulkan_testing PUBLIC /usr/local/include)
target_link_libraries(vulkan_testing PUBLIC glfw vulkan)
