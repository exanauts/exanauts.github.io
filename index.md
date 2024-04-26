# Exanauts

## Who Are We?
Originating from the Mathematical and Computational Science Division at Argonne
National Laboratory, we are the Exanauts—a dynamic group united by our shared
mission to tackle complex energy systems challenges. Our journey began within
the Exascale Computing Project [ExaSGD](https://www.exascaleproject.org/research-project/exasgd/), where we
harness the power of cutting-edge DOE computing resources. Driven by our
enthusiasm for the [Julia](https://julialang.org/) programming language, we
embark on developing
innovative solutions for today’s energy problems. Discover more about our
[ECP demonstration project](#ecp-demonstration).

[Our team](#Team-Members) covers a broad spectrum of expertise, allowing
us to oversee the entire software design, consisting of application, modeling,
optimization methods, and linear algebra.

## Our Vision
At the core of our vision is the transformative potential of applying
mathematical principles through the use of flexible, high-performance numerical
algorithms optimized for contemporary specialized hardware. We champion the
Julia programming language and its innovative frontends for intermediate
representations (such as LLVM IR and MLIR) as pivotal enablers of this
transformation. Our ultimate goal? To usher in a new era of scientific
discovery, including the rapid prototyping of digital twins.

## Our Mission
Under the auspices of the DOE Office of Science, our endeavors are directed toward contributing significantly to a multitude of projects. Each project is
carefully selected and designed to further our overarching goal: advancing DOE’s
scientific simulations to address the pressing challenges associated with
current energy infrastructures.

## Current Research

### Energy systems modeling
In response to the escalating demand for renewable energy sources and the
seamless integration of electric vehicles, we develop sophisticated models of
energy systems. Our work facilitates the transition to a more sustainable and
efficient energy landscape.

#### Software Contributions
* Fast GPU modeling for sparse, large-scale nonlinear programs: [ExaModels.jl](https://github.com/exanauts/ExaModels.jl)
* Multiperiod security-constrained optimal powerflow: [Milepost7.jl](https://github.com/exanauts/Milepost7.jl)


### Differentiable Sparse Linear Solvers on GPUs
We develop and enhance differentiable sparse linear solvers on GPUs available in Julia. This innovation is pivotal for solving large-scale optimization problems prevalent in the energy sector with unprecedented efficiency.

#### Software Contributions
* Interface to CUDSS: [CUDSS.jl](https://github.com/exanauts/CUDSS.jl)
* Fast refactorization for Schur-complement: [CUSOLVERRF.jl](https://github.com/exanauts/CUSOLVERRF.jl)
* Polymorphic Krylov solvers: [Krylov.jl](https://github.com/JuliaSmoothOptimizers/Krylov.jl/)
* GPU preconditioners: [KrylovPreconditioners.jl](https://github.com/JuliaSmoothOptimizers/KrylovPreconditioners.jl/)
* Differentiable Krylov methods: [DiffKrylov.jl](https://github.com/JuliaSmoothOptimizers/DiffKrylov.jl)

### Nonlinear Optimization on GPUs
Tackling the omnipresent nonlinear optimization challenges within energy
systems, we are at the forefront of formulating and implementing novel
algorithms and software. Our focus is on harnessing GPU capabilities to
revolutionize how these problems are approached and solved.
#### Software Contributions
* Nonlinear optimization solver running on CPU/GPU: [MadNLP.jl](https://github.com/MadNLP/MadNLP.jl)
* Trust-region Newton solver for batched nonlinear programming on GPUs: [ExaTron.jl](https://github.com/exanauts/ExaTron.jl)
* Batched second-order adjoint sensitivity for reduced space methods: [Argos.jl](https://github.com/exanauts/Argos.jl)
* Adaptive ADMM for distributed ACOPF: [ExaAdmm.jl](https://github.com/exanauts/ExaAdmm.jl)
* A power flow solver with GPU support: [ExaPF.jl](https://github.com/exanauts/ExaPF.jl)

## ECP Demonstration
Our ECP demonstration project involved a multiperiod security-constrained optimal power flow simulation modeled entirely in Julia. We used pure Julia numerical solvers that leveraged Julia's flexibility to run on GPU architectures and ECP systems. This included
[Summit](https://www.olcf.ornl.gov/summit/) at OLCF, [Frontier](https://www.olcf.ornl.gov/frontier/), and
[Aurora](https://www.alcf.anl.gov/aurora). To implement our methods, we
heavily relied on the Julia packages
[KernelAbstractions.jl](https://github.com/JuliaGPU/KernelAbstractions.jl),
[CUDA.jl](https://github.com/JuliaGPU/CUDA.jl),
[AMDGPU.jl](https://github.com/JuliaGPU/AMDGPU.jl), and
[oneAPI.jl](https://github.com/JuliaGPU/oneAPI.jl).

The entire code base of our ECP demonstration Milepost7 can be found at [Milepost7.jl](https://github.com/exanauts/Milepost7.jl).


Our adventure was published in [SIAG/OPT Views and
News](http://wiki.siam.org/siag-op/images/siag-op/e/e8/ViewsAndNews-29-1.pdf) and is summarized by the following highlights.

![Highlights](/highlights.png "Highlights")
# Team Members
* Anitescu, Mihai
* Kim, Kibaek
* Maldonado, Adrian
* Montoison, Alexis (GERAD, Montreal, Canada)
* Pacaud, François
* Rao, Vishwas
* Schanen, Michel
* Shin, Sungho
* Subramanyam, Anirudh (Penn State)

## Ongoing Collaborations
* Edelman, Alan (MIT/Julia Lab)
* Zavala, Victor (University of Wisconsin-Madison)

## Past Team Members
* Churavy, Valentin (MIT/Julia Lab)
* Kim, Youngdae (Research Associate at ExxonMobil)
* Samaroo, Julian (MIT/Julia Lab)

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
