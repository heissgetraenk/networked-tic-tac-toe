cmake_minimum_required(VERSION 3.16)
project(NetworkedTicTacToe)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find Boost ASIO
find_package(Boost REQUIRED COMPONENTS system)

# Add source library
add_library(mylib src/math.cpp)
target_include_directories(mylib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src)
target_link_libraries(mylib PUBLIC Boost::system)

# Enable testing
enable_testing()

# Add Google Test (or your preferred testing framework)
include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/refs/tags/v1.17.0.zip
)
FetchContent_MakeAvailable(googletest)

# Add test executable
add_executable(mylib_test test/test_math.cpp)
target_link_libraries(mylib_test mylib gtest gtest_main)
add_test(NAME MyLibTest COMMAND mylib_test)