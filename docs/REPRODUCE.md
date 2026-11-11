# Reproducing the workflow

## 1. Geometry and named boundaries

Import the Parasolid file in `geometry/`, or create a cylinder representing the fluid volume: diameter 10 mm, length 1000 mm, axis Z. Use the inlet at Z = 1 m, outlet at Z = 0 m and cylindrical wall. The saved names are `inlert`, `outlert` and `wall`.

## 2. Swept mesh sequence

| Mesh | Cross-section element size | Axial divisions | Use |
|---|---|---:|---|
| M1 | 1.00 mm | 200 | Laminar and turbulent |
| M2 | 0.70 mm | 300 | Laminar and turbulent |
| M3 | 0.50 mm | 400 | Laminar and turbulent |
| M4 | 0.35 mm | 600 | Laminar and turbulent |
| M5 | 0.35 mm plus inflation | 400 | Turbulent only |

For M1–M4 use a Sweep method. The per-run parameter files contain the actual resulting cell/node counts and reported quality values. Counts may differ if your geometry topology or meshing defaults differ.

For M5, set Sweep source selection to Manual Source, select the inlet circular end face, then add inflation to that method. Scope the inflation geometry to the source face and the boundary to its outer circular edges. Use First Layer Thickness, first-layer height 0.01 mm, requested maximum 20 layers and growth rate 1.2. The requested maximum is a control, not a statement that every boundary location has exactly that many undistorted layers. Inspect the resulting mesh before solving.

The final M5 contains 984,800 cells. An earlier 600-division attempt exceeded the active 1,048,576-cell limit, which is why the final M5 uses 400 axial divisions. Check your own licence limit before a large run.

## 3. Fluent physics

Use 3D double precision, a pressure-based steady solver, gravity off and hydrogen with constant density 0.08189 kg/m³ and dynamic viscosity 8.411e-6 Pa·s.

For laminar runs, select Laminar and inlet speed 10.271 m/s. For turbulent runs, select SST k-omega and inlet speed 102.711 m/s. Turbulent inlet specification is Intensity and Hydraulic Diameter: 5.06% and 0.01 m; the saved outlet backflow turbulence uses the same values. Keep outlet gauge pressure at 0 Pa and a stationary no-slip wall.

Use SIMPLE, second-order pressure and second-order upwind momentum. Use second-order upwind k and omega for turbulent runs. In Solution > Monitors > Residuals, set the absolute scaled criteria to 1e-6 for every active equation, including k and omega. See the recorded-setting exception for turbulent M1/M2 in RESULTS_NOTES.md.

## 4. Solve and verify

Refresh the new mesh in Fluent, verify the boundary conditions and use Hybrid Initialization. Start with up to 500 iterations for the laminar cases or 1000 for the turbulent cases, then judge the actual convergence rather than the requested iteration count. Save each completed case/data pair to its own mesh folder.

Check residuals, inlet pressure stabilisation and inlet/outlet mass balance. For turbulent runs, display Turbulence > Wall Yplus on the wall surface with Node Values off. The M5 target here is y+ < 1, verified after solving.

## 5. Post-process

Create a centerline from (0, 0, 0) to (0, 0, 1) and a longitudinal plane at Y = 0. Plot static pressure and velocity magnitude against Z on the centerline. Display velocity and static-pressure contours on the longitudinal plane. Export residual and inlet-pressure histories, mesh detail/cross-section views, and the wall y+ contour for turbulent cases.

The longitudinal images have a high physical aspect ratio because the pipe length is 100 times its diameter. `mesh_overview.png` is a local mesh-detail view. Use the original dimensions, not the apparent size of an exported image, to interpret the geometry.
