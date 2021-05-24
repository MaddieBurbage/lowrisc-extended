lowRISC chip
==============================================

This is my fork of lowRISC, used for accelerator research for the Bailey Research Group at Williams. It extends Cambridge's v0.6 lowRISC processor, which targets the Rocket Chip for the Nexys A7. Built with RV64GC, and can be built for Debian.

Major Changes
==============================================
Our extension of lowRISC served several purposes:
* We add accelerators to the processor, using the RoCC interface. These serve a variety of purposes, from speeding up functions and lowering power usage, to understanding the system and its performance.
* Accelerators using the RoCC interface can't connect to memory well in Rocket -- on a memory-access exception, the mem system breaks. We make the mem system resilient to exceptions.
* Our board, the Nexys A7, has eight 7-segment displays not used by lowRISC. We connect them to the processor for easy debugging of the system or accelerators.

Accelerators
==============================================
Our devices are contained in the rocket-chip submodule, in [src/main/scala/tile/](https://github.com/MaddieBurbage/rocket-chip/tree/d8f0bc6f1cfb2d93839948a754ddcd151bda09c5/src/main/scala/tile). 
* The Ephelia accelerator is a simple example accelerator. 
* MemTest is a simple test accelerator for the RoCC interface's mem system. 
* Combinations can create several varieties of number-theoretic sequences: the [cool, cooler, and coolest orders](https://link.springer.com/article/10.1007/s00224-013-9486-8) designed by Brett Stevens and Aaron Williams, with cool implemented by Donald Knuth. 
* DancingLinks accelerates Duane Bailey's exact cover solver, which uses Knuth's Dancing Link operations to search the solution space efficiently.
* LightDebugger uses the Nexys A7's light display to show users debugging information from within accelerators.

Setup
==============================================
This repository has several submodules, some of which are also forked from lowRISC. They give the basic setup for adding accelerators, as can be seen in Ephelia and Combinations.

To download the repo and grab its submodules:

~~~shell
git clone -b refresh-v0.6 --recursive https://github.com/MaddieBurbage/lowrisc-extended.git
~~~

lowRISC Documentation
==============================================
See LICENSE.Cambridge for license details.

See the [documentation](https://www.lowrisc.org/docs/) for build instructions.
For the lowRISC repository: [lowRISC](https://github.com/lowrisc/lowrisc-chip)
