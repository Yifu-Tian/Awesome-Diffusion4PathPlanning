# Awesome-Diffusion4PathPlanning

[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

A Collection of Diffusion for Path Planning Papers, Toolboxes and Notes.

**Outline**
- [Introduction](#0-introduction)
- [Foundational Theories and Methods](#1-foundational-theories-and-methods)
- [Diffusion Models for Path Planning Applications](#2-diffusion-models-for-path-planning-applications)
- [Diffusion Models for Optimization](#3-diffusion-models-for-optimization)
- [Diffusion Models for Constraint-guided Behavior Synthesis](#4-diffusion-models-for-constraint-guided-behavior-synthesis)
- [Other Diffusion-Related Works](#5-other-diffusion-related-works)

## 0. Introduction
Path Planning is a widely discussed topics in various domains such as robotics, autonomous driving and navigation systems. Classic methods including search-based, sampling-based and optimization-based methods are typically limited by increasing planning time as the complexity of the environment increases. 

Diffusion models, originally developed for generative tasks like image synthesis, have shown promising results applying to path planning. The diffusion models initially add noise to data in multiple steps, progressively corrupting the input until it becomes pure noise. During the reverse process, the model learns to gradually denoise the corrupted data to recover the original structure. This mechanism, known as the denoising process, allows diffusion models to generate high-quality outputs from noisy inputs. In the context of path planning, this process can be adapted to generate optimal or feasible paths, especially in environments with uncertain or dynamic obstacles and some other nonlinear constraints.

<p align="center">
<img width="620" height="480" alt="image" src="https://github.com/user-attachments/assets/c7e1b589-af23-4ce8-8d77-be6cbd781bcc" />
</p>

The **Awesome-Diffusion4Planning** repository serves as a comprehensive collection of resources focused on the application of diffusion models in path planning tasks. 

## 1. Foundational Theories and Methods
This section includes essential papers that lay the groundwork for diffusion models in path planning.
|Paper|Task|Methods|Contributions|Limitations|Note|
| --- | --- | --- | --- | --- | --- |
| [Planning with Diffusion for Flexible Behavior Synthesis](https://arxiv.org/abs/2205.09991) | Trajectory planning for robotic systems using DDPM. The task focuses on generating long-horizon, flexible behavior plans for robots, particularly when in dynamic environments or sparse reward settings| DDPM, conditional sampling, probabilistic trajectory representation | Diffuser, Long-Horizon Planning, Flexible Planning with Task Compositionality | Slow Plan Generation, Computation Overhead, Dependency on High-Quality Training Data, Hyperparameter Sensitivity| * |
| [Diffusion Policy: Visuomotor Policy Learning via Action Diffusion](https://arxiv.org/abs/2303.04137) |  The task involves generating robot behavior based on visual observations and manipulating objects via actions. The policy is designed for tasks where high precision and multimodal action distributions are required, such as robot manipulation tasks | DDPM, Visual Conditioning, Time-series Diffusion Transformer | Multimodal Action Distributions, High-dimensional Action Spaces, Stable Training, Receding Horizon Control and Visual Conditioning | Computational Costs, Inference Latency, Data Dependency, Hyperparameter Sensitivity for Transformers | * |
| [Motion Planning Diffusion: Learning and Planning of Robot Motions with Diffusion Models](https://arxiv.org/abs/2308.01557) | The task is to find a feasible, smooth, and collision-free path between a start and goal configuration for a robot. This involves optimizing the trajectory of the robot in high-dimensional space while avoiding obstacles. The goal is to generate trajectories that can be executed by a robot’s controller | Diffusion Models, Motion Planning as Inference, Gradient-guided Sampling | Diffusion as a Generative Model for Trajectories, Motion Planning as Inference, Effective Handling of Multimodal Trajectories, Generalization to Unseen Obstacles, Comparison with Baselines | Computational Costs, Inference Time, Dependency on Expert Data, Complexity in Real-World Applications | * |

## 2. Diffusion Models for Path Planning Applications
This section highlights the application of diffusion models specifically in path planning for robots.
|Paper|Task|Methods|Contributions|Limitations|Note|
| --- | --- | --- | --- | --- | --- |
| [DiPPeR: Diffusion-based 2D Path Planner applied on Legged Robots](https://arxiv.org/html/2310.07842v2) | The task is to generate feasible and efficient 2D paths for quadrupedal robots in complex environments | Image-Conditioned DDPM, CNN-based Diffusion Planner | Scalable Dataset Generator, Efficient and Scalable Path Planner, Real-World Deployment, Generalization to Different Environments| Trajectory Length Limitation, Sensitivity to Path Length Estimation, Inference Time for Complex Environments | * |
| [DiPPeST: Diffusion-based Path Planner for Synthesizing Trajectories Applies on Quadruped Robots](https://arxiv.org/abs/2405.19232) | The task is to generate both global and local paths for quadruped robots, which are required to navigate complex environments | Image-Conditioned DDPM, Visual Servoing, Waypoint Tracking and Local Refinement | Zero-Shot Adaptation for Local Planning, Real-Time Local Path Refinement, Visual Servoing Framework | Re-Planning Speed, Limited Goal Reaching in Complex Environments, Dependence on Camera View | * |
| [ViT-A*: Legged Robot Path Planning using Vision Transformer A*](https://arxiv.org/abs/2310.07525) | The task is to generate global paths for quadrupedal robots (legged robots), which involve navigating complex environments by generating paths from 2D maps with obstacles | ViT-based Neural A*, Guidance Map, Differentiable A* Path Planning | Vision Transformer Integration, Neural A* Path Planner, Real-World Quadrupedal Robot Testing | Map Size Dependency, Training Data Dependence, Inference Time | * |
| [LDP: A Local Diffusion Planner for Efficient Robot Navigation and Collision Avoidance](https://arxiv.org/abs/2407.01950) | The task is to generate efficient local motion plans for robots that avoid collisions in dynamic and complex environments | Conditional Diffusion Models (DDPM), Expert Policy Data, FiLM Conditioning | Local Diffusion Planner (LDP), Global Path Integration, Expert Data Diversity, Improved Generalization, Real-World Deployment | Data Diversity, Inference Speed, Complexity in Dynamic Environments, Overhead from Global Path Integration | * |

## 3. Diffusion Models for Optimization
These works apply diffusion models to enhance planning and trajectory optimization, ensuring safe, efficient, and guaranteed solutions, especially in non-convex or constrained environments.
|Paper|Task|Methods|Contributions|Limitations|Note|
| --- | --- | --- | --- | --- | --- |
| [SafeDiffuser: Safe Planning with Diffusion Probabilistic Models](https://arxiv.org/abs/2306.00148) | The task is to generate safe, collision-free trajectories for robots using diffusion probabilistic models (Diffusers), while maintaining safety guarantees | DDPM, Finite-Time Diffusion Invariance, Control Barrier Functions (CBFs), Quadratic Programming (QP) | SafeDiffuser Framework, Finite-Time Diffusion Invariance, Addressing Local Traps, Robust Safe Planning, Application to Real-World Tasks | Computational Complexity, Limited Generalization in Highly Dynamic Environments, Trade-off Between Safety and Performance, Data Dependency | * |
| [Efficient and Guaranteed-Safe Non-Convex Trajectory Optimization with Constrained Diffusion Model](https://arxiv.org/pdf/2403.05571v1) | The task is to solve trajectory optimization problems in robotics, where a robot must navigate complex environments while satisfying both dynamic constraints (like velocity and acceleration limits) and safety constraints (such as collision avoidance) | Constrained Diffusion Model (CDM), Surrogate Optimization, Gradient-Based Solver | Constrained Diffusion for Non-Convex Problems, Improved Efficiency, Parallelizable and Scalable, Verification of Feasibility and Optimality | Data Dependency, Challenges with Complex Constraints, Computational Overhead, Training Time | * |

## 4. Diffusion Models for Constraint-guided Behavior Synthesis
These works focus on incorporating problem constraints into trajectory optimization and planning for tasks such as UAV path planning and other constraint-based scenarios.
|Paper|Task|Methods|Contributions|Limitations|Note|
| --- | --- | --- | --- | --- | --- |
| [CGD: Constraint-Guided Diffusion Policies for UAV Trajectories Planning](https://arxiv.org/abs/2405.01758) | The task is to generate dynamic, collision-free, and feasible trajectories for UAVs (Unmanned Aerial Vehicles) in complex environments with changing constraints | Constraint-Guided Diffusion (CGD), Hybrid Learning/Optimization Framework, Block Coordinate Descent-inspired Method | Efficient Generation of Collision-Free Trajectories, Adaptation to Changing Constraint, Performance and Computational Trade-offs, Surrogate Optimization for Dynamic Feasibility, Benchmarking and Real-World Performance | Computational Overhead, Generalization to Highly Dynamic Environments, Dependency on Trajectory Initialization, Scalability for Multi-Agent Systems | [ZH](https://zhuanlan.zhihu.com/p/1903524408749950156) |
| [Aligning Diffusion Model with Problem Constraints for Trajectory Optimization](https://arxiv.org/abs/2504.00342) | The task is to generate optimal trajectories for robots or systems while respecting various constraints, such as goal-reaching, collision avoidance, and adherence to system dynamics | Diffusion Probabilistic Models (DDPMs), Hybrid Loss Function, Re-weighted Constraint Violation Loss | Constraint-Aligned Diffusion Model, Re-weighting Strategy for Constraint Violations, Improved Feasibility, Generalization to New Problem Instances | Computational Complexity, Trade-off Between Feasibility and Performance, Training Time | * |
| [Projected Generative Diffusion Models for Constraint Satisfaction](https://arxiv.org/abs/2402.03559v1) | The task is to generate feasible solutions in the form of trajectories or other outputs that not only conform to a generative model but also strictly adhere to specified constraints or physical principles | Projected Generative Diffusion Models (PGDM), Iterative Projections, Projection Guidance | Constraint-Adaptive Diffusion Model, Feasibility Guarantees, Improved Sampling Quality, Versatility Across Domains, Comparison with Other Methods | Computational Overhead, Difficulty with Non-Convex Constraints, Projection Efficiency, Training Complexity | * |
| [Potential Based Diffusion Motion Planning](https://arxiv.org/abs/2407.06169) | The task is to generate smooth and collision-free trajectories in high-dimensional spaces for robots, overcoming the traditional issues with potential-based motion planning methods | Diffusion Models for Potential Fields, Composability of Potentials, Trajectory-Level Potential Function | Learning-Based Potential Motion Planning, Generalization and Composability, Improved Optimization and Local Minima Avoidance, Practical Application to High-Dimensional Motion | Computational Costs, Scalability with Increased Constraints, Sub-Optimality in Some Scenarios, Difficulty in Real-Time Applications | [ZH](https://zhuanlan.zhihu.com/p/1931356476775077679) |
## 5. Other Diffusion-Related Works
This section includea papers related to diffusion models in areas outside direct path planning applications. 
|Paper|Task|Methods|Contributions|Limitations|Note|
| --- | --- | --- | --- | --- | --- |
| [More Control for Free! Image Synthesis with Semantic Diffusion Guidance](https://openaccess.thecvf.com/content/WACV2023/papers/Liu_More_Control_for_Free_Image_Synthesis_With_Semantic_Diffusion_Guidance_WACV_2023_paper.pdf) |||||[ZH](https://zhuanlan.zhihu.com/p/640631667)|
| [Classifier-Free Diffusion Guidance](https://arxiv.org/abs/2207.12598) |||||[ZH](https://zhuanlan.zhihu.com/p/640631667)|
| [Diffusion Models Beat GANs on Image Synthesis](https://arxiv.org/pdf/2105.05233) |
