# CPPProject

A minimal C++17 project that demonstrates a CMake build and a GitHub Actions CI pipeline.

## Structure

```
CPPProject/
├── CMakeLists.txt            # Build configuration
├── src/main.cpp              # Application entry point
├── test/test_main.cpp        # Test executable source (simple assert)
├── .github/workflows/ci.yml  # CI pipeline (Windows)
├── .vscode/launch.json       # VS Code debug configuration
└── docs/PROJECT.md           # This document
```

## Components

- **Application** (`src/main.cpp`): prints `CI/CD Pipeline Working!` and exits with code 0.
- **Tests** (`test/test_main.cpp`): checks `2 + 2 == 4` with `assert` and returns 0.
- **Build** (`CMakeLists.txt`): CMake 3.10+, C++17. Defines the `MyProject` executable and a `MyTest` target, and registers a CTest test named `MyTest` that runs the `MyTest` executable.
- **CI** (`.github/workflows/ci.yml`): runs on pushes and pull requests to `main`, on `windows-latest`. It installs CMake, configures, builds in Release, and runs `build\Release\MyProject.exe`.

## Building and running

```bash
cmake -S . -B build
cmake --build build --config Release
./build/MyProject          # on Windows: build\Release\MyProject.exe
```

Run the tests with:

```bash
ctest --test-dir build -C Release
```

## Known issues

- The CI workflow runs the application but not the tests, and uses the outdated `actions/checkout@v2`.
