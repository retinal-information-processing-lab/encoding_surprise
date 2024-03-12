# encoding_surprise
Repository containing data and code for PLOS CompBio 2024 paper, "Encoding surprise by retinal ganglion cells", by Danica Despotović, Corentin Joffrois, Olivier Marre, and Matthew Chalk.

This repository contains the following data:
- spike times (1 file per cell), for original and repeated experiment 
- model fit parameters and corresponding correlation coefficient for each model fit 

## Data description

### Spike times

The spike times files are stored in .hdf format and have 2 fields:
- `stimulus`, shaped Nx2, where X(:,1) are timestamps in seconds, and X(:,2) represents stimulus values (binary, 0 or 1, where 1 corresponds to a bright flash
- `spikes`, shaped Mx1, in seconds

The MEA (Multielectrode Array) sample rate used in both experiments is 20 kHz.

### Model fit parameters

Since the parameters of model fit are intended for use with MATLAB, they are saved as .mat files.

The file contains several variables:
- the IDs of cells, corresponding to the original recorded channel before spike sorting
- correlation coefficient, a struct with model's name as fields, each containing a vector of length corresponding to number of cells
- model parameters, a struct with model's name as fields, each containing a vector of length corresponding to number of model parameters

## Code demo

### Loading cell data

To load the spike data from a given cell N, the following code can be used:

```MATLAB
# define path
data_path = '/data/spike_times/';
h5_path = [data_path, 'cell_N.h5'];

# load stimulus and spikes
X = h5read(h5_path, '/stimulus');
S = h5read(h5_path, '/spikes');
```

## Notes

The cell types clustering was performed using code available in the following repository by Francesco Trapani: 

https://github.com/jagorn/MEA-Analysis/tree/master



