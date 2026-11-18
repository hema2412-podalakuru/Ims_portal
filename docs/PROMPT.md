# Prompt: Generate the C++ CI Project

Copy the text below into an AI coding assistant to generate this project from scratch.

---

Create a minimal C++17 project with a CMake build and a GitHub Actions CI pipeline.

## Project layout

```
CPPProject/
├── CMakeLists.txt
├── src/main.cpp
├── test/test_main.cpp
└── .github/workflows/ci.yml
```

## Requirements

### 1. Application (`src/main.cpp`)
- Print `CI/CD Pipeline Working!` to standard output and return 0.

### 2. Tests (`test/test_main.cpp`)
- Use `<cassert>` to check that `2 + 2 == 4`.
- Return 0 when the check passes.

### 3. CMake (`CMakeLists.txt`)
- Require CMake 3.10 or newer.
- Name the project `MyProject` and use C++17.
- Build an executable `MyProject` from `src/main.cpp`.
- Call `enable_testing()`.
- Build a second executable `MyTest` from `test/test_main.cpp`.
- Register a CTest test named `MyTest` that runs the `MyTest` executable.
- Use `#` for all comments.

### 4. CI (`.github/workflows/ci.yml`)
- Name the workflow `C++ CI`.
- Trigger on pushes and pull requests to `main`.
- Run on `windows-latest`.
- Steps, in order:
  1. Check out the code with `actions/checkout@v4`.
  2. Install CMake.
  3. Configure: `cmake -S . -B build`.
  4. Build: `cmake --build build --config Release`.
  5. Run the tests: `ctest --test-dir build -C Release --output-on-failure`.
  6. Run the application: `build\Release\MyProject.exe`.

## Acceptance criteria
- `cmake -S . -B build` configures without errors.
- `cmake --build build` builds both executables.
- `ctest --test-dir build` passes.
- Running `MyProject` prints `CI/CD Pipeline Working!`.
