cmake_minimum_required(VERSION 3.1)
project(libmeow_hash_cpp_test LANGUAGES CXX)

add_executable(testing
	catch.hpp
	meow_hash.h
	testing.cpp
)

target_link_libraries(testing meow_hash_cpp)

# Add test run
add_test(testing testing)
