# FC Tycoon Match Simulator - 3D Assets

3D models, animations, and textures for the [FC Tycoon Match Simulator](https://github.com/fc-tycoon/match-sim).

## Structure

```
match-sim-assets/
├── manifest.json       # Asset registry with metadata
├── models/
│   ├── player.glb      # Player character model
│   ├── player.blend    # Blender source file
│   ├── ball.glb        # Football/soccer ball
│   └── stadium1.glb    # Stadium environment
├── animations/
│   └── *.fbx           # Character animations (FBX format)
└── textures/
    └── grass_m.jpg     # Field grass texture
```

## Usage

This repository is designed to be used as a **Git submodule** of the Match Simulator:

```bash
# Clone Match Simulator with assets
git clone --recurse-submodules https://github.com/fc-tycoon/match-sim.git

# Or if already cloned, initialize submodule
cd match-sim
git submodule update --init --recursive
```

The assets are mounted at `assets/3d-assets/` in the Match Simulator project.

## Asset Loading

Assets are loaded via the `manifest.json` file which defines:
- Asset keys for programmatic access
- File paths (relative to this repo root)
- Loading priority (critical → high → normal → low)
- Material overrides
- Fallback primitives

The Match Simulator's asset loader prepends the `basePath` (`/3d-assets`) to all paths.

## Formats

| Type | Format | Notes |
|------|--------|-------|
| Models | GLB | Binary glTF, optimized for web |
| Animations | FBX | Better animation clip support than GLB |
| Textures | JPG/PNG | Standard image formats |
| Source | .blend | Blender project files |

## Git LFS

This repository uses **Git LFS** for large binary files. Ensure Git LFS is installed:

```bash
# Install Git LFS (one-time)
git lfs install

# Verify LFS is tracking files
git lfs ls-files
```

To initiate tracking (already done), the following command was executed:

```bash
# Files already in .gitattributes
git lfs track "*.glb" "*.fbx" "*.blend" "*.jpg"
```

## License

See [LICENSE.md](LICENSE.md) for full license terms.

**Summary**: Source-available license. Personal/educational use permitted. No redistribution of assets separately. Some assets have third-party licenses (CGTrader, Mixamo).

## Contributing

Asset contributions are welcome! Please ensure:
- Models are optimized for real-time rendering
- Include source files (.blend) when possible
- Follow existing naming conventions
- Update `manifest.json` for new assets
