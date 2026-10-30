<!-- SPDX-FileCopyrightText: 2026 Oliver Niggemann -->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 -->

# ReDiVO: Code and Artificial Data Generation

## Paper

**Reconstruction-Based Diagnosis through Gödel-Regularized Virtual Observability**

Oliver Niggemann, Jonas Ehrhardt, and Alexander Diedrich  
Chair of Computer Science in Mechanical Engineering  
Helmut Schmidt University / University of the Federal Armed Forces Hamburg, Germany

Contact: [oliver.niggemann@hsu.hamburg](mailto:oliver.niggemann@hsu.hamburg)

## Method

ReDiVO uses virtual sensors to reconstruct unmeasured process variables. It compares the current system trajectory with a learned nominal trajectory. Persistent deviations provide local fault symptoms. Their onset times are used to identify possible root causes.

Physical and system knowledge is expressed through Gödel logic to guide training. These rules regularize the neural observer. They are not used as an additional online diagnosis mechanism.

## Downloads

The following packages provide the algorithm code and generators associated with the two artificial studies in Section 4.1. They do not contain large raw datasets or trained models.

| Package | Contents | Size |
|---|---|---:|
| [Algorithm code](ReDiVO_Code_Minimal_20261030.zip) | Model, training, reconstruction, Gödel regularization, diagnosis, and required support modules | 338 KB |
| [Data generation](ReDiVO_Data_Generation_20261030.zip) | Generators, original configurations, seeds, and instructions for the linear networks and hybrid automata | 61 KB |

Sizes are rounded decimal kilobytes. Both packages include a README, provenance information, file checksums, license texts, and a verification script. No HPC, Slurm, monitoring, or campaign-submission scripts are included.

## Getting Started

1. Download and extract the package you need.
2. Read its `README.md` and install the listed dependencies in an isolated Python environment.
3. Run `python verify_package.py` inside the extracted package to check its files. This does not run simulations or training.
4. Follow the package instructions to use the algorithm or explicitly generate a selected dataset.

The algorithm package provides Python interfaces rather than a complete experiment command-line application. Callers supply prepared data, system knowledge, and the training and diagnosis configuration. The data-generation package provides a separate command-line interface. Generating data requires an explicit `--execute` flag. Depending on the selected system, generation and subsequent training can require substantial computation.

## Artificial Studies

**Linear component networks.** Each component has two hidden states, six redundant measurements, linear discrete-time dynamics, and delayed connections. The package contains the original graph-condition configurations and seeds for the study identified as EXP-C046, algorithm version ALG-V18.2.

**Random hybrid automata.** Components switch between three operating modes with affine or nonlinear ordinary differential equations. The generator includes actuator-effectiveness loss and additional outflow faults. The package corresponds to EXP-C067-HA-CPU-R4, algorithm version ALG-V18.3-RECURSIVE-R2 with its hybrid adapter. Its eight primary system seeds are 27101 to 27108. Development and larger exploratory systems are identified separately.

The two studies retain their original code versions. They must not be interpreted as runs of a later algorithm. Their parameters, masks, data roles, seeds, and numerical settings are documented in the archives. Offline state references, fault labels, and matched fault-free trajectories are not online diagnosis inputs.

The standalone linear generator removes ML-specific imports and preparation of neural-network windows. Its retained numerical definitions were checked against the original source. The hybrid generator and its numerical protocol remain byte-identical to the frozen files. The archives distinguish original source checksums from checksums of the reduced release packages.

## Verification and Reproduction

[SHA256SUMS.txt](SHA256SUMS.txt) contains the checksums of both ZIP files. Each extracted archive also contains `MANIFEST.json` and `verify_package.py` for checking individual files.

The export was checked for syntax, required local-module dependencies, numerical definitions retained in the linear generator, checksums, and archive integrity. No new simulation, training run, or ML runtime test was performed during packaging. The recorded numerical environment is documented where available. Regeneration across different library versions has not been established as bitwise identical.

## Copyright and Licenses

Copyright (c) 2026 Oliver Niggemann.  
Affiliation: Helmut Schmidt University / University of the Federal Armed Forces Hamburg, Germany.

- **Software, including both generators:** [GNU Affero General Public License, version 3 or later (AGPL-3.0-or-later)](https://spdx.org/licenses/AGPL-3.0-or-later.html).
- **Original data, data documentation, and this page:** [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/legalcode.en), to the extent the relevant rights exist and can be licensed.

The full license texts are included in each archive. File-level notices identify the applicable license. Existing rights and notices of other contributors remain unaffected. Institutional affiliation does not by itself imply institutional endorsement or joint copyright ownership.

Redistribution and covered adaptations must follow the applicable copyleft terms. The AGPL also requires a source offer for modified network-interactive versions when its conditions apply. These licenses do not require publication of every purely private modification.

## Warranty and Liability

**The software and data come without warranties or guarantees. Use is at your own risk.**

As far as applicable law allows, Oliver Niggemann, the identified rightsholders, contributors, and institution exclude liability for loss or damage connected with these materials. Legally mandatory liabilities remain unaffected. The applicable license contains the governing warranty and liability provisions.
