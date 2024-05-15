# Performance Measurement

## Overview

Two command has been provided to perform the measurements:
- `python-performance`: For measuring the performance of the Python implementation.
- `r-performance`: For measuring the performance of the R implementation.

## Installation

### Clone the repository and go to the project root dir

Before installing and running the CLI tool, you have to clone the repo and navigate
to the project's root directory.

```bash
git clone git@github.com:bionetslab/grn-benchmark.git && cd grn-benchmark/src/codc-cli-tool
```

### Using Docker

Build the Docker container from the Dockerfile at the root of the project if not done already. This will set up the necessary environment for both Python and R scripts.

```bash
docker build -t codc-tool .
```

### Using Locally

#### Python Dependencies
```bash
pdm install
```

#### R Dependencies
Ensure R is installed and run:
```R
Rscript dependencies.R
```

## Usage

### Python Performance Measurement

#### Using Docker

```bash
docker run --rm -v /tests/data:/data codc-tool python-performance --input_file_1 /data/BRCA_normal.tsv --input_file_2 /data/BRCA_tumor.tsv --iterations 10 --output_path /data/
```

#### Using Locally

```bash
pdm run cli python-performance --input_file_1 /tests/data/BRCA_normal.tsv --input_file_2 /tests/data/BRCA_tumor.tsv --iterations 10 --output_path .
```

### R Performance Measurement

#### Using Docker

```bash
docker run --rm -v /tests/data:/data codc-tool r-performance --input_file_1 /data/BRCA_normal.tsv --input_file_2 /data/BRCA_tumor.tsv --iterations 10 --output_path /data/
```

#### Using Locally

```bash
pdm run cli r-performance --input_file_1 /tests/data/BRCA_normal.tsv --input_file_2 /tests/data/BRCA_tumor.tsv --iterations 10 --output_path .
```

## Output

Both scripts generate CSV files detailing the execution times for each iteration, helping to analyze and compare the performance of Python and R implementations.