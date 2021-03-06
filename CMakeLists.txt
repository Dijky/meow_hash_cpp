# CMake 3.3 required for INTERFACE install() support
cmake_minimum_required(VERSION 3.3)
project(libmeow_hash_cpp VERSION 0.1.0 LANGUAGES CXX)

# Setup build type
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

# Set general C++ flags
set(CMAKE_CXX_FLAGS "-Wall -Wextra")

# Set optimization/debug flags
set(CMAKE_CXX_FLAGS_DEBUG "-g")
set(CMAKE_CXX_FLAGS_RELEASE "-O3")

# Add header-only library
add_library(meow_hash_cpp INTERFACE)
target_sources(meow_hash_cpp INTERFACE ${PROJECT_SOURCE_DIR}/include/meow_hash.hpp)

# Specify include directories for build and install
target_include_directories(meow_hash_cpp INTERFACE
	$<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}/include>
	$<INSTALL_INTERFACE:include>
)

# Require C++17 compilation
target_compile_features(meow_hash_cpp INTERFACE cxx_std_17)

# Add tests
enable_testing()
add_subdirectory(test)
