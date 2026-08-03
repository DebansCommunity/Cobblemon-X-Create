# Conventions

Rules to keep the crafting content consistent and reviewable.

## Naming

- Files and folders: `snake_case`, English, no spaces, no accents.
- File name = recipe intent. For datapacks, the file name **is** the recipe ID
  (e.g. `andesite_alloy.json` → `cxc:andesite_alloy`).
- Split scripts by mod, then by mechanic: `create/mixing.js`, `create/pressing.js`.
  One giant file is hard to review and causes Git conflicts.

## KubeJS vs Datapack — which to use?

| Goal | Use | Where |
|---|---|---|
| Add a brand-new recipe | Datapack | `datapacks/cxc/data/cxc/recipe/...` |
| Modify an existing recipe | KubeJS | `kubejs/server_scripts/.../*.js` |
| Remove an existing recipe | KubeJS | `kubejs/server_scripts/.../*.js` |

> ❗ Never define the **same** recipe in both a datapack and KubeJS — one silently
> overwrites the other. This is exactly the kind of "recipe conflict" we want to avoid.

## Datapack: new recipes vs overrides

- **New recipe** (your own): put it under your namespace →
  `data/cxc/recipe/create/my_recipe.json`. Subfolders are allowed and become part of
  the ID (`cxc:create/my_recipe`).
- **Overriding a mod's recipe**: the file path must match the target recipe's ID,
  under **that mod's** namespace. Example: replacing Create's andesite alloy →
  `data/create/recipe/andesite_alloy.json`. (Prefer KubeJS for this.)

## KubeJS folders

- `server_scripts/` — recipes (loaded recursively, all `.js`).
- Prefix a file with `_` (e.g. `_registry.js`) for things that must load first,
  like custom items or tags.

## How to test before opening a PR

1. Copy your changed files into your `.minecraft` instance
   (`kubejs/` and/or the datapack).
2. Run `/reload` in-game (or restart for startup scripts).
3. Check the recipe in **JEI/EMI**: it must appear and be craftable.
4. Confirm no ingredient is unobtainable and no conflict warning appears in the log.

## Version

- Minecraft **1.21.1** — datapack folder is `recipe` (singular), `pack_format` **48**.
