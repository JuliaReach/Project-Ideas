# :bulb: :notebook: Project Ideas: Contributing to JuliaReach

### Programs with external funding

Google summer of Code (GSoC) and Julia Seasons of Contributions (JSoC) are seasonal programs for funding and/or
mentoring students and other developers to contribute to the open source ecosystem.

If you have a record of contributions to the JuliaReach ecosystem, it is possible for you to apply to such programs which generally take place between june and august of each year. Please note that the selection bar is quite high: successful candidates are expected to be familiar with the development workflow (github, git, julia language) and should have an equivalent of a master's or phd degree in the scientific domain of the proposal.

For additional information see https://julialang.org/jsoc/

## Nonlinear reachability using state-space abstractions

**Description.** Computation of reachable 

- https://mediatum.ub.tum.de/doc/1615814/gwj94isxrct41uqcp7bxo3wat.pdf

## Reachability for differential-algebraic equation systems

- https://mediatum.ub.tum.de/doc/1281529/770926.pdf

## Fast global optimizer using tensor for Bernstein expansions

- bounds
- bounding functions
- cf Kodia
- see refs

- [1] Smith, A. P. Fast construction of constant bound functions for sparse polynomials. Journal of Global Optimization 43.2 (2009): 445-458.

- [2] Smith, A. P. Enclosure methods for systems of polynomial equations and inequalities. Doctoral dissertation, Universität Konstanz (2012).

- [3] Titi, J., & Garloff, J. (2017). Fast determination of the tensorial and simplicial Bernstein forms of multivariate polynomials and rational functions. Konstanzer Schriften in Mathematik; 361.


## Reachability analysis with sparse polynomial zonotopes in JuliaReach

