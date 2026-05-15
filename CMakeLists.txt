# Create CMake project
# Use C++17
# Build executable from src/main.cpp

cmake_minimum_required(VERSION 3.10)
project(MyProject)
set(CMAKE_CXX_STANDARD 17)
add_executable(MyProject src/main.cpp)

// add test execution as well
enable_testing()
add_test(NAME MyTest COMMAND MyProject)


# Add test executable
add_executable(MyTest test/testmain.cpp)
