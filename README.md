# :bulb: :notebook: Project Ideas: Contributing to the JuliaReach ecosystem roadmap

## :fast_forward: Distributed and GPU Verification of Semi-Discrete PDEs

**Description.** This project aims at pushing the frontier of reachability methods for the class of semi-discrete linear PDEs by use of distributed high-performance computing and GPU computing (the candidate will pick one of those two approaches). Problems considered fall into the category of linearized PDEs from the domain of structural mechanics [1], which, under spatial discretization using the finite-element method ([FEM](https://en.wikipedia.org/wiki/Finite_element_method)), are transformed into a system of second-order (or first-order) linear ODEs typically of the form `Mx''(t) + Kx'(t) + Cx(t) = F(t)` where both `x(0)` and `F(t)` are specified in terms of sets. Note that for a system with `n` degrees of freedom and a box of initial conditions, `2^n` trajectories are required to simulate all possible behaviors only in the vertices. Such approach is intractable if `n` is large. Hence we take a different, set-based approach, integrating with *sets* instead of *numbers*.

**Expected Results.** We aim at handling problems with ~10,000 mesh nodes with uncertain initial conditions, subject to external forces that are uncertain but constant over time, or uncertain but piecewise-constant. The flowpipe computation should be done in *dense time*, i.e. the result should cover *all possible behaviors* for any time point in the time span of interest, and for any initial condition and any function that satisfies the constraints.

**Recommended Skills.** Familiarity with `LazySets.jl` is a must. Zonotope based and support function based algorithms from the literature would be ideal [3], [4], [5]. Basic knowledge of GPU computing will be required, as we will build on existing Julia infrastructure [3]

**Example tasks.** An example task is to port the `BOX` algorithm from ReachabilityAnalysis.jl to work with GPUs. Two test models will be considered: (i) the clamped beam model from [4], which is a scalable model with very fast oscillations, and (ii) a three-dimensional heat transfer problem of a realistic, large concrete basement.

**Mentors.** The results will be integrated into an ongoing linea of reseacrh between Prof. [Marcelo Forets](https://github.com/mforets) (Depto. de Matemática y Aplicaciones, Centro Universitario Regional del Este, UdelaR, Uruguay), [Daniel Freire Caporale](https://github.com/dfcaporale) (Instituto de Física, Facultad de Ciencias, UdelaR, Uruguay) and [Jorge Pérez Zerpa](https://github.com/jorgepz) (Instituto de Estructuras y Transporte, Facultad de Ingeniería, UdelaR).

**References:**

- [1] Bathe, Klaus-Jürgen. "[Conserving energy and momentum in nonlinear dynamics: a simple implicit time integration scheme.](https://www.sciencedirect.com/science/article/abs/pii/S0045794906003099)" Computers & structures 85.7-8 (2007): 437-445.

- [2] Le Guernic, Colas, and Antoine Girard. [Reachability analysis of hybrid systems using support functions.](https://link.springer.com/content/pdf/10.1007/978-3-642-02658-4_40.pdf). International Conference on Computer Aided Verification. Springer, Berlin, Heidelberg, 2009.

- [3] Girard, A., Le Guernic, C., & Maler, O. (2006, March). Efficient computation of reachable sets of linear time-invariant systems with inputs. In International Workshop on Hybrid Systems: Computation and Control (pp. 257-271). Springer, Berlin, Heidelberg.

- [4] https://juliagpu.org/

## :money_mouth_face: Programs with external funding

Google summer of Code (GSoC) and Julia Seasons of Contributions (JSoC) are seasonal programs for funding and/or
mentoring students and other developers to contribute to the open source ecosystem.

If you have a record of contributions to the JuliaReach ecosystem, it is possible for you to apply to such programs which generally take place between june and august of each year. Please note that the selection bar is quite high: successful candidates are expected to be familiar with the development workflow (github, git, julia language) and should have an equivalent of a master's or phd degree in the scientific domain of the proposal.

For additional information see https://julialang.org/jsoc/
