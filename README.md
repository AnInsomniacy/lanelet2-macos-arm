# Lanelet2-macOS-ARM

A fork of [lanelet2x](https://github.com/wu-vincent/lanelet2x) with native **Apple Silicon (ARM64) macOS** support.

Lanelet2 is your favorite map handling framework for automated driving, now standalone with optimized builds for ARM-based Macs (M1/M2/M3/M4).

![](lanelet2_core/doc/images/lanelet2_example_image.png)

## Features

- **2D and 3D** support
- **Consistent modification**: if one point is modified, all owning objects see the change
- Supports **lane changes**, routing through areas, etc.
- **Separated routing** for pedestrians, vehicles, bikes, etc.
- **Python** bindings for the whole C++ interface
- **Boost Geometry** support for geometry calculations on map primitives
- Native **Apple Silicon (ARM64)** support
- Released under the [**BSD 3-Cldause license**](LICENSE)

## Installation (macOS ARM64)

### Prerequisites

- macOS with Apple Silicon (M1/M2/M3/M4)
- Python 3.9+
- CMake 3.26+
- Ninja

### Build from Source

```bash
# Clone the project
git clone git@github.com:AnInsomniacy/lanelet2-macos-arm.git
cd lanelet2-macos-arm

# Install build dependencies (numpy<2.0 is required for Boost compatibility)
pip install -r requirements.txt

# Setup Conan profile
conan profile detect

# Install C++ dependencies with Conan
conan install . --build=missing -o shared=True -c tools.cmake.cmaketoolchain:generator=Ninja

# Create symlink for CMake toolchain
ln -sf build/Release/generators generators

# Install Python package
pip install .
```

### Verify Installation

```bash
python -c "import lanelet2; print('lanelet2 installed successfully!')"
```

## Documentation

- [Lanelet Primitives](lanelet2_core/doc/LaneletPrimitives.md)
- [Software Architecture](lanelet2_core/doc/Architecture.md)
- [Geometry Calculations](lanelet2_core/doc/GeometryPrimer.md)
- [Map Projections](lanelet2_projection/doc/Map_Projections_Coordinate_Systems.md)
- [Creating Valid Maps](lanelet2_maps/README.md)

## Examples

Examples and common use cases in both C++ and Python can be found [here](lanelet2_examples/README.md).

## Citation

If you are using Lanelet2 for scientific research, please cite:

```latex
@inproceedings{poggenhans2018lanelet2,
  title     = {Lanelet2: A High-Definition Map Framework for the Future of Automated Driving},
  author    = {Poggenhans, Fabian and Pauls, Jan-Hendrik and Janosovits, Johannes and Orf, Stefan and Naumann, Maximilian and Kuhnt, Florian and Mayr, Matthias},
  booktitle = {Proc.\ IEEE Intell.\ Trans.\ Syst.\ Conf.},
  year      = {2018},
  address   = {Hawaii, USA},
  Url={http://www.mrt.kit.edu/z/publ/download/2018/Poggenhans2018Lanelet2.pdf}
}
```

## License

BSD 3-Clause License