**Description.** Sparse polynomial zonotopes are a new non-convex set representation that are well-suited for reachability analysis of nonlinear dynamical systems. The task is to add efficient Julia implementations of 1) sparse polynomial zonotopes in [LazySets](https://github.com/JuliaReach/LazySets.jl), 2) the corresponding reachability algorithm for dynamical systems in [ReachabilityAnalysis](https://github.com/JuliaReach/ReachabilityAnalysis.jl), and an integration of the new algorithm for neural-network control systems in 3) [NeuralNetworkAnalysis](https://github.com/JuliaReach/NeuralNetworkAnalysis.jl).

**Expected Results.** The goal is to efficiently implement sparse polynomial zonotopes and the corresponding reachability algorithms. The code is to be documented, tested, and evaluated extensively in benchmarks.

**Literature and related package.** The relevant theory is described in [this research article](https://arxiv.org/pdf/1901.01780). There exists a Matlab implementation in [CORA](https://tumcps.github.io/CORA/) (the implementation of polynomial zonotopes can be found in [this folder](https://github.com/TUMcps/CORA/tree/master/contSet/%40polyZonotope)).


## Efficient two-dimensional geometric operations in LazySets

**Description.** [LazySets](https://github.com/JuliaReach/LazySets.jl) is a Julia library for computing with geometric sets. The focus is on lazy set representations and efficient high-dimensional processing. Still, two-dimensional sets are prevalent and there are known efficient implementations for various types of two-dimensional sets. Many functions currently assume general sets and hence do not apply tricks known for two-dimensional geometry. For example, there is a vast body of literature on efficient polygon algorithms. In this project we are not restricted to polygons, and we want to support lazy operations as well.

**Expected Results.** The goal is to implement efficient algorithms for geometry in the plane (sets in two dimensions) from the literature. The code is to be documented, tested, and evaluated in benchmarks.

**Recommended Skills.** Familiarity with Julia and Git/GitHub is mandatory. Familiarity with [LazySets](https://github.com/JuliaReach/LazySets.jl) is recommended. Basic knowledge of geometric terminology is appreciated but not required.

**Related packages.** The [JuliaGeometry](https://github.com/JuliaGeometry) organization has several relevant packages, but only a few relevant functions for basic set types. In this project we aim to add more functionality for more general set types.


## GPU-accelerated reachability for structural mechanics

**Description.** This project aims at pushing the frontier of reachability methods for the class of semi-discrete linear PDEs by use of distributed high-performance computing and GPU computing (the candidate will pick one of those two approaches). Problems considered fall into the category of linearized PDEs from the domain of structural mechanics [1], which, under spatial discretization using the finite-element method ([FEM](https://en.wikipedia.org/wiki/Finite_element_method)), are transformed into a system of second-order (or first-order) linear ODEs typically of the form `Mx''(t) + Kx'(t) + Cx(t) = F(t)` where both `x(0)` and `F(t)` are specified in terms of sets. Note that for a system with `n` degrees of freedom and a box of initial conditions, `2^n` trajectories are required to simulate all possible behaviors only in the vertices. Such approach is intractable if `n` is large. We take a different, set-based approach: solve the dynamical system using the *sets* given in the initial problem formulation, instead of computing individual trajectories.

**Expected Results.** We aim at handling problems with ~10,000 mesh nodes with uncertain initial conditions, subject to external forces that are uncertain but constant over time, or uncertain but piecewise-constant. The computation will be done in *dense time*, i.e. the result should cover *all possible behaviors* for any time point in the time span of interest (the reach-sets are associated to time intervals hence no behavior escapes the flowpipe), for any initial condition and any function that satisfies the constraints.

**Recommended Skills.** Familiarity with [LazySets](https://github.com/JuliaReach/LazySets.jl) is a must. Knowledge of zonotope based [2] and support function based [3] algorithms from the literature would be ideal, see [4] for a general review, but in this project we will only consider linear systems. Basic knowledge about distributed and GPU computing is required, as we will build on existing infrastructure, e.g. [JuliaGPU](https://juliagpu.org/).

**Example tasks:**

- Implement `GLGM06` (zonotopes) on the GPU. The variations with and without order reduction should be considered.

- Implement the `BOX` algorithm (propagation of boxes, without wrapping effect) on the GPU. Distributed computations may use the property that the reach-set at index k can be found directly by diagonalizing the state transition matrix Phi^k, each processor computing an independent sub-sequence [X0, X1, ..., Xk1], [Xk2, ...]. 

- Example benchmark problems are:

    - (i) a clamped beam model from [5], which is a scalable model with very fast oscillations, and we are interested in validating the maximum tension in the bar, and
    
    - (ii) a three-dimensional heat transfer problem of a realistic, large concrete basement where the maximum temperature at any mesh node should not exceed a prescribed value [6].

For related work see the tool XSpeed [7].

**Mentors.** The results will be integrated into an active line of research between Professors [Marcelo Forets](https://github.com/mforets) (Depto. de Matemática y Aplicaciones, Centro Universitario Regional del Este, UdelaR, Uruguay), [Daniel Freire Caporale](https://github.com/dfcaporale) (Instituto de Física, Facultad de Ciencias, UdelaR, Uruguay) and [Jorge Pérez Zerpa](https://github.com/jorgepz) (Instituto de Estructuras y Transporte, Facultad de Ingeniería, UdelaR).

**References:**

<details>
    <summary> Click to see the list of references. </summary>

- [1] Bathe, Klaus-Jürgen. Finite element procedures. Klaus-Jurgen Bathe, 2006.

- [2] Girard, A., Le Guernic, C., & Maler, O. (2006, March). Efficient computation of reachable sets of linear time-invariant systems with inputs. In International Workshop on Hybrid Systems: Computation and Control (pp. 257-271). Springer, Berlin, Heidelberg.

- [3] Le Guernic, Colas, and Antoine Girard. [Reachability analysis of hybrid systems using support functions.](https://link.springer.com/content/pdf/10.1007/978-3-642-02658-4_40.pdf). International Conference on Computer Aided Verification. Springer, Berlin, Heidelberg, 2009.

- [4] Althoff, Matthias, Goran Frehse, and Antoine Girard. ["Set Propagation Techniques for Reachability Analysis."](https://www.annualreviews.org/doi/abs/10.1146/annurev-control-071420-081941) Annual Review of Control, Robotics, and Autonomous Systems 4 (2020).

- [5] Malakiyeh, Mohammad Mahdi, Saeed Shojaee, and Klaus-Jürgen Bathe. "The Bathe time integration method revisited for prescribing desired numerical dissipation." Computers & Structures 212 (2019): 289-298.

- [6] Tahersima, Mohammad, and Paul Tikalsky. "Finite element modeling of hydration heat in a concrete slab-on-grade floor with limestone blended cement." Construction and Building Materials 154 (2017): 44-50.

- [7] Ray, R., Gurung, A., Das, B., Bartocci, E., Bogomolov, S., & Grosu, R. (2015, November). XSpeed: Accelerating reachability analysis on multi-core processors. In Haifa Verification Conference (pp. 3-18). Springer, Cham.
    
</details>

