# CMake Commands Cheat Sheet

## Basic Configuration

```cmake
cmake -S . -B build                     # Configure the project in the 'build' directory
cmake -S . -B build -G "Unix Makefiles" # Configure with Unix Makefiles generator
cmake -S . -B build -G "Ninja"          # Configure with Ninja generator
```

## Build Types

```cmake
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug # Configure for debug build
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release # Configure for release build
cmake -S . -B build -DCMAKE_BUILD_TYPE=RelWithDebInfo # Configure for release build with debug info
cmake -S . -B build -DCMAKE_BUILD_TYPE=MinSizeRel # Configure for minimum size release
```

## Compiler Selection

```cmake
cmake -S . -B build -DCMAKE_CXX_COMPILER=/usr/bin/g++ # Use g++ as C++ compiler
cmake -S . -B build -DCMAKE_CXX_COMPILER=/usr/bin/clang++ # Use clang++ as C++ compiler
cmake -S . -B build -DCMAKE_C_COMPILER=/usr/bin/gcc # Use gcc as C compiler
cmake -S . -B build -DCMAKE_C_COMPILER=/usr/bin/clang # Use clang as C compiler
```

## Compilation Flags

```cmake
cmake -S . -B build -DCMAKE_CXX_FLAGS="-Wall -Wextra -pedantic" # Set C++ compilation flags
cmake -S . -B build -DCMAKE_C_FLAGS="-Wall -Wextra -pedantic" # Set C compilation flags
```

## Installation

```cmake
cmake -S . -B build -DCMAKE_INSTALL_PREFIX=/usr/local # Set installation prefix to /usr/local
cmake -S . -B build -DCMAKE_INSTALL_PREFIX=$HOME/.local # Set installation prefix to user's local directory
```

## Library Search Paths

```cmake
cmake -S . -B build -DCMAKE_PREFIX_PATH="/opt/qt5;/opt/boost" # Specify additional paths to search for libraries
```

## Library Types

```cmake
cmake -S . -B build -DBUILD_SHARED_LIBS=ON # Build shared libraries
cmake -S . -B build -DBUILD_SHARED_LIBS=OFF # Build static libraries
```

## IDE and Linter Support

```cmake
cmake -S . -B build -DCMAKE_EXPORT_COMPILE_COMMANDS=ON # Generate compile_commands.json for IDE and linter support
```

## Position Independent Code

```cmake
cmake -S . -B build -DCMAKE_POSITION_INDEPENDENT_CODE=ON # Generate position-independent code
```

## Verbose Build Output

```cmake
cmake -S . -B build -DCMAKE_VERBOSE_MAKEFILE=ON # Enable verbose output during build
```

## Advanced Configuration

```cmake
cmake -S . -B build -G "Ninja" -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_COMPILER=/usr/bin/clang++ -DCMAKE_CXX_FLAGS="-Wall -Wextra" -DBUILD_SHARED_LIBS=ON -DCMAKE_INSTALL_PREFIX=/opt/myapp # Complex configuration example
```

## Toolchain Usage

```cmake
cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE=/path/to/toolchain.cmake # Use a specific toolchain file
cmake --toolchain /home/user/my-toolchain.cmake . # Alternative toolchain specification
```

## Testing

```cmake
cmake -S . -B build -DBUILD_TESTING=ON # Enable testing
```

## Parallel Build

```cmake
cmake -S . -B build && cmake --build build -- -j$(nproc) # Configure and build using all available cores
```

## Cache Management

```cmake
cmake -S . -B build -UCMAKE_INSTALL_PREFIX -DCMAKE_INSTALL_PREFIX=/new/path # Unset a cached variable and set a new value
cmake -S . -B build -C /path/to/initial-cache.cmake # Load initial cache file
```

## Sanitizers

```cmake
cmake -S . -B build -DCMAKE_CXX_FLAGS="-fsanitize=address,undefined" # Enable Address and Undefined Behavior Sanitizers
```

## Dependency Graph Generation

```cmake
cmake -S . -B build --graphviz=deps.dot # Generate a graphviz file of the dependency graph
```

## Presets

```cmake
cmake --preset debug . # Use debug preset
cmake --preset release . # Use release preset
cmake --list-presets # List available presets
```

## Fresh Configuration

```cmake
cmake --fresh . # Start a fresh configuration, ignoring previous cache
```

## Build Commands

```cmake
cmake --build ./build # Build the project
cmake --build ./build --config Debug # Build the project in Debug configuration
cmake --build ./build --config Release # Build the project in Release configuration
```

## Installation Commands

```cmake
cmake --install ./build # Install the project
cmake --install ./build --prefix /usr/local # Install the project with a specific prefix
```

## Configuration Inspection

```cmake
cmake -N . # View configuration without executing commands
```

## Logging Levels

```cmake
cmake --log-level=ERROR . # Set log level to ERROR
cmake --log-level=WARNING . # Set log level to WARNING
cmake --log-level=NOTICE . # Set log level to NOTICE
cmake --log-level=STATUS . # Set log level to STATUS
cmake --log-level=VERBOSE . # Set log level to VERBOSE
cmake --log-level=DEBUG . # Set log level to DEBUG
cmake --log-level=TRACE . # Set log level to TRACE
```

## Tracing

```cmake
cmake --trace . # Enable tracing of all commands
cmake --trace-expand . # Enable tracing with variable expansion
```

## Combined Examples

```cmake
cmake -Wdev --fresh --log-level=DEBUG . # Fresh configuration with developer warnings and debug logging
cmake --toolchain /path/to/toolchain.cmake --install-prefix /opt/myapp --preset release . # Use toolchain, set install prefix, and use release preset
cmake --build ./build --config Release -- -j$(nproc) # Build in Release config using all cores
cmake --install ./build --prefix /opt/myapp --strip # Install with stripping symbols
```

## Large Project Example

```cmake
cmake -S . -B build -G "Ninja" --preset=release --log-level=VERBOSE # Configure large project
cmake --build build --config Release --parallel 8 # Build large project using 8 cores
cmake --install build --prefix /opt/myapp --strip # Install large project
```

## CMake Script Debugging

```cmake
cmake -P my_script.cmake --trace-expand --log-level=TRACE # Debug a CMake script
```

## Dry Run Configuration

```cmake
cmake -N --preset=debug . # Check debug configuration without building
```

## Cross-Compilation

```cmake
cmake -S . -B build -DCMAKE_TOOLCHAIN_FILE=/path/to/cross-toolchain.cmake # Configure for cross-compilation
```

## Packaging with CPack

```cmake
cmake -S . -B build -DCPACK_GENERATOR="DEB;RPM" # Configure for DEB and RPM package generation
cpack --config ./build/CPackConfig.cmake # Generate packages
```

## Code Coverage

```cmake
cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug -DENABLE_COVERAGE=ON # Configure for code coverage analysis
```

## Using CMake with Docker

```cmake
docker run --rm -v $(pwd):/src -w /src cmake cmake -S . -B build # Run CMake in a Docker container
```

## Specifying C++ Standard

```cmake
cmake -S . -B build -DCMAKE_CXX_STANDARD=17 -DCMAKE_CXX_STANDARD_REQUIRED=ON # Use C++17 and require it
```

## Using ccache

```cmake
cmake -S . -B build -DCMAKE_CXX_COMPILER_LAUNCHER=ccache # Use ccache to speed up repeated builds
```
