# Instructions

This document provides detailed instructions on how to train the model using different budget values and policy gradient methods.



## Prerequisites

Make sure you have the following prerequisites installed:
- Python 3.6 or higher
- Necessary Python packages (you can install them using `pip install -r requirements.txt`)

## Training the Model

```sh
git clone https://github.com/HuuPhat125/cs106.git

cd cs106
```

The training script `train.py` allows you to specify various parameters such as budgets, datasets, maximum episodes, savename, and policy gradient methods. Below are the steps and examples to train the model with different configurations.

### Main parameters

- `budgets`: The budget values for training. Format: 'budget1+budget2'
- `datasets`: The datasets to be used for training. Format: 'dataset1+dataset2'
- `maxepisode`: The maximum number of episodes for training.
- `savename`: The name under which the results will be saved.
- `pg`: The policy gradient method to be used. Possible values: 'reinforce', 'ppo', 'aac'

### Running the Training Script

You can use the following command template to run the training script:

```sh
python train.py --budgets '<budget1>+<budget2>' --datasets '<dataset1>+<dataset2>' --maxepisode <maxepisode> --savename '<savename>' --pg '<pg_method>'
```
Example:

```sh
python train.py --budgets '50+50' --datasets 'reddit1401+reddit1401' --maxepisode 2000 --savename 'reddit1401_1+2_50_reinforce' --pg 'reinforce'
```

Automating Multiple Training Runs
You can automate the process of running multiple training runs with different configurations using a Python script. Below is a sample script:

```python
import os

budgets_list = [20, 30, 50]
pg_methods = ['reinforce', 'ppo', 'aac']

for budget in budgets_list:
    for pg in pg_methods:
        savename = f"reddit1401_1+2_{budget}_{pg}"
        command = (
            f"python train.py "
            f"--budgets '{budget}+{budget}' "
            f"--datasets 'reddit1401+reddit1401' "
            f"--maxepisode 2000 "
            f"--savename '{savename}' "
            f"--pg '{pg}'"
        )
        print(f"Running command: {budget} {pg}")
        os.system(command)
```
## Testing the Model

The testing script test.py allows you to specify various parameters to test the trained model. Below are the steps and examples to test the model with different configurations

Parameters for Testing
- `budgets`: The budget values for testing. Format: 'budget1+budget2+budget3'
- `datasets`: The dataset to be used for testing.
- `modelname`: The name of the trained model to be used for testing.
- `method`: The method to be used for testing. Use 3 for policy method or 1 (default) for random method.
- `multigraphindex`: The indices of the graphs to be used for testing. Format: 'graph1+graph2+graph3'
  
Example command:

```sh
python test.py --budgets '50+50+50' --datasets 'reddit1401' --modelname 'gcnreddit1401_1+2_50_reinforce_2001' --method 3 --multigraphindex 'graph3+graph4+graph5'
```
All the training processes, model evaluations, and obtained results are presented in the two files `train.ipynb` and `test.ipynb`.