# clairvoyant-compiler

This is the RISC-V C and C++ cross-compiler for [clairvoyant](https://github.com/kagandikmen/clairvoyant), a RISC-V core enhanced with a super-resolution unit with its own custom instructions. clairvoyant-compiler, which is there to provide support for these custom instructions, is nothing else than a slightly modified version of [RISC-V GNU Toolchain](https://github.com/riscv-collab/riscv-gnu-toolchain).

##  Getting the sources

This repository uses submodules, but submodules will fetch automatically on demand,
so `--recursive` or `git submodule update --init --recursive` is not needed.

    $ git clone https://github.com/kagandikmen/clairvoyant-compiler.git

## Prerequisites

Several standard packages are needed to build the toolchain.  

On Ubuntu, executing the following command should suffice:

    $ sudo apt-get install autoconf automake autotools-dev curl python3 python3-pip libmpc-dev libmpfr-dev libgmp-dev gawk build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat-dev ninja-build git cmake libglib2.0-dev libslirp-dev

On Fedora/CentOS/RHEL OS, executing the following command should suffice:

    $ sudo yum install autoconf automake python3 libmpc-devel mpfr-devel gmp-devel gawk  bison flex texinfo patchutils gcc gcc-c++ zlib-devel expat-devel libslirp-devel
    
On Arch Linux, executing the following command should suffice:

    $ sudo pacman -Syyu autoconf automake curl python3 libmpc mpfr gmp gawk base-devel bison flex texinfo gperf libtool patchutils bc zlib expat libslirp

Also available for Arch users on the AUR: [https://aur.archlinux.org/packages/riscv-gnu-toolchain-bin](https://aur.archlinux.org/packages/riscv-gnu-toolchain-bin)

On OS X, you can use [Homebrew](http://brew.sh) to install the dependencies:

    $ brew install python3 gawk gnu-sed gmp mpfr libmpc isl zlib expat texinfo flock libslirp

To build the glibc (Linux) on OS X, you will need to build within a case-sensitive file
system.  The simplest approach is to create and mount a new disk image with
a case sensitive format.  Make sure that the mount point does not contain spaces. This is not necessary to build newlib or gcc itself on OS X.

This process will start by downloading about 200 MiB of upstream sources, then
will patch, build, and install the toolchain.  If a local cache of the
upstream sources exists in $(DISTDIR), it will be used; the default location
is /var/cache/distfiles.  Your computer will need about 8 GiB of disk space to
complete the process.

## Installation

To build the compiler, pick an install path (that is writeable).
If you choose, say, `/opt/riscv`, then add `/opt/riscv/bin` to your `PATH`.
Then, simply run the following commands from inside the clairvoyant-compiler directory:

    ./configure --prefix=/opt/riscv --with-abi=ilp32 --with-arch=rv32i
    make

You might want to speed up the make process by using

    make -j $(nproc)

instead. 

## Contributing

Pull requests, suggestions, bug fixes etc. are all welcome.

## License

RISC-V GNU Toolchain, of which clairvoyant-compiler is a redistribution, includes work distributed under GNU General Public License v2.0 and GNU Lesser General Public License v2.1. In accordance, the same license terms are reproduced by this redistribution, and modifications on it are licensed under GNU General Public License v2.0. Please see [`LICENSE`](LICENSE) for details.