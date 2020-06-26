# Logarithmic binning module

This module is for binning data. Linear binning can be done with standard libraries such as `numpy`, but I could not find a logarithmic data binning function, so here it is.


## Content

The module contains one single file, `logbinning.py`, that has the following functions:

- `linbinning()`: linear binning of data

- `logbinning()`: logarithmic binning of data

Directly running the file

```
python logbinning.py
```

will run a tiny tutorial that generates random data according to two distributions (exponential and power law), and bins them with both methods. Plots are shown, that emphasize the utility of the different kinds of binning.


## Requirements

We use Python 3, and import the following libraries: `numpy`, `matplotlib.pyplot`. Matplotlib is only required for the tutorial, but not for importing the functions. 

## Functions

#### `linbinning(values, xmin=None, xmax=None, n=10, align='center')`

Bins linearly the data contained in `values`.

_Returns_ a `numpy array` with 4 columns: `ibin` (index of the bin), `bins` (value of the bin), `histo` (how many entries were found in that bin), `density` (normalizes `histo` so that the integral is unity).

**input:**

`values`: an 1D array or list of data to bin.

`xmin`: lower extremum for the binning. Any value lower than `xmin` is discarded. If `xmin==None`, it is set to the lowest element of `values`.

`xmax`: upper extremum for the binning. Any value higher than `xmax` is discarded. If `xmax==None`, it is set to the highest element of `values`.

`n`: number of bins.

`align`: if `'center'`, every bin is represented with its average value. If `'left'`, every bin is represented with its lower value.


#### `logbinning(values, xmin=None, xmax=None, n=10, align='center')`

Bins logarithmically the data contained in `values`. Given that this function does logarithmic binning, non-positive values cannot be accepted. If negative values are present (or the user gives xmin<=0), the lowest value of the histogram is automatically set to `EPS=1e-6`.

_Returns_ a `numpy array` with 4 columns: `ibin` (index of the bin), `bins` (value of the bin), `histo` (how many entries were found in that bin), `density` (normalizes `histo` so that the integral is unity).

**input:**

`values`: an 1D array or list of data to bin.

`xmin`: lower extremum for the binning. Any value lower than `xmin` is discarded. If `xmin==None`, it is set to the lowest element of `values`. If `xmin<=0`, `xmin` is set to `EPS=1e-6`.

`xmax`: upper extremum for the binning. Any value higher than `xmax` is discarded. If `xmax==None`, it is set to the highest element of `values`.

`n`: number of bins.

`align`: if `'center'`, every bin is represented with its average value. If `'left'`, every bin is represented with its lower value.

