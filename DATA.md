# Data Documentation

This document describes the data files included in this repository and their formats.

## Directory Structure

```
CHIKV/
├── README.md           # Main repository documentation
├── BUILD.md            # Build process documentation
├── CONTRIBUTING.md     # Contribution guidelines
├── DATA.md             # This file
├── auspice/            # Nextstrain visualization files
│   ├── CHIKV.json                  # Main visualization data
│   ├── CHIKV_root-sequence.json    # Root sequence for tree
│   └── CHIKV_tip-frequencies.json  # Tip frequency data
└── autolin/            # Lineage annotation data
    └── labels.tsv      # Sequence-to-lineage mappings
```

## Data Files

### Auspice Directory

The `auspice/` directory contains JSON files that are used by Auspice for visualization:

#### CHIKV.json

The main visualization file containing:
- Phylogenetic tree structure
- Temporal data (collection dates)
- Geographic locations
- Lineage assignments
- Metadata for each sequence
- Color schemes and display settings

**Usage:**
- View online at: https://nextstrain.org/community/ViennaRNA/CHIKV
- View locally by dragging to: https://auspice.us
- View with local Auspice: `auspice view --datasetDir auspice/`

**Format:** Nextstrain JSON v2 format (see [Auspice JSON schema](https://nextstrain.org/docs/bioinformatics/data-formats))

#### CHIKV_root-sequence.json

Contains the inferred ancestral sequence at the root of the phylogenetic tree. This is used by Auspice to display mutations along branches.

#### CHIKV_tip-frequencies.json

Contains time-series data showing the frequency of different clades over time. This enables the frequency plot visualization in Auspice.

### Autolin Directory

The `autolin/` directory contains lineage annotation data.

#### labels.tsv

A tab-separated file mapping GenBank accession numbers to CHIKV lineages.

**Format:**
```
sample          lineage
OL343614.1      A
KR559492.1      A
MT150096.1      A.2.1
...
```

**Columns:**
- `sample`: GenBank accession number
- `lineage`: CHIKV lineage designation

**Lineage Nomenclature:**

Major lineages:
- **A** - African/Asian Lineages (ancestral)
- **ECSA** - East/Central/South African lineage
- **IOL** - Indian Ocean Lineage
- **WA** - Western African Lineage

Sub-lineages include:
- **A.1**, **A.2**, etc. - Sub-lineages of the A lineage
- **A.2.1**, **A.2.2**, etc. - Further subdivisions
- **AUL** - Asian Urban Lineage
- **AUL-Am** - Asian Urban + American Lineage
- **EAL** - Eastern African Lineage
- **MAL** - Middle African Lineage
- **SAL** - South American Lineage

For detailed information on CHIKV lineages, see:
- [Updated Phylogeny of Chikungunya Virus](https://dx.doi.org/10.3390%2Fv11090798)
- [Dynamic Molecular Epidemiology](https://dx.doi.org/10.3390%2Fgenes12020239)

## Data Sources

All sequence data originates from [NCBI GenBank](https://www.ncbi.nlm.nih.gov/genbank/):
- Publicly available CHIKV genome sequences
- Associated metadata (collection date, location, etc.)

## Data Updates

This build is updated irregularly when sufficient new sequences are available in GenBank. Check the commit history for the date of the latest update.

## Using the Data

### Accessing Sequence Data

The original sequence data is not stored in this repository. To obtain the sequences:

1. Use the accession numbers from `autolin/labels.tsv`
2. Download from GenBank using:
   - [NCBI Datasets](https://www.ncbi.nlm.nih.gov/datasets/)
   - NCBI E-utilities API
   - Augur's download functionality

Example using NCBI E-utilities:
```bash
# Download a single sequence
efetch -db nuccore -id OL343614.1 -format fasta > OL343614.fasta
```

### Programmatic Access

The JSON files can be parsed programmatically:

**Python example:**
```python
import json

# Load the main visualization data
with open('auspice/CHIKV.json', 'r') as f:
    data = json.load(f)

# Access tree structure
tree = data['tree']

# Access metadata
meta = data['meta']
```

**R example:**
```R
library(jsonlite)

# Load the data
data <- fromJSON('auspice/CHIKV.json')

# Access tree nodes
nodes <- data$tree
```

## Data Quality

All sequences included in this build have been filtered for:
- Completeness (sufficient genome coverage)
- Quality (no excessive ambiguous bases)
- Metadata availability (collection date, location)

Specific filtering criteria are defined in the build workflow (see [BUILD.md](BUILD.md)).

## Citations

If you use this data in your research, please:

1. Link back to this repository: https://github.com/ViennaRNA/CHIKV
2. Cite the associated publications (see [README.md](README.md#citation))
3. Acknowledge the original data submitters (sequences from GenBank)

## Questions or Issues

If you have questions about the data or notice any issues:
- Review this documentation
- Check [BUILD.md](BUILD.md) for build process details
- Open an issue on GitHub
- See [CONTRIBUTING.md](CONTRIBUTING.md) for more ways to get help

## Additional Resources

- [Nextstrain documentation](https://docs.nextstrain.org/)
- [Auspice JSON schema](https://nextstrain.org/docs/bioinformatics/data-formats)
- [NCBI GenBank](https://www.ncbi.nlm.nih.gov/genbank/)
