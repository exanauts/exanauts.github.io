# Exanauts

We are a loose team that started at the Mathematical and Computational Science
Division at the Argonne National Laboratory with common interests in solving
energy systems-related problems in the [Exascale Computing
Project](https://www.exascaleproject.org/)
[ExaSGD](https://www.exascaleproject.org/research-project/exasgd/) by
leveraging the latest DOE-provided computing hardware with a passion for the
programming language [Julia](https://julialang.org/). This includes accelerators
(e.g. GPUs), [Summit](https://www.olcf.ornl.gov/summit/) at OLCF, and future
exascale systems [Frontier](https://www.olcf.ornl.gov/frontier/) and
[Aurora](https://www.alcf.anl.gov/aurora). To prototype our methods, we
heavily rely on Julia,
[KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl),
[CUDA.jl](https://github.com/JuliaGPU/CUDA.jl),
[AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl), and
[oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl).

Our team covers a large area of expertise, allowing us to fully control the
entire software stack, consisting of application, modeling, optimization
methods, and linear algebra.

Our adventure was recently published in [SIAG/OPT Views and
News](http://wiki.siam.org/siag-op/images/siag-op/e/e8/ViewsAndNews-29-1.pdf).

# Current Challenges

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

# Current Hardware

## Moonshot

Moonshot is our main development workstation

* 2 Xeon Gold 6140 CPUs @ 2.30GHz
* 2 NVDIDA GV100 32GB Volta GPUs
* 512 GB RAM

## Frontier

Our code is being tested on the latest exascale system Frontier (OLCF).

## Intel GPUs

Our code is being tested on various testbed systems at Argonne National Laboratory.
## Polaris

The current system for the CUDA backend is the pre-Aurora system Polaris (ALCF) with A100 GPUs.
## Summit
Summit is a supercomputer at Oak Ridge National Laboratories. This machine is on
our path to the new exascale architectures, which will come online in the coming
years (Frontier and Aurora). A detailed description of its hardware can be found
[here](https://www.olcf.ornl.gov/olcf-resources/compute-systems/summit/).

# Julia on Summit

Julia builds for Summit at OLCF
* [julia-1.7.1-linuxppc64le.tar.gz](https://web.cels.anl.gov/~mschanen/julia-1.7.1-linuxppc64le.tar.gz)

# Team Members

* Anitescu, Mihai
* Churavy, Valentin (MIT/Julia Lab)
* Kim, Kibaek
* Maldonado, Adrian
* Pacaud, François
* Rao, Vishwas
* Samaroo, Julian (MIT/Julia Lab)
* Schanen, Michel
* Shin, Sungho
* Subramanyam, Anirudh (Penn State)

# Past Team Members

* Kim, Youngdae (Research Associate at ExxonMobil)

# References

* Anitescu, M., D. A. Maldonado, F. Pacaud, K. Kim, Y. Kim, V. Rao, M. Schanen, S. Shin, and A. Subramanyam. 2022. Targeting Exascale with Julia on GPUs for multiperiod optimization with scenario constraints. Vol. 29. SIAG-OP News and Views. http://wiki.siam.org/siag-op/images/siag-op/e/e8/ViewsAndNews-29-1.pdf.
* Cole, David, Sungho Shin, François Pacaud, Victor M. Zavala, and Mihai Anitescu. 2022. "Exploiting GPU/SIMD Architectures for Solving Linear-Quadratic MPC Problems." arXiv preprint arXiv:2209.13049.
Dandurand, Brian, Kibaek Kim, and Michel Schanen. 2020. "Toward a scalable robust security-constrained optimal power flow using a proximal projection bundle method." Electric Power Systems Research (Elsevier) 189: 106681. doi:10.1016/j.epsr.2020.106681.
* Kim, Youngdae, and Kibaek Kim. 2022. "Accelerated Computation and Tracking of AC Optimal Power Flow Solutions Using GPUs." Workshop Proceedings of the 51st International Conference on Parallel Processing. 1–8. doi:10.1145/3547276.3548631.
* Kim, Youngdae, François Pacaud, Kibaek Kim, and Mihai Anitescu. 2021. "Leveraging GPU batching for scalable nonlinear programming through massive Lagrangian decomposition." arXiv preprint arXiv:2106.14995.
* Maldonado, Daniel Adrian, Michel Schanen, François Pacaud, and Mihai Anitescu. 2021. "Domain Decomposition Preconditioners for Unstructured Network Problems in Parallel Vector Architectures." 50th International Conference on Parallel Processing Workshop. 1–5. doi:10.1145/3458744.3473363.
* Pacaud, François, Daniel Adrian Maldonado, Sungho Shin, Michel Schanen, and Mihai Anitescu. 2022. "A feasible reduced space method for real-time optimal power flow." Electric Power Systems Research (Elsevier) 212: 108268. doi:10.1016/j.epsr.2022.108268.
* Pacaud, François, Michel Schanen, Daniel Adrian Maldonado, Alexis Montoison, Valentin Churavy, Julian Samaroo, and Mihai Anitescu. 2022. "Batched second-order adjoint sensitivity for reduced space methods." Proceedings of the 2022 SIAM Conference on Parallel Processing for Scientific Computing. 60–71. doi:10.1137/1.9781611977141.6.
* Pacaud, François, Michel Schanen, Sungho Shin, Daniel Adrian Maldonado, and Mihai Anitescu. 2023. "Parallel Interior-Point Solver for Block-Structured Nonlinear Programs on SIMD/GPU Architectures." arXiv preprint arXiv:2301.04869.
* Pacaud, François, Sungho Shin, Michel Schanen, Daniel Adrian Maldonado, and Mihai Anitescu. 2022. "Condensed interior-point methods: porting reduced-space approaches on GPU hardware." arXiv preprint arXiv:2203.11875.
* Rao, Vishwas, Anirudh Subramanyam, Michel Schanen, Youngdae Kim, Ignas Satkauskas, and Mihai Anitescu. 2022. "Frequency Recovery in Power Grids using High-Performance Computing." Workshop Proceedings of the 51st International Conference on Parallel Processing. 1–6. doi:10.1145/3547276.3548632.
* Rao, Vishwas, Kibaek Kim, Michel Schanen, Daniel A. Maldonado, Cosmin Petra, and Mihai Anitescu. 2019. "A Multiperiod Optimization-Based Metric of Grid Resilience." 2019 IEEE Power & Energy Society General Meeting (PESGM). 1–5. doi:10.1109/pesgm40551.2019.8974137.
* Schanen, Michel, Daniel Adrian Maldonado, François Pacaud, Alexis Montoison, Mihai Anitescu, Kibaek Kim, Youngdae Kim, Vishwas Rao, and Anirudh Subramanyam. 2020. "Julia as a portable high-level language for numerical solvers of power flow equations on GPU architectures." Les Cahiers du GERAD ISSN 711: 2440.
* Subramanyam, Anirudh, Youngdae Kim, Michel Schanen, François Pacaud, and Mihai Anitescu. 2021. "A Globally Convergent Distributed Jacobi Scheme for Block-Structured Nonconvex Constrained Optimization Problems." arXiv preprint arXiv:2112.09027.


