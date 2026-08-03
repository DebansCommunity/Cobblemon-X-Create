# Cobblemon X Create — Recipes & Crafting

This repository holds the **crafting content** for the *Cobblemon X Create* modpack:
datapack recipes and KubeJS scripts. It also serves as the official **issue tracker**.

> ⚠️ The modpack is in **Alpha**. The focus is corepack stability; a large recipe
> overhaul is planned, so crafting balance is still a work in progress.

- 📖 Modpack page: https://modrinth.com/modpack/cobblemon-x-create
- 🐛 Found a bug or a broken recipe? [Open an issue](../../issues/new/choose)
- 🤝 Want to contribute a recipe? Read [CONTRIBUTING.md](CONTRIBUTING.md) and
  [docs/conventions.md](docs/conventions.md)

## Minecraft version

- Minecraft **1.21.1** (NeoForge)
- Datapack `pack_format`: **48**

## Repository layout

```
kubejs/
  server_scripts/        # KubeJS recipe scripts (loaded recursively)
    create/              # Create-related recipes
    cobblemon/           # Cobblemon-related recipes
datapacks/
  cxc/                   # the datapack
    pack.mcmeta
    data/cxc/recipe/     # brand-new recipes (own namespace)
docs/
  conventions.md         # naming rules, override vs add, how to test
```

The layout mirrors what goes into the modpack `overrides/` folder, so you can copy
these files straight into your `.minecraft` instance to test.

## Rule of thumb

- **KubeJS** → modifying or removing existing recipes.
- **Datapack** → adding brand-new recipes.
- Never define the *same* recipe in both places (they overwrite each other silently).
