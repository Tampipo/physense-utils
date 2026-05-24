# physense-utils

Shared utilities for the [Physense](https://github.com/you/physense-web) simulation platform.

## Contents

- **constants** — Fundamental physical constants (CODATA 2022, SI units)
- **grids** — Uniform 1D and 2D simulation grids
- **fft** — FFT helpers with physical normalisation
- **functions** — Common mathematical functions (Gaussian, sinc, Heaviside)

## Installation

```bash
pip install git+https://github.com/you/physense-utils
```

For development:

```bash
git clone https://github.com/you/physense-utils
cd physense-utils
pip install -e ".[dev]"
```

## Running tests

```bash
pytest
```

## Usage

```python
from physense_utils import Grid1D, gaussian, HBAR, fft1d, fft_frequencies

grid = Grid1D(x_min=-10.0, x_max=10.0, n_points=512)
psi = gaussian(grid.x, x0=0.0, sigma=1.0)
Psi = fft1d(psi, grid.dx)
k = fft_frequencies(grid.n_points, grid.dx)
```

## Design principles

- Pure numpy/scipy — no web dependencies
- Immutable grid objects
- Physical normalisation conventions documented explicitly
- 100% test coverage
