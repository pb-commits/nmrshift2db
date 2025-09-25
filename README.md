# NMR Chemical Shift Database (JSON Format)

This repository contains **57,055 individual JSON files** with NMR (Nuclear Magnetic Resonance) spectroscopic data for chemical compounds, extracted from the NMRShiftDB database.

## 📊 Dataset Overview

- **Total Compounds**: 57,055
- **File Format**: Individual JSON files (one per compound)
- **File Naming**: Based on InChI keys (International Chemical Identifier)
- **Source**: NMRShiftDB2 with signals (`nmrshiftdb2withsignals.sd`)
- **Data Size**: ~222 MB total

## 🧪 Data Structure

Each JSON file contains chemical and spectroscopic information for a single compound:

```json
{
  "INChI key": "AAAISYODTULZTR-DARAHFNDSA-N",
  "INChI": "InChI=1S/C19H23N3O4/c1-5-25-17(23)14-12-13...",
  "Temperature [K]": "0:Unreported ",
  "nmrshiftdb2 ID": 20172509,
  "Field Strength [MHz]": "0:Unreported ",
  "Solvent": "0:Unreported ",
  "Spectrum 1H 0": "1.41;0.0;24|3.6;0.0;26|4.27;0.0;27...",
  "Spectrum 13C 0": "chemical_shift_data...",
  "SMILES": "CCOC(=O)C1=NN[C@H]2[C@@H]1[C@@H]1c3ccccc3...",
  "_molecule_index": 25293
}
```

## 📋 Common Data Fields

### Essential Identifiers
- `INChI key`: Unique chemical identifier
- `INChI`: International Chemical Identifier string  
- `nmrshiftdb2 ID`: Database ID number
- `SMILES`: Simplified molecular input line entry system
- `_molecule_index`: Original position in source file

### Experimental Conditions
- `Temperature [K]`: Measurement temperature
- `Field Strength [MHz]`: NMR spectrometer frequency
- `Solvent`: Solvent used for measurement
- `Assignment Method`: Method used for peak assignment

### NMR Spectral Data
- `Spectrum 1H X`: Proton NMR data (various experiments)
- `Spectrum 13C X`: Carbon-13 NMR data
- `Spectrum 31P X`: Phosphorus-31 NMR data
- `Spectrum 19F X`: Fluorine-19 NMR data
- `Spectrum 15N X`: Nitrogen-15 NMR data
- And many other nuclei and 2D NMR experiments

## 🔍 Usage Examples

### Find a specific compound:
```bash
# By InChI key
cat AAAISYODTULZTR-DARAHFNDSA-N.json

# Search for compounds with specific solvent
grep -l "Chloroform" *.json

# Find compounds with 1H NMR data
grep -l "Spectrum 1H" *.json
```

### Python usage:
```python
import json
import glob

# Load a specific compound
with open('AAAISYODTULZTR-DARAHFNDSA-N.json', 'r') as f:
    compound = json.load(f)

# Load all compounds with 13C NMR data
compounds_with_13c = []
for filename in glob.glob('*.json'):
    with open(filename, 'r') as f:
        data = json.load(f)
        if 'Spectrum 13C 0' in data:
            compounds_with_13c.append(data)
```

## 📈 Data Statistics

- **Most Complete Fields**:
  - INChI key: ~100% of compounds
  - INChI: ~100% of compounds  
  - nmrshiftdb2 ID: ~100% of compounds
  - Temperature/Field Strength/Solvent: ~100% of compounds

- **Common Spectral Data**:
  - 13C NMR: ~58% of compounds (33,066 entries)
  - 31P NMR: ~22% of compounds (12,769 entries)
  - 1H NMR: ~18% of compounds (10,101 entries)

## 🛠️ Data Processing

This dataset was converted from the original SDF (Structure Data File) format using RDKit:

1. **Source**: `nmrshiftdb2withsignals.sd`
2. **Processing**: RDKit molecular property extraction
3. **Format**: Individual JSON files for efficient access
4. **Validation**: Automatic SMILES generation and error handling

## 📚 Applications

This dataset is useful for:
- **Cheminformatics research**
- **NMR prediction model training**
- **Chemical database queries**
- **Spectral analysis studies**
- **Machine learning on molecular properties**

## ⚠️ Data Quality Notes

- Some compounds may have missing spectral data (sparse dataset)
- Experimental conditions may be "Unreported" for some entries
- Complex molecular structures may have processing limitations
- Original source data quality varies

## 📄 License & Attribution

- **Source**: NMRShiftDB2 database
- **Processing**: Converted using RDKit and custom Python scripts
- **Format**: Individual JSON files for accessibility

Please cite the original NMRShiftDB database if using this data in research.

## 🔗 Related Files

- Original SDF file: `nmrshiftdb2withsignals.sd`
- Conversion scripts: Available in parent directory
- Alternative formats: CSV and consolidated JSON versions available

---

*Generated from NMRShiftDB2 database • Individual JSON format for efficient compound-specific access*
