# Conformance

Conformance beschreibt, wann ein Tool, Playbook, Quest-System oder KI-Agent behaupten darf, Teile des Real Life Network Protocols zu unterstützen.

## Grundregeln

Eine konforme Umsetzung MUSS:

1. Freiwilligkeit respektieren.
2. Ablehnung, Nicht-Reaktion und Rückzug als normale Ergebnisse behandeln.
3. Beziehungen und reale Begegnungen stärken, nicht ersetzen.
4. Menschen nicht ranken oder global bewerten.
5. Sichtbarkeit, Zustimmung und Kontext respektieren.
6. lokale Autonomie bewahren.
7. Quests als Einladungen formulieren.
8. KI-Agenten als unterstützend, nicht steuernd behandeln.

## Profile

### `rlnp-core@0.1`

Eine Umsetzung ist `rlnp-core@0.1`-konform, wenn sie:

- die Grundprinzipien des Protokolls respektiert,
- die Kernentitäten nicht widersprüchlich verwendet,
- soziale Operationen nicht in Pflicht-, Bewertungs- oder Kontrollmechanismen umdeutet.

### `rlnp-rollout@0.1`

Eine Umsetzung ist `rlnp-rollout@0.1`-konform, wenn sie:

- einen konkreten Pilotkontext beschreibt,
- Onboarding, Verifikation, Profil, Sichtbarkeit und Nachbereitung als freiwillige Flows anbietet,
- analoge oder organisatorische Fallbacks für technische Ausfälle vorsieht.

### `rlnp-quests@0.1`

Eine Umsetzung ist `rlnp-quests@0.1`-konform, wenn sie:

- Quests als freiwillige Einladungen modelliert,
- keine Menschen aufgrund abgeschlossener Quests hierarchisiert,
- den Zweck jeder Quest auf Beziehung, Commons, lokale Resilienz oder gemeinsames Handeln zurückführt.

### `rlnp-agent@0.1`

Eine Umsetzung ist `rlnp-agent@0.1`-konform, wenn sie:

- Agenten eine erkennbare Identität gibt,
- Vorschläge als Einladungen formuliert,
- menschliche Entscheidungen nicht ersetzt,
- nur mit Kontext arbeitet, für den Sichtbarkeit und Zustimmung bestehen.

## Noch offen

- Maschinenlesbares Conformance-Manifest.
- Testfälle für Agentenverhalten.
- Schema-Validatoren für Datenmodelle.
- Checklisten für Playbooks und Rollout-Slices.
