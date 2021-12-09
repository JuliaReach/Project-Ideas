# :bulb: :notebook: Project Ideas: Contributing to JuliaReach

### Programs with external funding

Google summer of Code (GSoC) and Julia Seasons of Contributions (JSoC) are seasonal programs for funding and/or
mentoring students and other developers to contribute to the open source ecosystem.

If you have a record of contributions to the JuliaReach ecosystem, it is possible for you to apply to such programs which generally take place between june and august of each year. Please note that the selection bar is quite high: successful candidates are expected to be familiar with the development workflow (github, git, julia language) and should have an equivalent of a master's or phd degree in the scientific domain of the proposal.

For additional information see https://julialang.org/jsoc/

## Reachability analysis with sparse polynomial zonotopes in JuliaReach

**Description.** Sparse polynomial zonotopes are a new non-convex set representation that are well-suited for reachability analysis of nonlinear dynamical systems. The task is to add efficient Julia implementations of 1) sparse polynomial zonotopes in [LazySets](https://github.com/JuliaReach/LazySets.jl), 2) the corresponding reachability algorithm for dynamical systems in [ReachabilityAnalysis](https://github.com/JuliaReach/ReachabilityAnalysis.jl), and 3) an integration of the new algorithm for neural-network control systems in [NeuralNetworkAnalysis](https://github.com/JuliaReach/NeuralNetworkAnalysis.jl).

**Expected Results.** The goal is to efficiently implement sparse polynomial zonotopes and the corresponding reachability algorithms. The code is to be documented, tested, and evaluated extensively in benchmarks.

**Recommended Skills.** Familiarity with Julia and Git/GitHub is mandatory. Familiarity with the mentioned Julia packages is appreciated but not required. The project does not require theoretical contributions, but it requires reading a research article (see below); hence a certain level of academic experience is recommended.

**Literature and related package.** The relevant theory is described in [this research article](https://arxiv.org/pdf/1901.01780). There exists a Matlab implementation in [CORA](https://tumcps.github.io/CORA/) (the implementation of polynomial zonotopes can be found in [this folder](https://github.com/TUMcps/CORA/tree/master/contSet/%40polyZonotope)).


## Efficient two-dimensional geometric operations in LazySets

**Description.** [LazySets](https://github.com/JuliaReach/LazySets.jl) is a Julia library for computing with geometric sets. The focus is on lazy set representations and efficient high-dimensional processing. Still, two-dimensional sets are prevalent and there are known efficient implementations for various types of two-dimensional sets. Many functions currently assume general sets and hence do not apply tricks known for two-dimensional geometry. For example, there is a vast body of literature on efficient polygon algorithms. In this project we are not restricted to polygons, and we want to support lazy operations as well.

**Expected Results.** The goal is to implement efficient algorithms for geometry in the plane (sets in two dimensions) from the literature. The code is to be documented, tested, and evaluated in benchmarks.

**Recommended Skills.** Familiarity with Julia and Git/GitHub is mandatory. Familiarity with [LazySets](https://github.com/JuliaReach/LazySets.jl) is recommended. Basic knowledge of geometric terminology is appreciated but not required.

**Related packages.** The [JuliaGeometry](https://github.com/JuliaGeometry) organization has several relevant packages, but only a few relevant functions for basic set types. In this project we aim to add more functionality for more general set types.


## GPU-accelerated reachability for structural mechanics

**Description.** This project aims at implementing reachability methods on the GPU, with a special focus on support-function based and/or zonotope-based methods. The algorithms will be tested on  semi-discrete linear PDEs arising from discretization using the method of finite elements.


