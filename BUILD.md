# Build Information

This repository contains a [Nextstrain](https://nextstrain.org) community build for Chikungunya virus (CHIKV). This document provides information about the build process and how to reproduce or extend the analysis.

## Overview

This Nextstrain build analyzes publicly available CHIKV genomes from NCBI GenBank to provide insights into the molecular epidemiology and phylogenetic relationships of Chikungunya virus strains.

## Build System

The analysis uses the **Nextstrain** platform, which consists of:

- **Augur**: Bioinformatics toolkit for phylogenetic analysis
- **Auspice**: Web-based visualization tool

## Data Sources

- **Sequence data**: CHIKV genomes from [NCBI GenBank](https://www.ncbi.nlm.nih.gov/genbank/)
- **Metadata**: Curated lineage annotations (see `autolin/labels.tsv`)

## Build Workflow

A typical Nextstrain build follows these steps:

1. **Data Download**: Fetch sequences from GenBank
2. **Filtering**: Quality control and sequence selection
3. **Alignment**: Multiple sequence alignment
4. **Tree Building**: Phylogenetic tree construction
5. **Temporal Analysis**: Time-calibrated phylogeny
6. **Trait Reconstruction**: Ancestral state reconstruction
7. **Export**: Generate JSON files for visualization

## Dependencies

To run a Nextstrain build, you need:

- [Augur](https://docs.nextstrain.org/projects/augur/en/stable/) - phylogenetic analysis toolkit
- [Auspice](https://docs.nextstrain.org/projects/auspice/en/stable/) - visualization framework

### Installation

The easiest way to get started is using conda:

```bash
conda create -n nextstrain augur auspice
conda activate nextstrain
```

Alternatively, use the [Nextstrain CLI](https://docs.nextstrain.org/en/latest/install.html):

```bash
curl http://nextstrain.org/cli/installer/linux > nextstrain
chmod +x nextstrain
./nextstrain setup --set-default docker
```

## Reproducing the Analysis

While this repository contains the output files (in the `auspice/` directory), the build scripts are not included. To create a similar build:

1. **Set up Nextstrain environment** (see Dependencies above)

2. **Download CHIKV sequences** from GenBank:
   ```bash
   # Using NCBI Datasets CLI or Augur's download functionality
   augur download --database genbank --organism "Chikungunya virus"
   ```

3. **Create a build configuration**:
   - Define filtering criteria (e.g., date range, completeness)
   - Specify alignment parameters
   - Configure tree-building options
   - Set up trait annotations (lineage, geography, etc.)

4. **Run the workflow**:
   ```bash
   snakemake --cores 4
   ```

5. **Visualize results**:
   ```bash
   auspice view --datasetDir auspice/
   ```

## Standard Nextstrain Workflow Files

A typical Nextstrain build includes:

- `Snakefile` - Workflow definition
- `config/` - Configuration files
  - `config.yaml` - Build parameters
  - `reference.fasta` - Reference genome
  - `colors.tsv` - Color schemes
  - `lat_longs.tsv` - Geographic coordinates
- `scripts/` - Custom analysis scripts
- `data/` - Input sequences and metadata

## Custom Annotations

This build includes custom lineage annotations in `autolin/labels.tsv`, which maps sequence accessions to CHIKV lineages:

- **A** - African/Asian Lineages
- **ECSA** - East/Central/South African lineage
- **AUL** - Asian Urban Lineage
- **AUL-Am** - Asian Urban + American Lineage
- **EAL** - Eastern African Lineage
- **IOL** - Indian Ocean Lineage
- **MAL** - Middle African Lineage
- **SAL** - South American Lineage
- **WA** - Western African Lineage

## Example Build Template

For a basic CHIKV Nextstrain build, you would create a `Snakefile` like this:

```python
rule all:
    input:
        auspice_json = "auspice/CHIKV.json"

rule download:
    # Download sequences from GenBank

rule filter:
    # Filter sequences for quality and completeness

rule align:
    # Multiple sequence alignment

rule tree:
    # Build phylogenetic tree

rule refine:
    # Time-calibrated tree

rule ancestral:
    # Ancestral sequence reconstruction

rule translate:
    # Translate to proteins

rule traits:
    # Reconstruct geographic spread

rule export:
    # Create Auspice JSON
```

## Viewing the Build

The pre-built visualization is available at:
- Online: https://nextstrain.org/community/ViennaRNA/CHIKV
- Local: Drag and drop `auspice/CHIKV.json` to https://auspice.us

## Resources

### Documentation
- [Nextstrain documentation](https://docs.nextstrain.org/)
- [Augur documentation](https://docs.nextstrain.org/projects/augur/en/stable/)
- [Building your own Nextstrain analysis](https://docs.nextstrain.org/en/latest/tutorials/creating-a-workflow.html)

### Example Builds
- [Nextstrain example workflows](https://github.com/nextstrain/workflows)
- [Zika virus build](https://github.com/nextstrain/zika)
- [Seasonal influenza build](https://github.com/nextstrain/seasonal-flu)

### Publications
This build is based on the methodology described in:

- **Dynamic Molecular Epidemiology Reveals Lineage-Associated Single-Nucleotide Variants That Alter RNA Structure in Chikungunya Virus**
  _Thomas Spicher, Markus Delitz, Adriano de Bernardi Schneider, and Michael T. Wolfinger_
  Genes, 12(2):239, Feb 2021. DOI:[10.3390/genes12020239](https://dx.doi.org/10.3390%2Fgenes12020239) PMCID:[PMC7914560](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7914560/)

- **Updated Phylogeny of Chikungunya Virus Suggests Lineage-Specific RNA Architecture**
  _Adriano de Bernardi Schneider, Roman Ochsenreiter, Reilly Hostager, Ivo L. Hofacker, Daniel Janies, and Michael T. Wolfinger_
  Viruses, 11:798, Aug 2019. DOI:[10.3390/v11090798](https://dx.doi.org/10.3390%2Fv11090798) PMCID:[PMC6784101](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6784101/)

## Support

For questions about:
- **This specific build**: Open an issue in this repository
- **Nextstrain in general**: Visit the [Nextstrain discussion forum](https://discussion.nextstrain.org/)
- **CHIKV research**: See the publications above or contact the authors

## Contributing

Contributions are welcome! If you have suggestions for improving the build or find issues with the data, please open an issue or pull request.
