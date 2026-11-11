# Full Fluent files

The lightweight repository contains geometry, settings, numerical records, monitor histories and figures. Full restart and mesh files are packaged separately as `KIG2014_CFD_Fluent_Files.zip` for a GitHub Release.

**Published:** [v1.0.0](https://github.com/Tonylo-lab/KIG2014-Fluid-Mechanics-II-CFD-Assignment/releases/tag/v1.0.0).

[Download KIG2014_CFD_Fluent_Files.zip](https://github.com/Tonylo-lab/KIG2014-Fluid-Mechanics-II-CFD-Assignment/releases/download/v1.0.0/KIG2014_CFD_Fluent_Files.zip) — 356,982,584 bytes (340.45 MiB), containing 27 files across nine runs.

SHA-256:

```text
3ea61e377872d4089a75e9687cc44fec0862db0675369fef3df261aa71d077f6
```

The archive contains the nine corresponding `.cas.h5`, `.dat.h5` and `.msh` sets. Extract it alongside the repository so its files merge into `results/laminar/M1` through `M4` and `results/turbulent/M1` through `M5`. Read the case and matching data file for the mesh you want to inspect.

Each file uses a descriptive prefix such as `laminar_M3` or `turbulent_M5`. These are Fluent restart/mesh files; an original Workbench project is not included in the release archive. The Parasolid geometry and reproduction guide allow a fresh Workbench project to be created.

GitHub blocks ordinary Git files larger than 100 MiB; the M5 `.msh` exceeds that limit. See [GitHub's large-file documentation](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github). A Release asset keeps these large binaries out of Git history.
