# UnitMaster

A versatile and powerful unit conversion tool for Python.

## Features

- Convert between various units in multiple categories:
  - Length (mm, cm, m, km, in, ft, yd, mi)
  - Weight (mg, g, kg, ton, oz, lb)
  - Volume (ml, l, gal, qt, pt, fl_oz)
  - Temperature (Celsius, Fahrenheit, Kelvin)
  - Time (sec, min, hr, day, week, month, year)
  - Digital (B, KB, MB, GB, TB)
  - Area (mm², cm², m², km², in², ft², acre, ha)

- Simple and intuitive API
- Command-line interface for quick conversions
- Comprehensive unit alias system
- Detailed error handling

## Installation

```bash
pip install unitmaster
```

## Usage

### Command-line interface

```bash
# Basic conversion
unitmaster 100 m ft

# Specify a category (optional)
unitmaster 100 m ft -c length

# List available categories
unitmaster -l

# List units in a specific category
unitmaster -l -c length

# Customize decimal places
unitmaster 100 m ft --decimal-places 2
```

### Python API

```python
from unitmaster import convert, get_available_units, get_available_categories

# Simple conversion
result = convert(100, 'm', 'ft')
print(result)  # Output: 328.084

# Specify a category (optional)
result = convert(100, 'm', 'ft', category='length')

# Get available categories
categories = get_available_categories()
print(categories)  # ['length', 'weight', 'volume', ...]

# Get units in a specific category
length_units = get_available_units('length')
print(length_units)  # ['mm', 'cm', 'm', 'km', 'in', 'ft', 'yd', 'mi']

# Get all units grouped by category
all_units = get_available_units()
```

## Error Handling

```python
from unitmaster import convert
from unitmaster.exceptions import UnitMasterError, UnitNotFoundError, CategoryNotFoundError

try:
    result = convert(100, 'invalid_unit', 'ft')
except UnitNotFoundError as e:
    print(f"Error: {e}")

try:
    result = convert(100, 'm', 'ft', category='invalid_category')
except CategoryNotFoundError as e:
    print(f"Error: {e}")
```

## License

MIT License

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.