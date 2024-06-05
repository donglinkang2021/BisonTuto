cmake_minimum_required(VERSION 3.16) 
project(simple_cpp) 
set(CMAKE_CXX_STANDARD 14) 
add_compile_options(-pedantic) 
# Add subdirectories

add_subdirectory(parse)

# Add the binary and sources
add_executable(
  parser
  main.cpp
)

target_link_libraries(parser parse)
