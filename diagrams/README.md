# diagrams/

PlantUML diagrams for this repository. See `DIAGRAMS.md` at the repo root for setup instructions.

## Header convention

Every `.puml` file in this folder starts with:

```plantuml
!include transitrix-theme.puml
```

`transitrix-theme.puml` applies the Transitrix brand palette (petrol borders, petrol-tint fills, amber/orange for author emphasis) and sets `!pragma layout smetana` — PlantUML's pure-Java layout engine, which removes the Graphviz external dependency and makes rendering deterministic across machines.

## Hierarchy tints

Use the named tint levels to signal structure:

| Level | Hex | Use |
|---|---|---|
| High / top | `#b3c8cf` | Top-level strategic nodes |
| Mid | `#ccd8dc` | Mid-level groupings |
| Default / leaf | `#e8f2f5` | Most nodes (default fill) |
| Large area | `#f4f9fb` | Packages, frames, backgrounds |

Apply tints directly in the diagram body:
```plantuml
component "Vision" #b3c8cf
component "Goal" #ccd8dc
component "Action" #e8f2f5
```

## Emphasis colours

Reserved for author-assigned attention. Apply sparingly:

| Colour | Hex | Use |
|---|---|---|
| Amber | `#ffaf00` | Normal emphasis ("this matters") |
| Orange | `#ff4d00` | Focus / active / high emphasis |

## Status colours (functional palette — separate namespace)

Never use brand colours for status. Use the functional palette instead:

| Status | Hex |
|---|---|
| Success | `#1f7a3f` |
| Warning | `#a76b00` |
| Error | `#b3261e` |
| Info | `#3b6cb3` |
