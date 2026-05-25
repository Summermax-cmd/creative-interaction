# 创意交互尝试 · Creative Interaction Experiments

Single-file HTML prototypes exploring gestural and physical interactions in the browser. No build step — open the file or visit the live demo.

## Live demos

| Demo | Link | Concept |
| --- | --- | --- |
| Invisible Cloth | <https://summermax-cmd.github.io/creative-interaction/> | A camouflaged cloth hangs in front of the camera. Pinch in the air to grab it; lift quickly to reveal what hides behind. |
| Water Shader | <https://summermax-cmd.github.io/creative-interaction/water.html> | The camera feed becomes the surface of water. Move your fingertips and watch ripples spread, refract, and disperse. |

Camera permission required. Best on a phone (rear camera, gesture in front of the lens).

## Tech

- **Invisible Cloth** — p5.js + MediaPipe Hands + Canvas2D. Verlet-integrated cloth (38×35 grid, 12 constraint iterations), three-layer optical-camouflage rendering (camera → media → camera-clipped-to-cloth), pinch-with-hysteresis grab, fling/drop dynamics.
- **Water Shader** — WebGL1 + MediaPipe Hands. FBO ping-pong wave equation with 9-tap isotropic Laplacian and non-linear damping; aspect-corrected capsule SDF for finger interaction; display pass with gradient-driven refraction, Laplacian lens, RGB dispersion, Schlick Fresnel, and dual-lobe specular. Half-float render targets with float fallback. Branch-free shader logic via `step()` / `mix()`.

## Run locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000/
```

A local HTTPS context isn't needed for `localhost`, but camera + MediaPipe require HTTPS or localhost — `file://` will fail.
