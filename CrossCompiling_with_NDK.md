# CrossCompiling Cmake projects with Android NDK

CMake projects can be cross compiled easily with Android NDK to run it
on android devices, BUT:

- NDK STL is different form AOSP STL, so you can't cross compile some
    library with NDK and add it as a prebuilt library in AOSP and hope
    to write application against that library

    If you see linker error for a missing function signature because
    the namespace for STL objects are different.

- NDK uses std::__ndk1::
- AOSP uses std::__1::

## How to ?

Same steps as any CMake projects,

- make a buld folder
- change dir
- insted of just ``` cmake .. ``` we use 

```sh
cmake .. \
  -DCMAKE_SYSTEM_NAME=Android \
  -DCMAKE_SYSTEM_VERSION=31 \
  -DCMAKE_ANDROID_ARCH_ABI=arm64-v8a \
  -DCMAKE_ANDROID_NDK=<path-to-androidNDK> \
  -DCMAKE_INSTALL_PREFIX=<path-to-install-dir>
```

Fast-DDS uses ifaddrs which is only available after API level 22 or so

If all goes well you can find the shared libs `fastdds.so` and
`fastcdr.so` in the `INSTALL_PREFIX` passed as argument
