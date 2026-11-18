# Create CMake project
# Use C++17
# Build executable from src/main.cpp

cmake_minimum_required(VERSION 3.10)
project(MyProject)
set(CMAKE_CXX_STANDARD 17)
add_executable(MyProject src/main.cpp)

# Add test execution as well
enable_testing()

# Add test executable
add_executable(MyTest test/test_main.cpp)
add_test(NAME MyTest COMMAND MyTest)
