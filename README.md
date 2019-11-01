# Timber.io Rust toolchain

This is a [Timber.io](https://timber.io) Rust toolchain. It is used to compile
[Vector](http://github.com/timberio/vector) release binaries.

## Main features
* Produces statically-linked binaries for `x86_64` and `armv7` Linux
* Uses `musl` as the standard C library
* Uses `libc++` as the standard C++ library
* Enables cross-language link-time optimization

## Usage

In order to build your project for a given target, run

```sh
docker run -w"$PWD" -v"$PWD":"$PWD" -t timberio/rust-toolchain:1.38.0-armv7-unknown-linux-musl cargo build
```

or just create a shell alias

```sh
alias cargo-armv7='docker run -w"$PWD" -v"$PWD":"$PWD" -t timberio/rust-toolchain:1.38.0-armv7-unknown-linux-musl cargo'
```

in order to be able to run `cargo-armv7 build`, `cargo-armv7 test`, etc.

Note that the tests should work too, although they are compiled for the target platform, with help of user-mode QEMU
installed inside the toolchain image.
