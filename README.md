# Minimal Subset Optimizer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://opensource.org/licenses/MIT)

## Overview

Minimal Subset Optimizer is a small Python library designed to extract a minimal subset from a given set, optimizing a given (set of) objective(s). Based on the [DEAP library](https://deap.readthedocs.io/en/master/).

## Features

- **Subset Extraction:** Automatically identifies and extracts a minimal subset from the input set optimizing given objective(s).
- **Multi-objective Optimization:** Optimizes the subset based on a provided objective or a set of objectives.
- **Highly Customizable:** Allows for customization of the crossover, mutation and selection functions (as long as they are contained in the DEAP library.


## Usage
This package is used by [TraP-GA](https://github.com/lavakin/TraP-GA), you might want to have a look.
### Getting optimized solutions and pareto front:
```python
# Example Usage
from set_subset_optimizer import SubsetOptimizer

pop,pareto_front = GA_select.run_minimizer(num_of_elements_in_the_set,fitness_function,stats_by,stats_names_list, 
                  eval_func_kwargs=eval_func_kwargs=,
                  mutation_rate = 0.001,crossover_rate = 0.02, 
                  pop_size = 150, num_gen = num_generations, num_islands = 8, mutation = "bit_flip" , 
                  crossover =  "uniform_partialy_matched",
                  selection = "SPEA2",frac_init_not_removed = 0.005)
```

```python
res_fit = np.array([end_evaluate_individual(x) for x in pop])

pop = np.array(pop)
par = np.array([list(x) for x in pareto_front[0]])
par_fit = np.array([end_evaluate_individual(x) for x in par])
```

### Plotting the pareto front
```python
GA_utils.plot_pareto(ress,par_fit,output_folder)
```
### Extracting a final minimizing subset
```python
GA_utils.get_results(pop,res_fit,output_folder,name_of_elements_of_the_set)
```
