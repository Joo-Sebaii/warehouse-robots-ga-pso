# Warehouse Robots: Grid Simulation and Task Allocation (GA vs PSO)

A Python and Jupyter Notebook project covering multi-agent warehouse robot simulation and optimization-based task allocation.

The project consists of two parts:

- **Part A – Warehouse Robot Grid Simulation:** A 6×6 grid where robots with limited energy collect packages, avoid occupied cells, and handle collisions when multiple robots target the same cell. The simulation compares different robot counts and package densities.
- **Part B – Task Allocation:** Assigning six tasks to three robots to minimize the makespan (the maximum workload assigned to any robot). The problem is solved using a Genetic Algorithm (GA) and Particle Swarm Optimization (PSO), then checked against exhaustive search.

**Technologies:** Python, Jupyter Notebook, NumPy, Matplotlib.

## Part A – Warehouse Robot Simulation

### Simulation Rules

- Grid size: 6×6.
- Initial configuration: 4 robots and 8 packages placed on distinct cells.
- Each robot starts with 5 energy units.
- Robots move randomly up, down, left, or right, subject to grid boundaries and occupied-cell restrictions.
- Each move costs 1 energy unit.
- Collecting a package gives the robot 3 additional energy units, and the package disappears.
- If two or more robots target the same cell during a step, they remain in place and each loses 1 additional energy unit, resulting in a total cost of 2 energy units per involved robot.
- Each contested cell counts as one collision.
- Robots with energy less than or equal to zero are removed from the simulation.

### Experimental Results

The following results represent the reported averages across 200 runs of 40 steps each.

| Robots | Package Density | Packages Available | Avg. Packages Collected | Avg. Collisions | Packages per Robot |
|---:|---|---:|---:|---:|---:|
| 2 | Low | 4 | 0.83 | 0.10 | 0.41 |
| 2 | High | 12 | 3.83 | 0.15 | 1.92 |
| 4 | Low | 4 | 1.55 | 0.66 | 0.39 |
| 4 | High | 12 | 6.29 | 0.91 | 1.57 |

### Discussion

Increasing the number of robots improves total package collection, but it also increases interference between robots.

- With 4 robots, the system collects more packages overall than with 2 robots.
- Average collisions increase as the number of robots increases.
- Packages collected per robot can decrease when more robots compete for the same space and resources.
- Higher package density generally improves package collection by providing more opportunities for robots to replenish their energy.

These results illustrate the trade-off between total system productivity and coordination overhead in multi-agent environments.

## Part B – Task Allocation: GA vs PSO

### Problem Definition

The goal is to assign six tasks to three robots while minimizing the **makespan**, defined as the largest total workload assigned to any robot.

Task workloads:

```python
[4, 7, 3, 8, 5, 6]
```

- Number of tasks: 6
- Number of robots: 3
- Theoretical lower bound for the makespan: 11

### Results

| Method | Best Makespan | Optimal? |
|---|---:|---|
| Genetic Algorithm (GA) | 12 | No |
| Particle Swarm Optimization (PSO) | 11 | Yes |
| Exhaustive Search | 11 | Yes |

Exhaustive search evaluates all \(3^6 = 729\) possible task-to-robot assignments and confirms that the optimal makespan is 11.

In this reported experiment, PSO reaches the optimal makespan, while the Genetic Algorithm finds a makespan of 12. This illustrates how different optimization methods can perform differently on the same task allocation problem.

## How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/Joo-Sebaii/warehouse-robots-ga-pso.git
cd warehouse-robots-ga-pso
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Launch Jupyter Notebook

Open the notebook included in the repository using Jupyter Notebook or JupyterLab.

For example:

```bash
jupyter notebook
```

Then open the relevant `.ipynb` file.

**Note:** Exact results may depend on the random seeds, implementation details, and package versions. The reported results should be reproducible only if the notebook uses the corresponding code and random-seed configuration.

## Project Structure

The repository structure may look like this:

```text
warehouse-robots-ga-pso/
├── Worksheet_1.ipynb
├── README.md
└── requirements.txt
```

The notebook contains the implementation and experiments for the warehouse robot simulation and task allocation algorithms.

## Requirements

- Python 3
- NumPy
- Matplotlib
- Jupyter Notebook

Install the required packages with:

```bash
pip install numpy matplotlib notebook
```

## Learning Objectives

- Model multi-agent interactions in a grid environment.
- Investigate energy constraints, package collection, and robot collisions.
- Compare performance under different robot counts and package densities.
- Implement Genetic Algorithm and Particle Swarm Optimization approaches.
- Evaluate optimization results against exhaustive search.
- Analyze the trade-off between system-level performance and resource allocation.

---

**Project:** Warehouse Robots – Grid Simulation and Task Allocation  
**Author:** Youssef Mohamed Mahmoud  
**GitHub:** [Joo-Sebaii](https://github.com/Joo-Sebaii)