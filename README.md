# Snakemake-merqury
Workflow to run [`merqury`](https://github.com/marbl/merqury) for assembly validation.

## Getting started
```bash
git clone https://github.com/logsdon-lab/Snakemake-merqury.git
cd Snakemake-merqury
```

## Usage
```bash
snakemake -np --configfile config.yaml -c 1 --sdm conda
```

## Config
Specify global parameters for `meryl`.
```yaml
output_dir: "results"
log_dir: "logs"
benchmark_dir: "benchmarks"
threads: 12
mem: 20
```

## Data
Input data is split by samples. Requires an assembly and short reads.

### By directory and regular expression.
```yaml
samples:
  sample_name:
    asm_dir: "data/asm"
    asm_rgx: ".*\\.(fasta|fasta.gz)$"
    read_dir: "data/illumina"
    read_rgx: ".*\\.gz$"
```

### By fofn
```yaml
samples:
  sample_name:
    asm_fofn: "data/asm.fofn"
    read_fofn: "data/reads.fofn"
```

### By path
```yaml
samples:
  sample_name:
    asm: ["data/asm.fa"]
    reads: ["data/reads.fastq.gz"]
```

## Outputs
See `merqury` [documentation](https://github.com/marbl/merqury?tab=readme-ov-file#outputs-from-each-modules) for more information.
