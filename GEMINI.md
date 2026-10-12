# Video Production & Character Animation Invariants

These invariants apply to video generation, animation retargeting, and scene assembly within this project.

## 1. LivePortrait Full-Frame Remapping
- **Never output isolated 512x512 face crops for final master shots.**
- Always invoke `execute_video` with `flag_remap_input=True` and `flag_stitching_input=True` (or execute `paste_back` onto the original high-resolution plate) to guarantee widescreen 1080p/2K composition with natural head-and-shoulders framing and crystal-clear definition.

## 2. Continuous Motion & Anti-Freeze Protocol
- Every character and dialogue shot must verify an inter-frame motion delta strictly exceeding **0.20** across all consecutive frames.
- Never hold static 0-delta frames at shot boundaries or before reactions. Introduce immediate micro-motion (eye contact, subtle head tilts, breathing) or smooth continuous cinematic camera transforms (subtle linear push-in / pan) to preserve natural fluidity.

## 3. Physical Object Grounding & Stacking
- Construction and building sequences must begin at ground level on the floor or rug foundation.
- Added components must be physically lowered and stacked from above by character hands, respecting gravity.
- Avoid optical flow motion interpolation (`minterpolate`) on retimed diffusion clips, which causes block warping and mid-air morphing.
