# Fibonacci C Implementation

A recursive implementation of the Fibonacci sequence in C demonstrating classic algorithm design patterns.

## Features

- **Recursive Algorithm**: Classic recursive approach for educational purposes
- **Simple Implementation**: Clean, readable C code
- **Educational Value**: Demonstrates recursive function design and time complexity concepts
- **Portable Code**: Standard C implementation that works across platforms

## Prerequisites

- **C Compiler**: GCC, Clang, or any standard C compiler
- **Make** (optional, for build automation)

### Installing Prerequisites

#### Windows
- Install [MinGW-w64](https://www.mingw-w64.org/) or [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022)
- Or use [Dev-C++](https://sourceforge.net/projects/orwelldevcpp/) for a complete IDE

#### macOS
```bash
# Install Xcode Command Line Tools
xcode-select --install

# Or install via Homebrew
brew install gcc
```

#### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install gcc make
```

#### Linux (CentOS/RHEL/Fedora)
```bash
# CentOS/RHEL
sudo yum install gcc make

# Fedora
sudo dnf install gcc make
```

## Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd fibonacci-c
   ```

## Usage

### Compiling the Code

To compile the C code:

```bash
# Basic compilation
gcc -o fibonacci fibonacci.c

# With debugging information
gcc -g -o fibonacci fibonacci.c

# With optimization
gcc -O2 -o fibonacci fibonacci.c
```

### Running the Program

Currently, the project contains a `fibonacci()` function that can be called from other code. To use it, you'll need to create a main program or integrate it into your project.

Example usage in a main program:
```c
#include <stdio.h>

// Include the fibonacci function
long long fibonacci(int n);

int main() {
    int n = 10;
    printf("Fibonacci of %d is: %lld\n", n, fibonacci(n));
    return 0;
}
```

## Code Structure

### Main Function

The `fibonacci(int n)` function:
- Takes an integer parameter `n`
- Returns the nth Fibonacci number as a `long long`
- Uses recursive approach following the mathematical definition
- Base cases: returns `n` when `n <= 1`

### Example Usage

```c
fibonacci(0);  // Returns: 0
fibonacci(1);  // Returns: 1
fibonacci(5);  // Returns: 5
fibonacci(10); // Returns: 55
```

### Current Limitations

⚠️ **Performance Warning**: The current implementation uses naive recursion and has exponential time complexity. For large values of `n` (>40), the function will be very slow.

## Performance Characteristics

| Algorithm | Time Complexity | Space Complexity | fibonacci(40) |
|-----------|----------------|------------------|---------------|
| Naive Recursion (Current) | O(2^n) | O(n) | ~Several seconds |
| Iterative (Potential) | O(n) | O(1) | ~0.001 seconds |
| Memoized Recursion | O(n) | O(n) | ~0.001 seconds |

## Development

### Project Structure

```
fibonacci-c/
├── fibonacci.c      # Main C implementation
├── LICENSE         # MIT License
└── README.md       # This file
```

### Compilation Flags

Recommended compilation flags:
- `-Wall`: Enable all warnings
- `-Wextra`: Enable extra warnings
- `-std=c99`: Use C99 standard
- `-O2`: Enable optimization level 2
- `-g`: Include debugging information

Example:
```bash
gcc -Wall -Wextra -std=c99 -O2 -g -o fibonacci fibonacci.c
```

### Testing

To test the function with different inputs:

```bash
# Create a test program
cat > test_fibonacci.c << 'EOF'
#include <stdio.h>
#include <time.h>

// Include the fibonacci function
long long fibonacci(int n);

int main() {
    int test_cases[] = {0, 1, 5, 10, 20, 30};
    int num_tests = sizeof(test_cases) / sizeof(test_cases[0]);
    
    for (int i = 0; i < num_tests; i++) {
        clock_t start = clock();
        long long result = fibonacci(test_cases[i]);
        clock_t end = clock();
        
        double time_taken = ((double)(end - start)) / CLOCKS_PER_SEC;
        printf("fibonacci(%d) = %lld (took %.6f seconds)\n", 
               test_cases[i], result, time_taken);
    }
    
    return 0;
}
EOF

# Compile with both files
gcc -o test_fibonacci fibonacci.c test_fibonacci.c

# Run the test
./test_fibonacci
```

## Potential Improvements

The current implementation could be enhanced with:

1. **Iterative Approach**: For better performance
2. **Memoization**: To cache previously computed values
3. **Input Validation**: To handle edge cases and invalid inputs
4. **Error Handling**: For overflow conditions
5. **Main Program**: Complete executable with user input

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test your implementation
5. Submit a pull request

## Additional Information

This implementation demonstrates:
- Classic recursive algorithm design
- Time complexity implications of naive recursion
- Basic C programming concepts
- Function design patterns

**Note**: This is an educational implementation. For production use, consider implementing an iterative version or adding memoization for better performance.