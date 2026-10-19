---
type: Reference
title: Modding API
description: Gen 1 defines API 3 conventions; generation adapters provide common mod-facing records and services.
tags:
  - modding
  - api
  - compatibility
status: draft
sources:
  - id: loader
    resource: ../src/mods/Loader.lua
  - id: content
    resource: ../src/mods/UnifiedContent.lua
  - id: records
    resource: ../src/mods/UnifiedRecords.lua
  - id: world
    resource: ../src/mods/UnifiedWorld.lua
  - id: battle
    resource: ../src/mods/UnifiedBattle.lua
  - id: callbacks
    resource: ../src/mods/UnifiedCallbacks.lua
  - id: wiki
    resource: https://github.com/bryanthaboi/gen1recomp/wiki/Reference-Mod-Object
  - id: guide
    resource: ../docs/modding.md#portable-api-3
generated:
  by: process:project-maintenance
  at: "2026-10-15T11:49:49Z"
---

# Contract

Gen 1 is the authoritative source for public names, shapes and units. Generation 2 adds to that contract; Generation 3 adds to Generation 2. The upstream wiki supplies the established mod-object and lifecycle conventions.[^wiki] Manifest API 3 selects that shared boundary; API 1/2 retain their native accessor path. Loader owns selection, per-mod isolation, rollback, freeze and lazy engine access.[^loader]

UnifiedContent translates common species, move, item, trainer and encounter records. Species use Gen 1 `special`, `level1Moves`, `learnset` and evolution target `species`; trainer parties, encounter levels and move effects follow Gen 1. Later split stats and native mechanics remain explicit extensions; conversion retains native storage. Unsupported native systems and fields remain explicit results, discoverable through capability queries.[^content]

UnifiedRecords owns detached runtime Pokémon views and validated identifier/stat/status/move translation. Native tables and serialized saves keep their existing shapes.[^records]

World and battle handles resolve the current provider. World owns portable mod flags, block-ID metadata and native action sequencing; Battle retains native input authority and normalizes snapshots and percentage capture previews following Gen 1.[^world][^battle]

UnifiedCallbacks adapts supported record/identifier boundaries while native buses retain ownership, priorities, unsubscribe and rollback. Custom-event emission is owner-scoped; subscribing across mod namespaces remains legal.[^callbacks]

# Authoring and evidence

The portable API guide in `docs/modding.md`, section `Portable API 3` describes API 3 and the runnable example. Native game-specific content IDs, mechanics and asset limits remain relevant; `mod.game` and explicitly native fields are engine interfaces.[^guide]

Fixture tests can verify source behavior and native table changes. They do not prove an installed process loaded this checkout, human visual acceptance, or ROM-backed behavior for every game. Consult current test receipts and the affected auto-discovered modkit cases before making a validation claim.

[^loader]: ../src/mods/Loader.lua
[^content]: ../src/mods/UnifiedContent.lua
[^records]: ../src/mods/UnifiedRecords.lua
[^world]: ../src/mods/UnifiedWorld.lua
[^battle]: ../src/mods/UnifiedBattle.lua
[^callbacks]: ../src/mods/UnifiedCallbacks.lua
[^guide]: ../docs/modding.md#portable-api-3

[^wiki]: https://github.com/bryanthaboi/gen1recomp/wiki/Reference-Mod-Object
