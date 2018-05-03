# Xilinx BRAM wrapper

This is a flexible work-around for [this](https://www.xilinx.com/support/answers/61995.html) Xilinx Vivado issue:
When inferring block RAMs from RAMs described in RTL, the RAM depth is extended to the nearest power of 2, which in the worst
case means a doubling of the number of BRAM elements used.

This wrapper module splits the RAM depth into power of 2-sized chunks such that a minimal amount of BRAMs will be inferred.
For instance, if the depth is 21000 it will be decomposed into three RAMs of size 16384 + 4096 + 520 instead of one RAM of size
32768. Decomposing the RAM into several smaller RAMs is done automatically at elaboration time.
