This repository is an artifact for my thesis, in partial fulfillment of the requirements for the degree of Master of Engineering in Electrical Engineering and Computer Science.

The respective submodules have their own READMEs for documentation on setup. The below contains further information.

The version of Haskell used was GHC 8.4.3. The version of Coq used is version 8.19.2, compiled with OCaml 5.2.0.

The setup instructions for `riscv-semantics` remain mostly the same. To build the test cases for vector instructions, 
run 
```
$ ./install_riscv_gcc_vector.sh 
$ . setup.sh
```
and build tests as before. Source code for the test cases is at folder `test/src/vector`, and generated assembly will be at `test/build/`.

To emulate assembly with RISC-V vector instructions, use `stack exec riscv-semantics-v <name of binary file>`. Only a limited subset of the RISC-V V extension instructions are supported. 

To update the Coq translation, after successfully running `./install.sh` in folder `riscv-semantics`, change current directory to `bedrock2/deps/riscv-coq`, run `make convert`, `make spec`, and then `make all`.

Errors may arise due to `hs-to-coq` not recognizing Haskell constructs used; to resolve this, update the edit files in `bedrock2/deps/riscv-coq/convert-hs-to-coq` as appropriate, as well as the Makefile in needed. Errors may also arise in Coq files outside of the decode and execute files in Coq, in which case they will need to be manually updated. 




