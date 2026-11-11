# Full Fluent files

The lightweight repository contains geometry, settings, numerical records, monitor histories and figures. Full restart and mesh files are packaged separately as `KIG2014_CFD_Fluent_Files.zip` for a GitHub Release.

**Publication status:** the archive is prepared locally; no online download URL has been assigned yet. Once it has been uploaded, use the repository's Releases page to obtain it.

The archive contains the nine corresponding `.cas.h5`, `.dat.h5` and `.msh` sets. Extract it alongside the repository so its files merge into `results/laminar/M1` through `M4` and `results/turbulent/M1` through `M5`. Read the case and matching data file for the mesh you want to inspect.

Each file uses a descriptive prefix such as `laminar_M3` or `turbulent_M5`. These are Fluent restart/mesh files; an original Workbench project is not included in the release archive. The Parasolid geometry and reproduction guide allow a fresh Workbench project to be created.

GitHub blocks ordinary Git files larger than 100 MiB; the M5 `.msh` exceeds that limit. See [GitHub's large-file documentation](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github). A Release asset keeps these large binaries out of Git history.
