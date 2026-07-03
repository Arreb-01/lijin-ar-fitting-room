# AR Model Optimization Report

Generated: 2026-07-03

## Method

- Tool: `@gltf-transform/cli` 4.4.1.
- First-pass command: `optimize --compress draco --texture-compress webp --texture-size 1024 --simplify-ratio 0.06 --simplify-error 0.02`.
- `dali_god.glb` needed a second simplification pass before final compression because the one-pass output stayed above the mobile triangle target.
- Output target: `03_AR/assets/models_optimized/*.glb`.

## Results

| Model | Source size / triangles | Optimized size / triangles | Required extensions |
| --- | ---: | ---: | --- |
| frog | 54.22 MB / 1,953,278 tris | 0.50 MB / 117,195 tris | EXT_texture_webp, KHR_draco_mesh_compression |
| gonggong | 53.68 MB / 1,946,768 tris | 0.50 MB / 116,806 tris | EXT_texture_webp, KHR_draco_mesh_compression |
| dali_god | 56.89 MB / 1,938,770 tris | 0.52 MB / 105,882 tris | EXT_texture_webp, KHR_draco_mesh_compression |
| deer | 53.15 MB / 1,927,458 tris | 0.49 MB / 115,646 tris | EXT_texture_webp, KHR_draco_mesh_compression |
| human | 51.59 MB / 1,842,677 tris | 0.47 MB / 110,558 tris | EXT_texture_webp, KHR_draco_mesh_compression |

## Notes

- `fog.glb` from the handoff package is treated as the frog model and exported as `frog.glb`.
- All optimized models meet the first mobile budget: under 12 MB and under 120k triangles.
- The optimized files require WebP texture and Draco mesh decoding. H5 `model-viewer` supports this path; the WeChat XR-FRAME project should verify Draco support on target devices before using these assets as final production builds.
