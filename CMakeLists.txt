cmake_minimum_required(VERSION 3.10)

project(Tutorial VERSION 1.0)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# add the MathFunctions library
add_subdirectory(MathFunctions)

add_executable(Tutorial src/tutorial.cpp)

target_link_libraries(Tutorial PUBLIC MathFunctions)

#Adding a Version Number and Configured Header File¶
configure_file(include/TutorialConfig.h.in TutorialConfig.h)

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
target_include_directories(Tutorial PUBLIC
                          "${PROJECT_BINARY_DIR}"
                          "${PROJECT_SOURCE_DIR}/MathFunctions"
                          )