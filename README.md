# llvm-out-of-tree-pass
Template for an out-of-tree LLVM pass.

Tested with clang-10

## Build
```bash
# modify CMakeLists.txt: add_subdirectory(hello)
# modify hello/hello.cpp
# modify hello/CMakeLists.txt: hello.cpp
mkdir build
cd build
cmake ..
```

## Run
```bash
clang-10 -S -emit-llvm -B test/gold/ld -flto -fsanitize=cfi-icall test/cfi_icall.c -o test/cfi_icall.ll
opt-10 -load build/hello/LLVMHelloWorld.so -helloworld test/cfi_icall.ll 
```
