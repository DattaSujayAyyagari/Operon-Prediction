# Operon Prediction from PTT and GFF Files

[![Python](https://img.shields.io/badge/Python-3.8%2B-brightgreen)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-1.x-blue)](https://pandas.pydata.org/)
[![CSV](https://img.shields.io/badge/CSV-Format-yellow)](https://en.wikipedia.org/wiki/Comma-separated_values)

This project demonstrates the use of Python to predict operons in bacterial genomes using data from PTT and GFF files. It includes data extraction, operon prediction logic, and output formatting for analysis.

## Overview

The goal of this project is to identify operons, which are clusters of genes transcribed together, based on their genomic proximity and strand orientation. Operons play a crucial role in gene regulation and understanding them helps in annotating genomes and studying gene functions.

## Dataset

### PTT Files

PTT (Protein Table) files contain:
- **Location**: Start and stop positions of genes.
- **Strand**: The DNA strand (`+` or `-`) the gene is on.
- **Length**: Length of the gene.
- **PID**: Protein ID.
- **Gene**: Gene name.
- **Synonym**: Alternative gene name.
- **Code**: Gene code.
- **COG**: Cluster of Orthologous Groups classification.
- **Product**: Description of the gene product.

### GFF Files

GFF (General Feature Format) files contain:
- **contig**: Contig or chromosome name.
- **start**: Start position of the gene or feature.
- **stop**: Stop position of the gene or feature.
- **strand**: Strand direction (`+` or `-`).

## Code Description

### PTT File Operon Prediction

**Function**: `predict_operons(filepath, threshold=50)`

**Objective**: Predicts operons from a PTT file by identifying clusters of genes that are close together and on the same DNA strand.

**Inputs**:
- `filepath`: Path to the PTT file.
- `threshold`: Maximum distance (in base pairs) between consecutive genes in the same operon (default: 50).

**Outputs**:
- Number of predicted operons.
- List of operons, each containing a set of genes.

**Method**:
- Reads and parses the PTT file.
- Extracts start and stop positions from the `Location` field.
- Sorts genes by their start position.
- Groups genes into operons based on strand and proximity.

### GFF File Operon Prediction

**Function**: `predict_operons_gff(filepath, threshold=50)`

**Objective**: Predicts operons from a GFF file using a similar logic to PTT file prediction.

**Inputs**:
- `filepath`: Path to the GFF file.
- `threshold`: Maximum distance (in base pairs) between consecutive genes in the same operon (default: 50).

**Outputs**:
- Number of predicted operons.
- List of operons, each containing a set of genes.

**Method**:
- Reads and parses the GFF file.
- Extracts relevant columns (`contig`, `start`, `stop`, and `strand`).
- Sorts genes by contig and start positions.
- Groups genes into operons based on strand and proximity.

## Example Use Cases

- **Genome Annotation**: Provides insights into gene clusters and regulatory regions by identifying operons.
- **Comparative Genomics**: Useful in analyzing operon structures across different bacterial genomes for evolutionary studies.
- **Gene Regulation Studies**: Helps in understanding the regulatory mechanisms by identifying co-transcribed gene clusters.

## Contributing

Contributions to this project are welcome! If you have suggestions or improvements, please fork the repository and submit a pull request.
