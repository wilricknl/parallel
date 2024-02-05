# Parallel

GPU parallel program development using CUDA.

### Windows

This project builds out of the box in Visual Studio 2022 with an integrated
installation of vcpkg.

### Linux with CLion

1. Install vcpkg from https://github.com/Microsoft/vcpkg. (I assume it is installed in `~/tools/`)
2. Go to `File -> Settings -> Build, Execution, Deployment -> CMake`.
3. Find `CMake Options`.
4. Insert `-DCMAKE_TOOLCHAIN_FILE=~/tools/vcpkg/scripts/buildsystems/vcpkg.cmake`.
