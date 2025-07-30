# Minimum CMake version required
cmake_minimum_required(VERSION 3.10)

# Project name and languages
project(SavitzkyGolayFilter LANGUAGES C CXX)

# Set C and C++ standards
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Ensure Cygwin runtime linkage for all targets
if (CYGWIN)
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -lc -lcygwin")
    set(CMAKE_SHARED_LINKER_FLAGS "${CMAKE_SHARED_LINKER_FLAGS} -lc -lcygwin")
    set(CMAKE_STATIC_LINKER_FLAGS "${CMAKE_STATIC_LINKER_FLAGS} -lc -lcygwin")
endif()

add_library(SG_filter STATIC src/iterative/savgolFilter.c)
target_include_directories(SG_filter PUBLIC include/iterative)