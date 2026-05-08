# Versioning

Dieses Repository verwendet semantisch lesbare Protokoll-Versionen.

## Versionstypen

| Typ | Bedeutung |
|---|---|
| `draft` | Arbeitsstand ohne Stabilitätsversprechen |
| `v0.x` | Frühe Spezifikation, geeignet für Pilotprojekte |
| `v1.0` | Erste stabile Version für breitere Implementierung |

## Profil-Versionen

Konformität wird über Profile ausgedrückt:

- `rlnp-core@0.1` — Prinzipien, Entitäten und soziale Kernoperationen
- `rlnp-rollout@0.1` — minimale Pilot-/Festival-Rollout-Fähigkeit
- `rlnp-quests@0.1` — Quest-Modell als freiwillige Einladungen
- `rlnp-game@0.1` — Real-Life-Game-Grundmechanik auf Basis von WoT, RLS und RLNP
- `rlnp-agent@0.1` — KI-Agenten-Handlungsrahmen
- `rlnp-data@0.1` — Datenmodell und Relationen für App-Implementierungen

## Änderungsregeln

- Normative Begriffe wie MUSS, DARF NICHT, SOLLTE und DARF dürfen nur bewusst geändert werden.
- Jede breaking change an Entitäten, Operationen, Schemata oder Conformance-Profilen muss im Changelog genannt werden.
- Pilot-Slices dürfen experimenteller sein als Core-Spezifikationen, müssen aber klar als solche markiert werden.
