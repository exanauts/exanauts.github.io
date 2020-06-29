# Exanauts

We are loose team at the Mathematical and Computational Science division at the Argonne National Laboratory with common interests in solving energy systems related problems by leveraging the latest DOE provided computing hardware. This includes accelerators (e.g. GPUs), [Summit](https://www.olcf.ornl.gov/summit/) at OLCF, and future exascale systems [Frontier](https://www.olcf.ornl.gov/frontier/) and [Aurora](https://www.alcf.anl.gov/aurora). In order to prototype our methods we heavily rely on the programming lanuage [Julia](https://julialang.org/).

Our team covers a large area of expertise allowing us to have full control of the entire software stack compromising application, modeling, optimization methods, and linear algebra.

# Current Challenges

* Overcome sparse algebra on GPUs for unstructured optimization problems.
* Fast and higher-order derivatives on GPUs and other architectures.

# Software Overview

## [ExaPF](https://github.com/exanauts/ExaPF.jl)

A power flow solver running the Newton steps entirely on the GPU. This includes, the evaluation of the Jacobian using automatic differentiation, the optimization solver (Newton), the preconditioner (Block-Jacobi), and the linear solver (BICGSTAB).

## [PIPS-NLP](https://github.com/Argonne-National-Laboratory/PIPS/)

PIPS is a suite of parallel optimization solvers mainly for stochastic optimization problems written in C++. Our most used solver is PIPS-NLP which implements the interior-point method similar to [Ipopt](https://github.com/coin-or/Ipopt). It uses sparse algebra kernels and the Schur complement to decompose the optimization problems. It is one of our solvers for security constrained optimal pwerflow.

## GO-Data

Large-scale data sets for problems that were used in the [ARPA-E Grid Optimization](https://gocompetition.energy.gov/) competition.

# Current Hardware

## Moonshot

Moonshot is our main development workstation

* 2 Xeon Gold 6140 CPUs @ 2.30GHz
* 2 NVDIDA GV100 32GB Volta GPUs
* 512 GB RAM

## Summit

Supercomputer at Oak Ridge National Laboratories. This machine is on our path to the new exascale architectures which will come online in the coming years (Frontier and Aurora).
A detailed description of its hardware can be found [here](https://www.olcf.ornl.gov/olcf-resources/compute-systems/summit/).

# Julia on Summit

These are Julia builds that are used on [Summit](https://www.olcf.ornl.gov/summit/) in our ECP project ExaSGD.

Julia builds for Summit at OLCF 
* [julia-1.3.1-linuxppc64le.tar.gz](https://www.mcs.anl.gov/~schanen/julia-1.3.1-linuxppc64le.tar.gz)
* [julia-1.4.2-linuxppc64le.tar.gz](https://www.mcs.anl.gov/~schanen/julia-1.4.2-linuxppc64le.tar.gz)

Requirements:

```
module load gcc/7.4.0
```
# Team Members

* Anitescu, Mihai
* Kim, Kibaek
* Kim, Youngdae
* Maldonado, Adrian
* Rao, Vishwas
* Schanen, Michel
* Subramanyam, Anirudh
