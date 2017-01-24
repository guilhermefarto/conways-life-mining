# conways-life-mining

[Processing](https://processing.org/) project for

* (i) [Conway's Life Mining](#conways-life-mining) simulation and data export ([examples](#all-examples))

## Dependencies

The .py project adopts [Numpy](http://www.numpy.org/) - a fundamental package for scientific computing with Python - and [Matplotlib](http://matplotlib.org/) - a Python 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms.

First, upgrade `pip`to the latest version by executing the command in the prompt `python -m pip install --upgrade pip`.

It is possible to the full SciPy stack - a scientific package that contains several components, e.g., Numpy, Simpy, and Pandas - from [Python Package Index](https://pypi.python.org/pypi/pip) (PIP).

Then install the SciPy stack packages with `pip install --user numpy scipy matplotlib ipython jupyter pandas sympy nose`.

For Windows users, the SciPy [official page](https://www.scipy.org/install.html) recommends the use of [pre-built Windows installers](http://www.lfd.uci.edu/~gohlke/pythonlibs/) for many Python packages, including all of the core SciPy stack. Some pre-built Windows installers can ben also downloaded from [this link](https://sourceforge.net/projects/scipy/) and [this link](https://sourceforge.net/projects/scipy/files/scipy/0.16.1/).

To install the `Matplotlib` dependency from [Python Package Index](https://pypi.python.org/pypi/pip) (PIP), execute the command in the prompt `python -m pip install matplotlib`.

Other dependencies of this project are native to Python platform:

```python
  import os
  import errno
  import argparse
  import time
```

## Contact / License

Feel free to contact me by mail: guilherme.farto@gmail.com

---

<a name="conways-life-mining"></a>
## Conway's Life Mining (conways-life-mining.py)
> Based on Conway's Game of Life - a cellular automaton devised by the British mathematician John Horton Conway in 1970

Usage:
```python
python conways-life-mining.py [-h] -c CELLS [-p PATH] [-ni] [-d] [-cn] [-lc LIVE_CELL_NOTATION] [-dc DEAD_CELL_NOTATION] [-g GENERATIONS]
```

The arguments shoud be:

`-c CELLS, --cells CELLS` *(required)*
* path of the initial cell pattern (`.cells` file)

`-p PATH, --path PATH` *(required)*
* path of the directory for simulation and data export

`-ni, --no_images` *(optional but default value is True)*
* ignore export of images for generations

`-d, --data` *(optional but default value is False)*
* export of data for generations

`-cn, --cells_notation` *(optional but default value is False)*
* uses cell notation for data export

`-lc LIVE_CELL_NOTATION, --live_cell_notation LIVE_CELL_NOTATION` *(optional but default value is 'O')*
* live cell notation for data export

`-dc DEAD_CELL_NOTATION, --dead_cell_notation DEAD_CELL_NOTATION` *(optional but default value is '.')*
* dead cell notation for data export

`-g GENERATIONS, --generations GENERATIONS` *(optional but default value is 50)*
* number of generations to be computed

### Main concepts of Conway's Game of Life (introduction and concepts)

asdf

### Proposed approach for Conway's Life Mining (introduction and concepts)

* **Main functions of the proposed approach**

```python
  def create_cells_map(rows, cols): ...
  def extract_initial_cell(path): ...
  def insert_cell_map(cells_map, data): ...

  def export_cell_map(cells_map, index): ...
  def export_cell_map_data(cells_map, index, header): ...

  def clean_cell_map(cells_map): ...

  def filter_array(a_where, indices): ...
  def remove_zero_rows(cells_map): ...
  def remove_zero_cols(cells_map): ...

  def expand_cell_map(cells_map, size=1): ...

  def conways_step(cells_map): ...
  def check_rules(cells_map, rowId, colId): ...
  def cell_is_alive(cells_map, rowId, colId): ...
  def count_neighbors(cells_map, rowId, colId): ...

  def get_max_cols(lines): ...
  def get_max_rows(lines): ...

  def mkdir_p(path): ...
```

* **Steps of the proposed approach**

#### 1. Extract data of the initial life (or generation) from the `.cells` file (`-c CELLS, --cells CELLS` argument)

```python
  data = extract_initial_cell(INITIAL_CELLS)
```

#### 2. Create a new array (also called a map) based on the size needed for the instantiation of the life (or generation) extracted from the `.cells` file

```python
  cells_map = create_cells_map(get_max_rows(data), get_max_cols(data))
```

#### 3. Insert life (or generation) on the map

```python
cells_map = insert_cell_map(cells_map, data)
```

#### 4. Iterate from the first to the desired generation (by default, 50, or equal to the value of `-g GENERATIONS, --generations GENERATIONS` argument)

```python
  last_index = NUMBER_GENERATIONS

  for i in range(1, last_index + 1):
```

#### 4.1. Clear, if necessary, rows or columns (upper, lower and side edges) containing only zero values - to optimize the generation of images and data with relevant values

```python
  cells_map = clean_cell_map(cells_map)
```

#### 4.2. Expand the map structure (in the top, bottom, and side corners) to one level - to allow expansion of life (or generation) pattern if necessary

```python
  cells_map = expand_cell_map(cells_map, 1)
```

#### 4.3. Export of the images and data from the generations (if configured by `-ni, --no_images` and `-d, --data` arguments - respectively, True and False as default values)

> For image export

```python
  export_cell_map(cells_map, i)
```

> For data export

```python
  export_cell_map_data(cells_map, i, header)
```

#### 4.4. Perform a step in generation based on the Conway's Game of Life rules

> Conway's 23/3 rules: (i) two or three neighbors = living cells will remain alive, (ii) three neighbors = dead cells will become alive (born), and (iii) otherwise cells die

```python
  cells_map = conways_step(cells_map)
```

<a name="all-examples"></a>
## Examples

<a name="conways-life-mining-examples-1"></a>
### > asdf

asdf

