cmake_minimum_required(VERSION 3.3 FATAL_ERROR)
project(Include LANGUAGES CXX)
add_executable(hello main.cpp mylib.cpp)

find_program(iwyu_path NAMES include-what-you-use iwyu REQUIRED)

# If using CGAL<3.18, you remove REQUIRED and use
# if(NOT iwyu_path)
#   message(FATAL_ERROR "Could not find the program include-what-you-use")
# endif()

set_property(TARGET hello PROPERTY CXX_INCLUDE_WHAT_YOU_USE ${iwyu_path})