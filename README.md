# CS-361-Final-Project
This is a MILP Based Optimisation of EMS Dispatch

## Abstract
Timely access to emergency medical services is
crucial in reducing mortality and improving patient outcomes.
In many Low and Middle Income countries, long wait times
for ambulances pose a significant challenge, often resulting in
adverse health consequences. This paper proposes an approach to
optimise ambulance locations by formulating the problem using
the p-Median model, which can be solved using Mixed Integer
Linear Programming (MILP) techniques, with the objective of
minimising response times. Additionally, we also consider multiobjective optimisation (MOO) case where the aim is to strategically determine the optimal locations for ambulance deployment
while also limiting the number of ambulances deployed. This
allows us to consider both response times and resource efficiency,
both of which are extremely important for LMICs with limited
ambulance availability.

# Problem Formulation

## Single Objective Optimization

This problem formulation is an instantiation, with necessary modifications, of the p-Median problem.

### Nomenclature

| Symbol | Description |
|--------|-------------|
| n      | Total number of patients |
| p      | Total number of EMS Ambulance facilities |
| m      | Total number of possible locations |
| t_{ij} | Time taken for ambulance j to reach patient i |
| x_{ij} | Decision variable for patient i served by ambulance j |
| a_j    | Indicator variable for ambulance location j |

Note that each ambulance has a capacity of 1.

### Objective Function

Minimize the total time taken to reach all patients by assigning them to appropriate ambulances:


### Constraints

1. ∑_{j=1}^{m} x_{ij} = 1 for all i = 1, ..., n
2. x_{ij} ∈ {0, 1} for all i = 1, ..., n and j = i = 1, ..., p
3. ∑_{i=1}^{n} x_{ij} ≤ a_j for all j = 1, ..., m
4. a_j ∈ {0, 1} for all j = 1, ..., m
5. ∑_{j=1}^{m} a_j ≤ p

## Multi-Objective Optimization

In the multi-objective optimization case, we have two objective functions:

1. Minimize ∑_{i=1}^{n} ∑_{j=1}^{p} t_{ij} ⋅ x_{ij}
2. Minimize ∑_{j=1}^{m} a_j

The constraints remain the same as in the single objective case.

We employ the weighted sum method for multi-objective optimization. The objectives are combined as follows:


where w_1 = w_2 = 0.5.

