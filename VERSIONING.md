# Versioning

Dieses Repository verwendet semantisch lesbare Protokoll-Versionen.

## Versionstypen

| Typ | Bedeutung |
|---|---|
| `draft` | Arbeitsstand ohne Stabilitaetsversprechen |
| `v0.x` | Fruehe Spezifikation, geeignet fuer Pilotprojekte |
| `v1.0` | Erste stabile Version fuer breitere Implementierung |

## Profil-Versionen

Konformitaet wird ueber Profile ausgedrueckt:

- `rlnp-core@0.1` — Prinzipien, Entitaeten und soziale Kernoperationen
- `rlnp-rollout@0.1` — minimale Pilot-/Festival-Rollout-Faehigkeit
- `rlnp-quests@0.1` — Quest-Modell als freiwillige Einladungen
- `rlnp-agent@0.1` — KI-Agenten-Handlungsrahmen
- `rlnp-data@0.1` — Datenmodell und Relationen fuer App-Implementierungen

## Aenderungsregeln

- Normative Begriffe wie MUSS, DARF NICHT, SOLLTE und DARF duerfen nur bewusst geaendert werden.
- Jede breaking change an Entitaeten, Operationen, Schemata oder Conformance-Profilen muss im Changelog genannt werden.
- Pilot-Slices duerfen experimenteller sein als Core-Spezifikationen, muessen aber klar als solche markiert werden.
