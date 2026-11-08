# Skill Routing Reference

Extended routing tables for the Blender Director.

## By Engine Target

All engines (Unity, Unreal, Godot, generic) go through `export-pipeline`; it holds the per-engine settings (FBX vs GLB, UCX collision, cm scale).

## By Production Phase

| Phase | Lead Skill | Validators |
|-------|------------|------------|
| Reference analysis | blender-director + reference-image-match | reference-analysis-template |
| Art direction lock | blender-director | production brief |
| Blockout | blender-modeler / discipline skill | blender-director |
| Detail pass | discipline skill | asset-optimization |
| UV pass | uv-workflow | texture-workflow |
| Look dev | lookdev + materials | qa-review |
| Camera / shot | camera-cinematography | rendering |
| FX / sim | vfx-fx / physics-sim / cloth-sim | compositing |
| Reference compare | rendering + lighting | visual-match-checklist |
| Scene layout | scene-assembly + set-dressing | qa-review |
| Performance | asset-optimization + lod-pipeline | collision-proxy |
| Delivery | export-pipeline | qa-review + validation-checklist |

## Parallel vs Sequential

**Sequential (default):** Art direction lock → Modeling → UV → Materials → Lookdev → Export

**Parallel allowed:**
- Material prototyping while UVs in progress (separate collections)
- Lighting setup while optimization runs on duplicate collection
- Collision proxies while LOD1+ generates
- Mood/world reference gathering during blockout

**Never parallel:**
- Retopology before sculpt complete
- Export before validation / qa-review
- Rigging before final topology locked
- Engine export before LOD/collision plan when required
