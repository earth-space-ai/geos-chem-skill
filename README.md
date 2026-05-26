# GEOS-Chem Skill

Progressive-disclosure skill for [GEOS-Chem](https://github.com/geoschem/GCClassic), the global 3D model of atmospheric chemistry and composition. Covers the **Classic** (single-node OpenMP) execution flavor via the `GCClassic` wrapper; for high-performance runs, GCHP is also covered.

> **Skill author:** Koutian Wu (ktwu01@gmail.com)
> **Skill version:** 0.1.0-scaffold

> ⚠️ **Disclaimer — please read before using this skill.**
> This skill is **not a gold-standard reference**. It is a helper that lowers
> the barrier for new users to **get their hands dirty** with the model. AI
> agents (and the humans drafting this material) make mistakes; commands, file
> paths, namelist options, and physics explanations here can be wrong,
> incomplete, or out of date. **Always cross-check with the official model
> documentation, the source code, and a human expert before trusting any
> output for research, publication, or operational use.**

## What This Is

A guide to building, running, configuring, and post-processing GEOS-Chem. Covers the GCClassic wrapper (with its `geos-chem` and `HEMCO` submodules), CMake build, run-directory generation, the multi-file configuration (`geoschem_config.yml`, `HEMCO_Config.rc`, `HISTORY.rc`), HEMCO emissions, and the `gcpy` Python toolkit.

## Status

Scaffold. Layout and submodule structure verified against the cloned `geoschem/GCClassic` tree. Priority skill for full deep-dive.

## License

MIT (skill content). GEOS-Chem itself is MIT-licensed.
