# HomeBatterySim

## Overview
HomeBatterySim is a simulation toolkit for analyzing the financial and operational benefits of installing a home battery system. It uses real consumption and tariff data (e.g., from Octopus Energy) to estimate potential savings and earnings from battery storage, considering variable import/export rates and battery constraints.

## Features
- Download and process electricity consumption and tariff data from Octopus Energy APIs
- Merge and clean data for simulation
- Simulate battery operation (charge/discharge) based on real price signals
- Estimate annual savings/earnings from battery usage
- Export results for further analysis

## Project Structure
- `get-data.ipynb`: Jupyter notebook to download electricity consumption and tariff data from Octopus Energy, convert JSONs to CSVs, and merge them for simulation.
- `bat-sim.ipynb`: Jupyter notebook to simulate battery operation using merged data and calculate savings/earnings.
- `output.csv`: Merged data file with consumption, buy rate, and sell rate for each interval.
- `simulation_results.csv`: Output of the simulation, showing battery state and financials per interval.
- `historic_data.csv`, `export.csv`, `tariffs.csv`, etc.: Raw and processed data files.
- `apikey.txt`, `e_mpan.txt`, `e_serial.txt`: Local files for API keys and meter details (not tracked in git).

## Setup
1. **Clone the repository** and navigate to the `HomeBatterySim` directory.
2. **Install dependencies** (recommended: use a virtual environment):
   ```bash
   pip install pandas requests jupyter
   ```
3. **Prepare API credentials**:
   - Place your Octopus Energy API key in `apikey.txt`.
   - Place your MPAN in `e_mpan.txt` and meter serial in `e_serial.txt`.

## Usage
### 1. Download and Prepare Data
- Open `get-data.ipynb` in Jupyter.
- Run the notebook to:
  - Download consumption and tariff data from Octopus Energy
  - Convert JSONs to CSVs
  - Merge consumption, buy rate, and sell rate into `output.csv`

### 2. Run the Simulation
- Open `bat-sim.ipynb` in Jupyter.
- Set the `data_filepath` to `output.csv` (or your merged data file).
- Run the notebook to simulate battery operation and calculate annual savings/earnings.
- Results are saved to `simulation_results.csv` and printed in the notebook.

## Requirements
- Python 3.7+
- pandas
- requests
- jupyter

## Notes
- Sensitive files (API keys, raw data) are excluded from version control via `.gitignore`.
- The simulation is based on Tesla Powerwall specs by default, but you can adjust battery parameters in `bat-sim.ipynb`.
- Data files can be large; ensure you have sufficient disk space.

## License
This project is for personal and research use. Please check data provider terms before sharing data or results.
