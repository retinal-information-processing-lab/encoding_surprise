# encoding_surprise
Repository containing data and code for PLOS CompBio 2024 paper, "Encoding surprise by retinal ganglion cells", by Danica Despotović, Corentin Joffrois, Olivier Marre, and Matthew Chalk.

This repository contains the following folders:
- data, containing spike times (1 file per cell), for original and repeated experiment 
- code, for plotting figures presented in the paper

## Data description

The spike times files are in hdf format and have 2 fields:
- stimulus X (Nx2 matrix, where X(:,1) are timestamps in seconds, and X(:,2) represents stimulus values (binary, 0 or 1, where 1 corresponds to a bright flash)
- spike times S, in seconds

The used MEA sample rate in both experiments is 20 kHz.

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

### Plotting figures

To reproduce the figures from the paper, the script ```demo_plot()``` can be used.

## Notes

The cell types clustering was performed using code available in the following repository by Francesco Trapani: https://github.com/jagorn/MEA-Analysis/tree/master



