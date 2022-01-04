# Exanauts

We are a loose team at the Mathematical and Computational Science division at the Argonne National Laboratory with common interests in solving energy systems related problems by leveraging the latest DOE provided computing hardware. This includes accelerators (e.g. GPUs), [Summit](https://www.olcf.ornl.gov/summit/) at OLCF, and future exascale systems [Frontier](https://www.olcf.ornl.gov/frontier/) and [Aurora](https://www.alcf.anl.gov/aurora). In order to prototype our methods we heavily rely on the programming lanuage [Julia](https://julialang.org/).

Our team covers a large area of expertise allowing us to have full control of the entire software stack compromising application, modeling, optimization methods, and linear algebra.

# Current Challenges

* Overcome sparse algebra limitations on GPUs for unstructured optimization problems.
* Fast and higher-order derivatives on GPUs and other architectures.

# Software Overview

## [ProxALjl](https://github.com/exanauts/ProxAL.jl)

An ADMM-like proximal Augmented Lagrangian solver for tackling large-scale block-structured nonconvex optimization problems in a distributed manner. The latter includes security-constrained as well as multi-period AC optimal power flow problems.

## [ExaTron.jl](https://github.com/exanauts/ExaTron.jl)

ExaTron is the Julia implementaion of novel GPU-accelerated algorithm for bound-constrained nonlinear nonconvex optimization problems. As a use case, this package also provides the implementation of adaptive ADMM for distributed ACOPF introduced by [Mhanna et al. (2019)](https://doi.org/10.1109/TPWRS.2018.2886344), running fully on GPUs without data transfer to the CPU, where `ExaTron.jl` is used to solve many small nonlinear nonconvex problems, each of which represents a branch subproblem of the ADMM.

## [Argos.jl](https://github.com/exanauts/Argos.jl)

Argos.jl extends [ExaPF.jl](https://github.com/exanauts/ExaPF.jl) by implementing the optimization routines required to solve the optimal power flow (OPF) problems.

## [ExaPF.jl](https://github.com/exanauts/ExaPF.jl)

A power flow solver running the Newton steps entirely on the GPU. This includes, the evaluation of the Jacobian using automatic differentiation, the optimization solver (Newton), the preconditioner (Block-Jacobi), and the linear solver (BICGSTAB).

## [ExaData](https://github.com/exanauts/ExaData)

ExaData is collection of power grid network data we use in our project. It contains a script to create a Julia artifact such that our codes can use this data transparently.

## [MadNLP]()

MadNLP is a nonlinear programming (NLP) solver, purely implemented in Julia. MadNLP implements a filter line-search algorithm, as that used in [Ipopt](https://github.com/coin-or/Ipopt). MadNLP was initially developed at University of Madison.

## [PIPS-NLP](https://github.com/Argonne-National-Laboratory/PIPS/)

PIPS is a suite of parallel optimization solvers mainly for stochastic optimization problems written in C++. Our most used solver is PIPS-NLP which implements the interior-point method similar to [Ipopt](https://github.com/coin-or/Ipopt). It uses sparse algebra kernels and the Schur complement to decompose the optimization problems. It is one of our solvers for security constrained optimal powerflow.

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

Julia builds for Summit at OLCF
* [julia-1.7.1-linuxppc64le.tar.gz](https://web.cels.anl.gov/~mschanen/julia-1.7.1-linuxppc64le.tar.gz)

# Team Members

* Anitescu, Mihai
* Churavy, Valentin (MIT/Julia Lab)
* Kim, Kibaek
* Kim, Youngdae
* Maldonado, Adrian
* Pacaud, François
* Rao, Vishwas
* Samaroo, Julian (MIT/Julia Lab)
* Schanen, Michel
* Shin, Sungho
* Subramanyam, Anirudh
