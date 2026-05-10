---
name: geos-chem
description: >
  Progressive-disclosure skill for GEOS-Chem, the global 3D model of
  atmospheric chemistry and composition driven by assimilated meteorology
  (typically MERRA-2, GEOS-FP). Covers the GCClassic wrapper (this repo),
  the GCHP high-performance variant, the geos-chem science codebase
  (submodule), CMake build, run directories, configuration files, and
  the python tooling (gcpy). Used in chemistry-climate, air-quality,
  and methane/CO2 studies.
version: 0.1.0-scaffold
tags:
  - earth-science
  - atmospheric-chemistry
  - air-quality
  - chemistry-transport-model
  - geos-chem
  - merra2
  - geos-fp
  - hemco
  - fortran
---

# GEOS-Chem Guide

> **GEOS-Chem** = global 3D model of atmospheric chemistry driven by GEOS-DAS assimilated meteorology.
> Maintainer: GEOS-Chem Steering Committee, Harvard et al.
> This repo: https://github.com/geoschem/GCClassic (the "Classic" wrapper)
> Science submodule: https://github.com/geoschem/geos-chem
> High-performance variant: https://github.com/geoschem/GCHP
> Python toolkit: https://github.com/geoschem/gcpy
> Docs: https://geos-chem.readthedocs.io
> Skill author: Koutian Wu (ktwu01@gmail.com)
> Skill version: 0.1.0-scaffold

**What GEOS-Chem does:** Simulates atmospheric chemistry (gas-phase, aerosol, photolysis) and transport offline from a host meteorological dataset (MERRA-2 or GEOS-FP). Used for air-quality, climate-chemistry, and trace-gas (CH4, CO2, CO) studies. Two execution flavors:
- **Classic** (this repo, `GCClassic`), single-node OpenMP, simpler workflow
- **GCHP**, MPI parallel, ESMF-based, for high-resolution / many-CPU runs

**Architecture note:** `GCClassic` is a **wrapper "superproject"**. The science routines and run-directory generation scripts live in the [`geos-chem`](https://github.com/geoschem/geos-chem) submodule under `src/GEOS-Chem/`. Cloning the wrapper with `--recurse-submodules` is required.

**Who this skill is for:** Researchers running GEOS-Chem Classic for chemistry/composition studies, switching to GCHP for high resolution, or post-processing GEOS-Chem output.

---

## Quick Decision Tree

```
"What do I need?"
│
├─ 🆕 What is GEOS-Chem, Classic vs GCHP?
│  └─ Read: reference/overview.md
│
├─ 📥 Clone with submodules and prereqs (Spack-based env)
│  └─ Read: reference/getting-started.md
│
├─ 🛠️ Build with CMake
│  └─ Read: reference/build.md
│
├─ 📁 Generate a run directory and run a simulation
│  └─ Read: reference/run-directory.md
│
├─ 📝 Configuration files: geoschem_config.yml, HEMCO_Config.rc, HISTORY.rc, ...
│  └─ Read: reference/config-files.md
│
├─ 🌬️ HEMCO emissions and meteorology I/O
│  └─ Read: reference/hemco.md
│
├─ 🐍 Post-processing with gcpy
│  └─ Read: reference/gcpy.md
│
└─ 🐛 Common run failures
   └─ Read: reference/debugging.md
```

---

## Repo Layout (verified from clone)

```
GCClassic/
├── CMakeLists.txt        # Top-level CMake build
├── CMakeScripts/
├── docs/                 # Sphinx documentation source
├── run/                  # Run-directory generation helpers
├── spack/                # Spack environment files (recommended dependency setup)
├── src/                  # Submodules: GEOS-Chem, HEMCO, Cloud-J, ...
├── test/                 # Compile and integration tests
├── LICENSE.txt           # MIT
├── CHANGELOG.md
├── CONTRIBUTING.md
├── SUPPORT.md
└── AUTHORS.txt
```

After `git clone --recurse-submodules`, `src/GEOS-Chem` contains the science codebase, `src/HEMCO` contains the emissions module, `src/Cloud-J` contains the photolysis module.

---

## Critical Rules

1. **Always `--recurse-submodules` (or `git submodule update --init --recursive`) after clone.** GCClassic without submodules is non-functional.
2. **Run directories are external to the source tree.** Use `run/createRunDir.sh` (or follow ReadTheDocs) to generate a run directory; the executable is run there, not inside the repo.
3. **Configuration is multi-file:**
   - `geoschem_config.yml`, main run control (simulation type, dates, transport)
   - `HEMCO_Config.rc`, emissions inventories and overrides
   - `HISTORY.rc`, diagnostic output (collections, variables, frequencies)
   - `species_database.yml`, species metadata
4. **Spack-based environment is recommended.** Manually managing NetCDF/MPI/HDF5 versions is a common source of build failures; use the provided spack env.
5. **For high-resolution (≤ 0.5°) runs, use GCHP**, not Classic. Classic is OpenMP single-node.
6. **`gcpy` is the official Python toolkit.** Use it for plotting and benchmarking; ad-hoc xarray scripts work but lose convenience.

---

## Reference Index

| File | Topic |
|---|---|
| reference/overview.md | Classic vs GCHP, science scope |
| reference/getting-started.md | Clone with submodules, prereqs |
| reference/build.md | CMake build |
| reference/run-directory.md | createRunDir.sh, run-dir structure |
| reference/config-files.md | geoschem_config.yml, HEMCO, HISTORY |
| reference/hemco.md | HEMCO emissions framework |
| reference/gcpy.md | Python post-processing |
| reference/debugging.md | Common errors |

## Status

Scaffold (v0.1.0-scaffold). Layout, submodule structure, and configuration-file convention verified against the cloned tree. This is a priority skill for full deep-dive after scaffold pass.
