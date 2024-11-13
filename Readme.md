# Fast-DDS for AOSP

This repo contains build files(Android.bp) for adding Fast-DDS project
and its dependencies to AOSP build system.

## Tree

```sh
.
├── asio/*
├── Fast-CDR
│   └── Android.bp
├── Fast-DDS
│   └── Android.bp
├── memory
│   └── Android.bp
└── Readme.md

3 directories, 5 files
```

Each folder contains the corresponding `Android.bp` file for the project.Simple copy these files to your clone, add names to `PRODUCT_PACKAGES` in your device.mk file.

Asio is a header only lib export, source is included or reuse the
`Android.bp` file with a newer clone.

## FYI

- Make changes to fit your build.
- Some header files are generated from .ini files by cmake,
    don't know there is rule in Android.bp that have the same
    effect.I cross compiled with NDK and stole the missing 
    header form the build folder.
- There could be unsuported data types like float 128,
    some minor code changes are done here and there to get this
    to build.

## Refs

- Future me add links to
- [CrossCompiling](www.placeholder.scom) FastDDS with Android NDK