# README.md

# MountainSort to Phy Extension

This repository provides tools to integrate
- MountainSort spike sorting 
- with the Phy curation environment.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Modules](#modules)
- [Configuration](#configuration)
- [Contributing](#contributing)
- [License](#license)

## Installation

1. **Clone the repository:**
   ```sh
   git clone https://github.com/yourusername/mountainsort-to-phy.git
   cd mountainsort-to-phy
   ```

2. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

3. **Add the Phy plugins:**
   Copy the plugins to your Phy plugins directory. This is typically located at `~/.phy/plugins/`.
   ```sh
   mkdir -p ~/.phy/plugins
   cp plugins/* ~/.phy/plugins/
   ```

4. **Update your Phy configuration:**
   Edit your `~/.phy/phy_config.py` to include the new plugins:
   ```python
   c.TemplateGUI.plugins = ['MSCurationTagsPlugin', 'WaveformUMAPPluginComplete', 'TetrodeMetrics', 'MSCurationSave']
   ```

## Usage

### Converting Phy Clusters to MountainSort Format

To convert Phy clusters back to the MountainSort format, run:
```sh
python phy_to_mountainsort.py /path/to/phy/folder
```

### Converting MountainSort to Phy

To convert MountainSort data for use in Phy:
1. Ensure your MountainSort data is organized in the specified directory structure.
2. Run the conversion script:
   ```sh
   python mountainsort_to_phy.py
   ```

### Adding Behavioral Data to Phy

Use the provided MATLAB scripts to add behavioral data to Phy:
1. Update the configuration in `makeNPYfiles.m` and `atomicNPYfile.m` as needed.
2. Run the MATLAB scripts to generate the NPY files for behavioral data.

## Modules

### phy_to_mountainsort.py

Converts Phy clusters back to the MountainSort format. The script expects a folder containing Phy output and converts it to a format compatible with MountainSort.

### mountainsort_to_phy.py

Processes MountainSort output to prepare it for use with Phy. This includes extracting waveforms, spike sorting, and exporting to Phy format.

### Plugins

- **umap_plugin.py:** Adds a custom UMAP view for dimensionality reduction and visualization in Phy.
- **MSclusterPlugins.py:** Integrates MountainSort cluster metrics with Phy for enhanced curation capabilities.

### MATLAB Utilities

- **constructheader.m:** Constructs headers for NPY files.
- **write.m:** Writes MATLAB arrays to NPY files.
- **makeNPYfiles.m:** Generates NPY files for behavioral data to be used in Phy.
- **atomicNPYfile.m:** Helper function to write behavioral data to NPY files.

## Configuration

### Configuration Options in `mountainsort_to_phy.py`

- `filtered`: Use filtered MDA files instead of raw MDA files.
- `toleratemissing`: Skip folders with missing tetrodes.
- `skipproc`: Skip already processed folders.
- `parent_path`: Directory containing MountainSort data.

### Example Configuration

Update the configuration variables in `mountainsort_to_phy.py` as needed:
```python
config['filtered'] = True
config['toleratemissing'] = True
config['skipproc'] = True
config['parent_path'] = '/mnt/data/MountainSort'
```

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
