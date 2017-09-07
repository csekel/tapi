# TAPI

TAPI is a **T**ext-based **A**pplication **P**rogramming **I**nterface. It
replaces the Mach-O Dynamic Library Stub files in Apple's SDKs to reduce SDK
size even further.

The text-based dynamic library stub file format (.tbd) is a human readable and
editable YAML text file. The _TAPI_ projects uses the _LLVM_ YAML parser to read
those files and provides this functionality to the linker as a dynamic library.


## Building TAPI

TAPI is a _CLANG_ project and requires the _LLVM_ and _CLANG_ sources to
compile.

Create a separate build directory and configure the project with CMake:

    cmake -G Ninja -C <src_dir>/tapi/cmake/caches/apple-tapi.cmake -DCMAKE_INSTALL_PREFIX=<install_dir> -DLLVM_ENABLE_PROJECTS="clang;tapi" <src_dir>/llvm

The CMake cache file defines most of the settings for you, such as enabling LTO,
etc. It also specifies the distribution components to include all the files
needed for TAPI.

To build and install the _TAPI_ project invoke:

    ninja install-distribution

in the build directory.
