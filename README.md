# Exam Scheduling Optimization

This repository explores the implementation of optimization models for scheduling exams. We present two distinct scenarios:

1. **Scenario One: Maximum Flow Exam Scheduling Without Special Time Slot Preferences**
2. **Scenario Two: Maximum Flow Exam Scheduling with Special Time Slot Preferences**

## Scenario One: Basic Model

In this scenario, we aim to schedule exams without any specific preferences for time slots. The goal is to maximize the number of exams scheduled.

### Model Components

#### Sets
- $U$: Set of exam subjects.
- $R$: Set of classrooms.
- $T$: Set of time slots.

#### Parameters
- $a_u$: Number of students for subject $u$.
- $c_r$: Capacity of classroom $r$.

#### Variables
- $x_{u,r,t}$: Binary decision variable, equals 1 if subject $u$ is scheduled in classroom $r$ during time slot $t$, otherwise 0.

### Mathematical Model

**Objective Function:**
$$
\text{maximize} \quad \sum_{u \in U} \sum_{r \in R} \sum_{t \in T} x_{u,r,t}
$$
**Constraints:**

1. **Each subject can be scheduled at most once:**
   $$
   \sum_{r \in R} \sum_{t \in T} x_{u,r,t} \leq 1 \quad \forall u \in U
   $$

2. **Classroom capacity:**
   $$
   a_u \cdot x_{u,r,t} \leq c_r \quad \forall u \in U, \forall r \in R, \forall t \in T
   $$

## Scenario Two: Special Time Slot Preferences

In this scenario, Thursday and Friday afternoons are considered ideal and can host up to two exams across all rooms, while weekends can host only one exam across all rooms.

### Model Components

#### Parameters
- $d_t$: Equals 2 if time slot $t$ is either Thursday or Friday afternoon; otherwise, equals 1.

### Additional Constraint for Scenario Two

**Desirable and Undesirable Time Slots:**
$$
\sum_{r \in R} \sum_{u in U} x_{u,r,t} \leq d_t \quad \forall t \in T
$$

## Usage

- **Requirements**: Ensure you have Gurobi installed and a valid license.
- **Running Models**: You can run the models using Python scripts provided in the `scripts` directory.

## Results

Results from running these models will demonstrate the efficiency and effectiveness of each approach, highlighting differences in scheduling based on the constraints introduced by different time slot preferences.

## Contributing

Contributions to this project are welcome. Please fork the repository and submit pull requests with any enhancements, additional models, or corrections.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
