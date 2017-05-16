SCR1 is an open-source RISC-V compatible MCU core, designed by Syntacore.

## Key features
* RV32I|E[MC] ISA
* Machine privilege mode
* 2 to 4 stage pipeline
* 32-bit AHB-Lite external interface
* Integrated IRQ controller and advanced debug
* Optimized for area and power
* Written in SystemVerilog
* Features a number of configurable parameters

For more information, see *docs/scr1_eas.pdf*.

## Repository contents
Folder | Description
------ | -----------
docs                         | SCR1 documentation
src                          | SCR1 RTL source and testbench files
tests/common                 | Common source files for tests
tests/riscv_isa              | Subset of the RISC-V ISA tests from the master RISC-V repo, relevant for SCR1
tests/benchmarks/dhrystone21 | Dhrystone 2.1 source files

## Quick start guide

### Clone and build the RISC-V toolchain

    git clone https://github.com/riscv/riscv-gnu-toolchain.git
    cd riscv-gnu-toolchain
    git checkout 4bcd4f57af50b32efafa2088f996ede3142ec77b
    ./configure --prefix=<YOUR_INSTALL_PATH> --with-xlen=32 --with-arch=IM
    make

Add the <YOUR_INSTALL_PATH>/bin folder to the PATH environment variable.


### Build RTL, compile and run tests
`make run_<SIMULATOR>` will build RTL and tests, then run all tests with default parameters.

Currently supported options:
* run_modelsim
* run_vcs
* run_ncsim

Please note that RTL simulator executables should be in your PATH variable.

To run an arbitrary subset of tests, edit the *tests* target in the top Makefile, or the *list.txt* in riscv_isa subfolder.
After all the tests have finished, the results can be found in *build/test_results.txt* (default location).

* Test build and run parameters can be configured in the *Makefile*
* SCR1 core parameters can be configured in *src/includes/scr1_arch_description.svh*

Please make sure that architectural config selected for the SCR1 RTL matches the one used for tests compilation.
