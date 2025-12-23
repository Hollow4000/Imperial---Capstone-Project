# Imperial---Capstone-Project
Black-Box Optimisation (BBO) Capstone Project
1. Project Overview
This repository contains my work for the Black-Box Optimisation (BBO) Capstone Project, completed as part of the Imperial College Professional Certificate in Machine Learning and AI. The challenge focuses on optimising a set of unknown functions under strict query constraints, where no information about the functional form, gradients or noise structure is available.
The core objective of the BBO capstone is to design a data-efficient query strategy that balances exploration and exploitation in order to identify high-performing inputs with as few evaluations as possible. This mirrors many real-world ML problems where experiments are expensive, slow or irreversible (e.g. hyperparameter tuning, engineering design, scientific experimentation).
This project is directly relevant to applied machine learning roles that require principled decision-making under uncertainty. It has strengthened my understanding of surrogate modelling, acquisition strategies and iterative model refinement—skills that transfer to optimisation, experimentation and model tuning problems in industry.

2. Inputs and Outputs
Inputs
•	The system exposes 8 unknown objective functions, each with a different input dimensionality.
•	Inputs are real-valued vectors constrained to the unit hypercube:

x ∈ [0,1]^d

•	where d varies by function (from 2 to 8).
•	Queries must be submitted in a strict formatted string:

x1-x2-...-xd
•	with each value rounded to six decimal places.

Outputs
•	For each query, the system returns a scalar performance value.
•	The objective function is unknown and treated as a black box.
•	Observations may include noise and are revealed only after submission.
Example submission format:
0.413287-0.928104-0.175602

3. Challenge Objectives
The primary goal of the BBO capstone is to maximise the unknown objective functions using a limited number of sequential queries. Key constraints include:
•	A strict cap on the number of queries per function
•	No access to gradients or analytic structure
•	Delayed feedback after each submission
•	High-dimensional input spaces for later functions
Success is measured by how efficiently high-performing regions are identified rather than by exhaustive exploration.

4. Technical Approach

Overall Strategy
My approach evolves across query rounds, moving from broad exploration toward increasingly model-driven optimisation. I treat the problem as a sequential decision-making task under uncertainty.

First Iteration
•	Emphasis on space-filling exploration
•	Uniform random sampling to obtain initial coverage
•	Limited reliance on modelling due to sparse data

Second Iteration
•	Introduction of Gaussian Process (GP) regression as a surrogate model
•	Use of uncertainty-aware acquisition to guide queries
•	Early balance between exploration and exploitation

Third Iteration (Current)
•	Fully model-based Bayesian Optimisation framework
•	Gaussian Process with ARD Matérn kernel to handle differing relevance across dimensions
•	Upper Confidence Bound (UCB) acquisition function to balance:

o	exploitation of high predicted means
o	exploration of high uncertainty regions
•	Dimension-dependent tuning of the exploration parameter (κ)
•	Low-discrepancy (Sobol) candidate sampling to improve coverage in higher dimensions
•	Explicit avoidance of querying points too close to existing samples

Modelling Choices and Extensions
•	Bayesian methods are used to quantify uncertainty and guide efficient exploration
•	I have considered SVM-based classification as a complementary approach to identify promising vs low-performing regions, particularly for non-linear response surfaces
•	As data grows, I monitor for overfitting and implicitly identify irrelevant dimensions via learned GP length-scales

This section is treated as a living record and will continue to evolve as additional queries are submitted and new modelling insights emerge.
Summary
This repository documents an iterative, principled approach to black-box optimisation under realistic constraints. The project demonstrates not only technical implementation, but also reflective modelling decisions, uncertainty-aware reasoning and disciplined experimentation—core skills for applied machine learning work.


