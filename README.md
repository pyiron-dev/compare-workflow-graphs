# Compare Workflow Graphs
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/pyiron-dev/compare-workflow-graphs/HEAD)

## Current draft
Example of the Python Workflow Definition for a very simple workflow like:
```python
def add_x_and_y(x, y):
    z = x + y
    return x, y, z

def add_x_and_y_and_z(x, y, z):
    w = x + y + z
    return w

x, y, z = add_x_and_y(x=1, y=2)
w = add_x_and_y_and_z(x=x, y=y, z=z)
```
This can be writted as a graph represented with a dictionary of nodes and a list of edges: 
```python
# The keys must be consistent with `target` and `source` in `edges_lst`
nodes_dict = {
    0: add_x_and_y,
    1: add_x_and_y_and_z,
    2: 1,
    3: 2,
}

edges_lst = [
    {'target': 1, 'targetHandle': 'x', 'source': 0, 'sourceHandle': 'x'},
    {'target': 1, 'targetHandle': 'y', 'source': 0, 'sourceHandle': 'y'},
    {'target': 1, 'targetHandle': 'z', 'source': 0, 'sourceHandle': 'z'},
    {'target': 0, 'targetHandle': 'x', 'source': 2, 'sourceHandle': None},
    {'target': 0, 'targetHandle': 'y', 'source': 3, 'sourceHandle': None},
]
```
As an extension to save the nodes and edges to a JSON file, we could write the python functions to a module named `test.py` and then reference them as `test.add_x_and_y` and `test.add_x_and_y_and_z`. 

## Implementations 

| Framework | To Python Workflow Definition | From Python Workflow Definition | 
|:----------|:-----------------------------:|:-------------------------------:|
| aiida     | [aiida-workgraph_to_universal.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/aiida-workgraph_to_universal.ipynb) | [universal_to_aiida-workgraph.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/universal_to_aiida-workgraph.ipynb) |
| jobflow | [jobflow_to_universal.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/jobflow_to_universal.ipynb) | [universal_to_jobflow.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/universal_to_jobflow.ipynb) |
| pyiron_base | [pyiron_base_to_universal.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/pyiron_base_to_universal.ipynb) | [universal_to_pyiron_base.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/universal_to_pyiron_base.ipynb)
| pyiron_workflow | [pyiron_workflow_to_universal.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/pyiron_workflow_to_universal.ipynb) | [universal_to_pyiron_workflow.ipynb](https://github.com/pyiron-dev/compare-workflow-graphs/blob/main/universal_to_pyiron_workflow.ipynb) |
