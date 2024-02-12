cmake_minimum_required(VERSION 3.21)

set(parallel_VERSION 0.1.0)

project(parallel
        VERSION ${parallel_VERSION}
        DESCRIPTION "GPU parallel program development using CUDA"
        HOMEPAGE_URL "https://github.com/wilricknl/parallel"
        LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 20)

include(CMakePackageConfigHelpers)
include(GNUInstallDirs)

## Interpret source as utf-8 on Windows to ensure
## non-ascii characters are read properly.
add_compile_options("$<$<C_COMPILER_ID:MSVC>:/utf-8>")
add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/utf-8>")

## Static builds on Windows
if (MSVC)
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
endif()

# -----------------------------------------------------------------------------
# DEPENDENCIES
# -----------------------------------------------------------------------------

include_directories(include)

# -----------------------------------------------------------------------------
# EXECUTABLES
# -----------------------------------------------------------------------------

# chapter 1: serial image flip
add_executable(
    image_flip
    src/image_flip/image_stuff.c
    src/image_flip/main.c)

# chapter 2: parallel image flip
add_executable(
        image_flip_parallel
        src/image_flip_parallel/image_stuff.c
        src/image_flip_parallel/main.c)

# -----------------------------------------------------------------------------
# TEST
# -----------------------------------------------------------------------------
