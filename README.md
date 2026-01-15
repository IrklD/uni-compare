Here is the updated `README.md`. I have added all the new features found in your code: **Argument support** (using quotes), **Valgrind memory checks**, **Custom output directories**, and **Timeouts**.

I also updated the "Results Structure" section because your code now saves files with suffixes like `_output.txt` and `_valgrind.txt` instead of the old naming convention.

```markdown
# UniCompare


```

---

/ / / /___  () ***/***  ____ ___  ____  ____ _________
/ / / / __ / / /   / __ / __ `__ \/ __ \/ __ `/ / _

/ // / / / / / // // / / / / / / /*/ / /*/ / /  /  **/
_***/*/ /*/*/_***/_***/*/ /*/ /*/ .***/_*,*/*/   ___/
/*/

```

A simple program to help university students manage their coursework. Given 2 executable files, it will run them and compare their outputs with the given input file/s.

## Features

- ✅ **Compare outputs** of two executable programs
- 🚀 **Argument Support**: Pass command-line arguments to your executables (e.g., `"./prog 10 20"`)
- 🧠 **Memory Leak Detection**: Integration with **Valgrind** to check for memory leaks
- 📁 **Recursive Traversal**: Search directories with configurable depth (default: 5 levels)
- ⏱️ **Timeout Protection**: Automatically kills programs that run too long (default: 5s)
- 💾 **Custom Output Location**: Choose where to save your test results
- 🔍 **Smart Duplicates**: Handles duplicate filenames in different directories
- 🔄 **Cross-platform**: Support for Windows/Linux (WSL recommended for Valgrind)
- 📊 **Visual Diff**: Automatic integration with Beyond Compare

## Installation

### 1. Python Dependencies
Run the following to install required packages:
```bash
pip install colorama pyfiglet

```

### 2. Beyond Compare (Optional)

For visual diff functionality:

* **Windows:** [Download here](https://www.scootersoftware.com/download.php) (Default: `C:\Program Files\Beyond Compare 4`)
* **Linux:** `sudo apt install bcompare`

### 3. Valgrind (Optional)

Required only if you want to use the Memory Check feature (`--valgrind`):

* **Linux/WSL:** `sudo apt install valgrind`
* **Windows:** Not supported natively; please use WSL (Ubuntu).

## Usage

### Basic Syntax

```bash
unic <executable1> <executable2> --files <input_files...> [options]

```

### Examples

#### 1. Standard Comparison

Compare two programs using a single input file:

```bash
unic program1.exe program2.exe --files input.txt

```

#### 2. Passing Arguments to Programs (New!)

If your program requires arguments (e.g., `./a.out 100 17`), wrap the command in quotes:

```bash
unic "./solution1 100 17" "./solution2 100 17" -f input.txt

```

#### 3. Memory Check with Valgrind

Run tests and check for memory leaks at the same time:

```bash
unic ./prog1 ./prog2 -f tests/ --valgrind

```

#### 4. Recursive Directory Search

Recursively search for `.txt` files in a folder:

```bash
unic ./prog1 ./prog2 -f tests/

```

#### 5. Custom Output Folder and Timeout

Save results to `my_results` and set timeout to 2 seconds:

```bash
unic ./prog1 ./prog2 -f input.txt --output my_results --timeout 2

```

## Output Examples

### Successful Run

```
==========================================
Running tests on 3 file(s)...
==========================================

[✓] tests/basic/input1.txt
[✓] tests/basic/input2.txt
[✓] tests/edge/special.txt

==========================================
All tests passed! No mismatches found.
==========================================

```

### Run with Errors (Mismatches & Memory Leaks)

```
[✓] tests/basic/simple.txt
[✗] tests/advanced/hard.txt (Output Mismatch)
[M] tests/memory/leak_test.txt (Memory Error)
    ↳ Memory leaks in Exec 1
[T] tests/infinite_loop.txt (Timeout)

==========================================
Results saved in uniTestResults/ folder
==========================================

```

## File Organization

### Results Structure

By default, results are saved in `uniTestResults/` (configurable via `--output`).

When a test fails, UniCompare saves:

1. **Output files:** The standard output of both programs.
2. **Valgrind logs:** (If `--valgrind` was used) The memory report.

```
uniTestResults/
├── tests/advanced/hard.txt/
│   ├── prog1_output.txt        # Output from first executable
│   └── prog2_output.txt        # Output from second executable
└── tests/memory/leak_test.txt/
    ├── prog1_output.txt
    ├── prog2_output.txt
    └── prog1_valgrind.txt      # Memory leak report for prog1

```

## Command Line Arguments

| Argument | Flag | Description | Default |
| --- | --- | --- | --- |
| `exec1` | N/A | Path to first executable (quote if using args) | Required |
| `exec2` | N/A | Path to second executable (quote if using args) | Required |
| `--files` | `-f` | List of input files or directories | Required |
| `--output` | `-o` | Directory to save results | `uniTestResults` |
| `--valgrind` | `-v` | Enable memory leak detection | `False` |
| `--timeout` | `-t` | Timeout in seconds per test | `5.0` |
| `--max-depth` | `-d` | Max recursion depth for directories | `5` |

## Interactive Mode

If mismatches are found, the program enters interactive mode:

```
Which input file would you like to view the differences for?
(Type 'exit' to quit)
Available files:
  - hard.txt
  - leak_test.txt

Enter filename: hard.txt

```

* **Select a file:** Opens the outputs in **Beyond Compare**.
* **Exit:** Type `exit` to close.

## Authors

Naor Biton (5'7 160lbs lean 12% bf)
Denis Irkl (6'1 180lbs lean btw)
Claude Sonnet 4 & Github Copilot Pro ❤️

---

*Made for university students who need to compare program outputs efficiently.*

```

```