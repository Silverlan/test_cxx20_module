
cmake_minimum_required(VERSION 3.25)

set(CMAKE_EXPERIMENTAL_CXX_IMPORT_STD "d0edc3af-4c50-42ea-a356-e2862fe7a444")
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_MODULE_STD 1)

message(STATUS "CMake version: ${CMAKE_VERSION}")

project(modules_test LANGUAGES CXX)

#add_compile_options(-stdlib=libstdc++)
#add_link_options(-stdlib=libstdc++)

add_library(math STATIC)
target_sources(math
  PUBLIC
    FILE_SET cxx_modules TYPE CXX_MODULES FILES
    src/math.cppm
)
target_compile_features(math PUBLIC cxx_std_23)

add_executable(app src/main.cpp)
target_link_libraries(app PRIVATE math)
