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

## Acknowledgments

**Gold-standard references for GEOS-Chem** (use these to cross-check anything in this skill):
- GEOS-Chem documentation portal: https://geos-chem.readthedocs.io/
- geoschem/GCClassic wrapper repository: https://github.com/geoschem/GCClassic
- geoschem/geos-chem source repository: https://github.com/geoschem/geos-chem
- geoschem/HEMCO emissions module: https://github.com/geoschem/HEMCO
- gcpy Python toolkit: https://github.com/geoschem/gcpy

This scaffold exists only because of the work of other people, and any value
it has is borrowed from theirs.

- The **Harvard Atmospheric Chemistry Modeling Group** and the broader
  **GEOS-Chem Steering Committee + International GEOS-Chem User Community**
  for building and maintaining
  [geoschem/GCClassic](https://github.com/geoschem/GCClassic), the
  `geos-chem` and `HEMCO` submodules, the `gcpy` Python toolkit, and the
  wiki / Confluence documentation this skill leans on.
- The maintainers of **GCHP** (high-performance variant) for the alternative
  execution path that this skill routes to when users need MPI scaling.
- **Zesen Huang** for [laps-skill](https://github.com/huangzesen/laps-skill),
  the progressive-disclosure layout this repo borrows.

Any errors, oversimplifications, or out-of-date claims in this skill are the
skill author's responsibility, not the upstream community's. This is a
scaffold; operational depth is being filled in iteratively.

## License

MIT (skill content). GEOS-Chem itself is MIT-licensed.
