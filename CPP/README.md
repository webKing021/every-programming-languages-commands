# C++ Commands Reference

## Compilation and Execution

### Basic Compilation
```bash
# Compile a single file
g++ filename.cpp -o executable_name

# Compile with C++11 standard
g++ -std=c++11 filename.cpp -o executable_name

# Compile with C++14 standard
g++ -std=c++14 filename.cpp -o executable_name

# Compile with C++17 standard
g++ -std=c++17 filename.cpp -o executable_name

# Compile with C++20 standard
g++ -std=c++20 filename.cpp -o executable_name

# Compile with warnings
g++ -Wall filename.cpp -o executable_name

# Compile with all warnings and debug information
g++ -Wall -g filename.cpp -o executable_name

# Compile multiple files
g++ file1.cpp file2.cpp -o executable_name
```

### Execution
```bash
# Run the executable (Linux/Mac)
./executable_name

# Run the executable (Windows)
executable_name.exe
```

### Using Clang Compiler
```bash
# Compile with clang
clang++ filename.cpp -o executable_name

# Compile with specific standard
clang++ -std=c++17 filename.cpp -o executable_name
```

## Build Systems

### Make Commands
```bash
# Build with make
make

# Build specific target
make target_name

# Clean build files
make clean
```

### CMake Commands
```bash
# Create build directory
mkdir build && cd build

# Generate build files
cmake ..

# Build the project
cmake --build .

# Build specific configuration
cmake --build . --config Release
```

## Debugging

### GDB Commands
```bash
# Start debugging
gdb executable_name

# Set breakpoint
break filename.cpp:line_number

# Run program
run

# Continue execution
continue

# Step into function
step

# Step over function
next

# Print variable value
print variable_name

# Display variable value (updates automatically)
display variable_name

# Show backtrace
bt

# Quit debugger
quit
```

### Valgrind Commands
```bash
# Check for memory leaks
valgrind --leak-check=full ./executable_name

# Detailed memory analysis
valgrind --tool=memcheck --leak-check=yes --show-reachable=yes ./executable_name
```

## Package Management

### Conan Commands
```bash
# Install packages
conan install .

# Create package
conan create . user/channel

# Search for packages
conan search package_name
```

### vcpkg Commands
```bash
# Install package
vcpkg install package_name

# List installed packages
vcpkg list

# Update packages
vcpkg update
```

## Static Analysis

### Cppcheck Commands
```bash
# Basic analysis
cppcheck filename.cpp

# Check all errors
cppcheck --enable=all filename.cpp

# Check directory
cppcheck directory_name/
```

### Clang-Tidy Commands
```bash
# Basic analysis
clang-tidy filename.cpp

# With specific checks
clang-tidy filename.cpp -checks=*,-clang-analyzer-*
```

## Documentation

### Doxygen Commands
```bash
# Generate configuration file
doxygen -g

# Generate documentation
doxygen Doxyfile
```

## Profiling

### gprof Commands
```bash
# Compile with profiling info
g++ -pg filename.cpp -o executable_name

# Run the program
./executable_name

# Generate profiling report
gprof executable_name gmon.out > analysis.txt
```

## Code Formatting

### Clang-Format Commands
```bash
# Format a file
clang-format -i filename.cpp

# Format with specific style
clang-format -style=llvm -i filename.cpp

# Format all files in directory
find . -name "*.cpp" -o -name "*.h" | xargs clang-format -i
```