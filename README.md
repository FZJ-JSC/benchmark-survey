# HPC Benchmark Survey

**[https://fzj-jsc.github.io/benchmark-survey/](https://fzj-jsc.github.io/benchmark-survey/)**

A survey of existing HPC benchmarks and benchmark suites. See also [benchmark taxonomy](https://github.com/LLNL/benchmark-taxonomy).

The results have been gathered for the paper [_An HPC benchmark survey and taxonomy for characterization_](https://doi.org/10.1177/10943420251351424). See below for citing our work (repo, paper).

The list of benchmarks collected here in a machine-readable manner is transformed into tables, like a TeX table for a paper or an interactive table hosted within the repository. Access the website at [https://fzj-jsc.github.io/benchmark-survey/](https://fzj-jsc.github.io/benchmark-survey/).

## Benchmark YAML Scheme

Rules: 

1. Top-level keys can be either a name of a suite or `benchmarks`
2. A benchmark is identify with a unique key, and sibling keys `name`, `tags`, `license`, `url`, `ref`; with the according values
3. If the top-level key is a suite, the sibling keys are the same as _benchmark keys_ (`name`, `tags`, `license`, `url`, `ref`) plus a key `benchmark`, which contains keys for each benchmark like in 2.

Notes:

* Mandatory: `name` and (`url` or `ref `)
* `license`: use SPDX identifiers; be conscious of the distinction between a suite license and license for the individual benchmarks, they can be different
* `ref`: DOI


```yaml
rajaperf:
  name: RAJAPerf
  tags: [raja]
  license: BSD-3-Clause
  url: https://github.com/LLNL/RAJAPerf/
  # ref: none
  benchmarks:
    stream:
      name: STREAM
      tags: [benchmark-scale:single-node, memory-access-characteristics:regular-memory-access, programming-language:c]  # inline lists are a little more space-efficient
      license: free
      url: https://www.cs.virginia.edu/stream/
      ref: doi/1.2jladf
    polybench:
      name: PolyBench
      #...
benchmarks:
  hpl:
    name: HPL
```

The schema file `schema.json` can be used for validation of entries. Validate with

```bash
pajv validate -s schema.json -d benchmarks.yaml
```

A GitHub action is setup to for validation, triggered on pushed on `benchmarks.yaml`.

## Website

[The website](https://fzj-jsc.github.io/benchmark-survey/) is served through GitHub pages and utilizes open-source JavaScript libraries for dynamic view with filtering capabilities. Because of the interactivity, the website is the preferred way to view and use the benchmark table.

## PDF

The table can be converted into TeX syntax which we use in a paper. The script for conversionis available in `./tex-gen/`.

## Citing

The repository and the resulting website are outcome of the paper [_An HPC benchmark survey and taxonomy for characterization_](https://doi.org/10.1177/10943420251351424) ([arXiv](https://arxiv.org/abs/2509.08347)). Cite us the following:

```
Herten A, Pearce O, Guimarães FSM. An HPC benchmark survey and taxonomy for characterization. The International Journal of High Performance Computing Applications. 2026;40(1):42-51. doi:10.1177/10943420251351424
```
