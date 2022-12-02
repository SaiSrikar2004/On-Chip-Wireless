# gem5-X + On-Chip-Wireless

Gem5-X-On_Chip-Wireless supports the modelling of systems featuring interconnections enabled by on-chip transceivers and a nano-antennae. The behaviour a wireless link with different latencies, bandwidths, and Medium Access Control (MAC) protocols can be emulated.

The features of the modeled on-chip wireless interconnect and an exploration of its parameters is described in the following paper:
>R. Medina, J. Klein, G. Ansaloni, M. Zapater, S. Abadal, E. Alarcón, D. Atienza.
>"[**System-Level Exploration of In-Package Wireless Communication for Multi-Chiplet Platforms**](https://infoscience.epfl.ch/record/298245?&ln=en)".
>In _ASPDAC '23_.

## 

## Installing gem5-X-On-Chip-Wireless

Please carefully follow the instructions provided in Section 2 of the [technical manual][https://github.com/gem5-X/On-Chip-Wireless/blob/master/gem5_X_TechnicalManual_Wireless.pdf] enclosed in this repository to install gem5-X-On-Chip-Wireless and the necessary dependencies. 

## Compiling benckmarks

The compiler should target arm-linux system. The modified Stream benchmark can be compiled using [arm_compile.sh](benchmarks/Stream/arm_compile.sh).

## Running code on gem5-X

You can launch a simulation of a system implementing an on-chip wireless interconnect using the following command:

```
./build/ARM/gem5.{fast, opt, debug} \
--remote-gdb-port=0 \
-d /path/to/your/output/directory \
configs/example/fs.py \
--cpu-clock=1GHz \
--kernel=vmlinux \
--machine-type=VExpress_GEM5_V1 \
--dtb-file=<path_to_gem5-X>/system/arm/dt/armv8_gem5_v1_<NUM_CORES>cpu.dtb \ 
-n <NUM_OF_CORES> \
--disk-image=gem5_ubuntu16.img  \
--caches  \
--l2cache  \
--l1i_size=32kB \
--l1d_size=32kB  \
--l2_size=1MB  \
--l2_assoc=2  \
--mem-type=DDR4_2400_4x16 \
--mem-ranks=4 \
--mem-size=4GB \
--sys-clock=1600MHz \
--membus-wireless \
--wireless-bandwidth=12.5GB/s \
--mac-protocol=exp_backoff
```

## Acknowledgements

This work has been supported by the EC H2020 WiPLASH (GA No. 863337) and the EC H2020 FVLLMONTI (GA No. 101016776) projects.
