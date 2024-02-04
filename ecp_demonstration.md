Our ECP demonstration project involved a multiperiod security-constrained optimal power flow simulation modelled entire in Julia. We used pure Julia numerical solvers that leveraged Julia's flexibilty to run on GPU architectures and ECP systems. This  included
[Summit](https://www.olcf.ornl.gov/summit/) at OLCF, [Frontier](https://www.olcf.ornl.gov/frontier/), and
[Aurora](https://www.alcf.anl.gov/aurora). To implement our methods, we
heavily relied on the Julia packages
[KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl),
[CUDA.jl](https://github.com/JuliaGPU/CUDA.jl),
[AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl), and
[oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl).

The entire code base of our ECP demonstration Milepost7 can be found at [Milepost7.jl](https://github.com/exanauts/Milepost7.jl).


Our adventure was recently published in [SIAG/OPT Views and
News](http://wiki.siam.org/siag-op/images/siag-op/e/e8/ViewsAndNews-29-1.pdf).

# Challenges

* Overcome sparse algebra limitations on GPUs for unstructured optimization problems.
* Fast and higher-order derivatives on GPUs and other architectures.

# Software Overview

## [ProxAL.jl](https://github.com/exanauts/ProxAL.jl)

An ADMM-like proximal Augmented Lagrangian solver for tackling large-scale
block-structured nonconvex optimization problems in a distributed manner. The
latter includes security-constrained as well as multi-period AC optimal power
flow problems.

## [ExaTron.jl](https://github.com/exanauts/ExaTron.jl)

ExaTron.jl implements a trust-region Newton solver for batched nonlinear
programming on GPUs. Problems in the batch are solved in parallel by employing
multiple thread blocks on GPUs. Our basic algorithm to solve each problem on
GPUs is an extension of the algorithm by [Lin and
More](https://epubs.siam.org/doi/10.1137/S1052623498345075) and its code
[TRON](https://www.mcs.anl.gov/~more/tron/).
## [ExaAdmm.jl](https://github.com/exanauts/ExaAdmm.jl)

This package also provides the implementation of adaptive ADMM for distributed ACOPF
introduced by [Mhanna et al.
(2019)](https://doi.org/10.1109/TPWRS.2018.2886344), running fully on GPUs
without data transfer to the CPU, where `ExaTron.jl` is used to solve many small
nonlinear nonconvex problems, each of which represents a branch subproblem of
the ADMM. So far, it relies on ExaTron.jl as a bound-constrained QP solver.

## [Argos.jl](https://github.com/exanauts/Argos.jl)

Argos.jl extends [ExaPF.jl](https://github.com/exanauts/ExaPF.jl) by
implementing the optimization routines required to solve the optimal power flow
(OPF) problems.

## [ExaPF.jl](https://github.com/exanauts/ExaPF.jl)

A power flow solver running the Newton steps entirely on the GPU. This includes
the evaluation of the Jacobian using automatic differentiation, the optimization
solver (Newton), the preconditioner (Block-Jacobi), and the linear solver
(BICGSTAB).

## [ExaData](https://github.com/exanauts/ExaData)

ExaData is a collection of power grid network data we use in our project. It
contains a script to create a Julia artifact such that our codes can use this
data transparently.

## [MadNLP.jl](https://github.com/MadNLP/MadNLP.jl)

MadNLP is a nonlinear programming (NLP) solver, purely implemented in Julia.
MadNLP implements a filter line-search algorithm, as that used in
[Ipopt](https://github.com/coin-or/Ipopt). MadNLP was initially developed at
University of Madison.

## [PIPS-NLP](https://github.com/Argonne-National-Laboratory/PIPS/)

PIPS is a suite of parallel optimization solvers mainly for stochastic
optimization problems written in C++. Our most used solver is PIPS-NLP which
implements the interior-point method similar to
[Ipopt](https://github.com/coin-or/Ipopt). It uses sparse algebra kernels and
the Schur complement to decompose the optimization problems. It is one of
our solvers for security-constrained optimal powerflow.
