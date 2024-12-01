cmake_minimum_required(VERSION 3.19.0)
message(STATUS "CMake version: ${CMAKE_VERSION}")

enable_language(CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O2")

project(main CXX)
file(GLOB cpu_source_files "${CMAKE_SOURCE_DIR}/src/*.cpp")

find_package(Vulkan REQUIRED)

add_executable(${PROJECT_NAME} ${cpu_source_files})

target_include_directories(${PROJECT_NAME} PRIVATE ${Vulkan_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} Vulkan::Vulkan glfw)