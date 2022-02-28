# Introduction

OPTIGA™ TPM 2.0 on embedded systems.

# Table of Contents

# Prerequisites

- Tested on Raspberry Pi 4 Model B with Iridium 9670 TPM 2.0 board [[1]](#1) 
- Set up the Raspberry Pi according to [[2]](#2) but skipping section "Set Up TSS and Tools"
- Install dependencies:
    ```
    $ sudo apt install cmake
    ```

# Mbed TLS Library

```
$ git clone https://github.com/ARMmbed/mbedtls ~/mbedtls
$ cd ~/mbedtls
$ git checkout mbedtls-2.28.0
$ cd library/
$ make -j$(nproc)
```

# Decouple Tpm2-tss Library

```
$ git clone https://github.com/tpm2-software/tpm2-tss ~/tpm2-tss
$ cd ~/tpm2-tss
$ git checkout 3.2.0

$ git clone https://github.com/wxleong/tpm2-embedded ~/tpm2-embedded
$ cp -r ~/tpm2-embedded/tpm2-tss/cmake ~/tpm2-tss/
$ cd ~/tpm2-tss/cmake
$ rm -rf CMakeFiles
$ cmake -j$(nproc) .
$ cmake --build . -j$(nproc)
```

# Sample Application

```
$ git clone https://github.com/wxleong/tpm2-mbedtls ~/tpm2-mbedtls
$ cp -f ~/tpm2-embedded/tpm2-mbedtls/Makefile ~/tpm2-mbedtls/code/
$ cd ~/tpm2-mbedtls/code 
$ make -j$(nproc)
$ ./main
```

# License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
