# Traveling Salesman Problem (TSP) Optimization

**Author:** Mohamed Elafifi  
**Student ID:** 22066939  
**Course:** Advanced Intelligent Systems Optimization (AISO)

## Project Overview

This project implements and compares two metaheuristic optimization algorithms for solving the Traveling Salesman Problem (TSP):
- **Genetic Algorithm (GA)**
- **Simulated Annealing (SA)**

The implementation includes comprehensive performance analysis across different problem sizes (10, 20, 30, 40, and 50 cities) to evaluate solution quality, execution time, and scalability.

## Project Structure

```
AISO_Assessment/
├── cities.csv                          # Dataset with 50 cities (X, Y coordinates)
├── Genetic Algorithm TSP.ipynb         # GA implementation and experiments
├── Simulated Annealing TSP.ipynb       # SA implementation and experiments
├── Comparison.ipynb                    # Comparative analysis and visualizations
├── GA TSP RESULTS.csv                  # Genetic Algorithm results
├── SA TSP RESULTS.csv                  # Simulated Annealing results
├── Full Results GA.ipynb               # Detailed GA results analysis
├── Full Results for SA.ipynb           # Detailed SA results analysis
├── Genetic Algorithm old.ipynb         # Previous GA implementations
├── simulated annealing old algs.ipynb  # Previous SA implementations
├── Unusued Algorithms.ipynb            # Experimental algorithms
└── README.md                           # Project documentation
```

## Problem Statement

The Traveling Salesman Problem seeks to find the shortest possible route that:
1. Visits each city exactly once
2. Returns to the starting city
3. Minimizes the total travel distance

This is an NP-hard combinatorial optimization problem, making metaheuristic approaches ideal for finding near-optimal solutions in reasonable time.

## Algorithms Implemented

### 1. Genetic Algorithm (GA)

**Key Features:**
- Population-based evolutionary approach
- Tournament selection for parent choosing
- Order crossover (OX) for offspring generation
- Mutation through random city swapping
- Nearest neighbor heuristic for initial population seeding

**Parameters:**
- Population Size: 100
- Generations: 2000
- Mutation Rate: 0.01
- Tournament Size: 5
- Elitism: Top 10% preserved

### 2. Simulated Annealing (SA)

**Key Features:**
- Single-solution trajectory-based approach
- Temperature-based acceptance probability
- 2-opt swap neighborhood generation
- Nearest neighbor heuristic for initial solution
- Best starting city selection strategy

**Parameters:**
- Initial Temperature: 1000
- Cooling Rate: 0.995
- Minimum Temperature: 0.01
- Neighborhood: 2-opt swaps

## Results Summary

### Solution Quality

| Cities | SA Distance | GA Distance | Winner |
|--------|-------------|-------------|--------|
| 10     | 301.95      | 301.95      | Tie    |
| 20     | 450.77      | 445.25      | **GA** |
| 30     | 536.77      | 489.42      | **GA** |
| 40     | 573.40      | 629.75      | **SA** |
| 50     | 597.06      | 602.52      | **SA** |

### Execution Time

| Cities | SA Time    | GA Time     | Speed Ratio |
|--------|------------|-------------|-------------|
| 10     | 0.0177s    | 45.27s      | 2557.7x     |
| 20     | 0.0444s    | 46.85s      | 1055.1x     |
| 30     | 0.0847s    | 54.46s      | 642.9x      |
| 40     | 0.5721s    | 56.30s      | 98.4x       |
| 50     | 0.8664s    | 65.93s      | 76.1x       |

### Key Findings

**Solution Quality:**
- GA finds better solutions in 2/5 cases (20 and 30 cities)
- SA finds better solutions in 2/5 cases (40 and 50 cities)
- Average difference: negligible (~3%)

**Execution Speed:**
- SA is dramatically faster (76x - 2558x)
- Speed advantage decreases with problem size
- SA suitable for time-critical applications

**Trade-off Analysis:**
- **GA:** Better for solution quality when time is flexible
- **SA:** Better for fast, near-optimal solutions in real-time scenarios

## Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib jupyter
```

### Running the Notebooks

1. **Individual Algorithm Experiments:**
   ```bash
   jupyter notebook "Genetic Algorithm TSP.ipynb"
   jupyter notebook "Simulated Annealing TSP.ipynb"
   ```

2. **Comparative Analysis:**
   ```bash
   jupyter notebook "Comparison.ipynb"
   ```

### Dataset

The `cities.csv` file contains 50 cities with X,Y coordinates:
- Format: `City, X, Y`
- Coordinate range: [0, 100]
- Used for all experiments with subsets (10, 20, 30, 40, 50 cities)

## Visualizations

The project includes:
- City coordinate scatter plots
- Route visualization before/after optimization
- Convergence graphs (fitness over iterations/generations)
- Side-by-side performance comparisons
- Quality vs. runtime trade-off analysis

## Implementation Details

### Common Functions

```python
calculate_distance(route)          # Euclidean distance calculation
create_nearest_neighbor_route()    # Greedy heuristic initialization
best_nearest_neighbor_route()      # Best starting city selection
```

### GA-Specific Functions

```python
create_initial_population()        # Random route generation
calculate_fitness()                # Inverse distance fitness
selection()                        # Tournament selection
crossover()                        # Order crossover (OX)
mutate()                          # Random swap mutation
```

### SA-Specific Functions

```python
create_initial_route()            # Random initial solution
get_neighbors()                   # 2-opt swap generation
acceptance_probability()          # Metropolis criterion
cooling_schedule()                # Exponential cooling
```

## Experimental Setup

Each algorithm was tested on:
- **Problem Sizes:** 10, 20, 30, 40, 50 cities
- **Trials:** Multiple runs per configuration
- **Metrics:** Final distance, execution time, convergence rate
- **Initialization:** Best nearest neighbor starting point

## Conclusions

1. **No Clear Winner:** Both algorithms have strengths depending on requirements
2. **Quality vs Speed:** Classic optimization trade-off clearly demonstrated
3. **Scalability:** SA scales better with problem size
4. **Practical Choice:**
   - Use **SA** for real-time/embedded systems
   - Use **GA** for offline optimization where quality matters most

## References

- Genetic Algorithms: Holland, J.H. (1992)
- Simulated Annealing: Kirkpatrick et al. (1983)
- TSP Problem: Traveling Salesman Problem benchmarks

## Contact

**Mohamed Elafifi**  
Student ID: 22066939  
Course: AISO Assessment

---

*Last Updated: December 2025*
