# C-DataProcessing

C-DataProcessing is a command-line utility written in C that processes a two-dimensional grid of floating-point numbers for machine learning purposes by replacing or removing invalid values (`nan`). Designed with modular programming principles, this project demonstrates advanced C programming concepts and efficient memory management, making it a robust tool for preprocessing messy data.

## Features
- **Imputation Strategy**: Replace invalid values (`nan`) with the average of valid column values or `0` if the column contains only invalid values.
- **Deletion Strategy**: Remove rows containing invalid values.
- **Flexible Input/Output**: Processes input from standard input and writes cleaned data to standard output.
- **Scalable Design**: Handles grids of any size with dynamic memory allocation.

---

## Key C Concepts Used

1. **Dynamic Memory Allocation**: Uses `malloc` for creating dynamic arrays and `realloc` for resizing during the deletion strategy. Proper memory deallocation with `free` prevents memory leaks.
2. **Pointer Arithmetic**: Handles 2D arrays efficiently using pointers. Demonstrates type casting and dereferencing for grid manipulation.
3. **Modular Programming**: Divides the program into multiple `.c` files and header files for cleaner organization.
4. **Error Handling**: Uses the `<math.h>` function `isnan` to detect invalid values. Handles edge cases gracefully.
5. **Command-Line Arguments**: Implements a `-d` flag to switch between imputation and deletion strategies.

---

## How to Build the Project

### Prerequisites
1. C Compiler (e.g., gcc)
2. Make (build tool)

### Build Instructions
1. Clone the repository:
   `git clone https://github.com/yourusername/C-DataProcessing.git`
   `cd C-DataProcessing`

2. Navigate to the `src/` directory:
   `cd src`

3. Build the project using the provided `Makefile`:
   `make`

4. To clean up generated files, use:
   `make clean`

---

## How to Execute the Program

### Basic Usage
Run the `clean` executable with input data from a file and redirect the output to another file:
`./clean < input.txt > output.txt`

### Deletion Strategy
Use the `-d` flag to clean the data using the deletion strategy:
`./clean -d < input.txt > output.txt`

### Input Format
The input data must follow this format:
- The first line contains two integers: the number of rows (`R`) and columns (`C`).
- The subsequent lines contain `R * C` floating-point numbers (including `nan`).

#### Example Input (`input.txt`):
3 4
nan nan 5.3 1.0
nan 1.8 1.9 nan
nan 2.8 nan nan

### Output Format
The output data will have the same dimensions as the input (imputation strategy) or fewer rows (deletion strategy), with invalid values cleaned.

#### Example Output (Imputation Strategy):
3 4
0.000 2.300 5.300 1.000
0.000 1.800 1.900 1.000
0.000 2.800 3.600 1.000

#### Example Output (Deletion Strategy):
2 4
1.000 1.800 1.900 2.300
0.000 1.200 3.400 5.600

---

## Automated Testing and CI Pipeline

The project includes a CI pipeline configured via GitHub Actions. Every commit triggers:
1. **Build**: Compiles the project using the `Makefile`.
2. **Test**: Runs the `clean` executable on test data (e.g., `wbcd.txt`) and verifies the output.

You can view the CI pipeline configuration in `.github/workflows/ci.yml`.

---

## Contributing
Contributions are welcome! If you have suggestions or want to add features, please:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Commit your changes and push them to your fork.
4. Submit a pull request.
