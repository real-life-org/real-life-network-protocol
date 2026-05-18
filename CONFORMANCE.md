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
7. Quests als Handlungseinladungen formulieren.
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

- Quests als freiwillige Handlungseinladungen modelliert,
- keine Menschen aufgrund abgeschlossener Quests hierarchisiert,
- globalen Quest-Status von persönlichen QuestRuns trennt,
- Quest-Autorenschaft, Sichtbarkeit, lokale Completion, Evidence, Confirmation und Badge-Vergabe nachvollziehbar modelliert,
- portable Badges als visuell dargestellte signierte Attestations behandelt,
- Selbst-Claims oder hochgeladene Evidence nicht als portable Completion, Badge oder Self-Attestation ausgibt,
- QR-Scans, Host-Bestätigungen, gegenseitige Bestätigungen und Systemereignisse als Evidence, Trigger oder Confirmer-/Issuer-Rollen für Confirmations behandelt, nicht als eigene portable Wahrheitsarten,
- `confirmationPolicy`, `requiredEvidence`, `completionConfirmationTemplate` und `safetyRequirements` als Quest-Completion-Logik behandelt, nicht als Game-Mechaniken,
- nur solche Confirmations als Quest-Completion zählt, die zu einer vorhandenen `confirmationPolicy` passen,
- hostlose Systemquests trotzdem einer erkennbaren System-/Agenten-Identität zuordnet,
- den Zweck jeder Quest auf Beziehung, Commons, lokale Resilienz oder gemeinsames Handeln zurückführt,
- keine feste Quest-Typ-Taxonomie als Voraussetzung für Interoperabilität verlangt,
- keine Game-Mechaniken wie XP, Level, Skill-Trees, Avatar-Items, Storylines oder Campaigns als Voraussetzung für Basis-Interoperabilität verlangt.

### `rlnp-agent@0.1`

Eine Umsetzung ist `rlnp-agent@0.1`-konform, wenn sie:

- Agenten eine erkennbare Identität gibt,
- Vorschläge als Einladungen formuliert,
- menschliche Entscheidungen nicht ersetzt,
- nur mit Kontext arbeitet, für den Sichtbarkeit und Zustimmung bestehen.

### `rlnp-data@0.1`

Eine Umsetzung ist `rlnp-data@0.1`-konform, wenn sie:

- Confirmations als backend-agnostische Views mit sichtbarer Trust-Stufe behandelt,
- WoT-Verifikationen und Attestations als WoT-Trust-VC-JWS behandelt, wenn eine Confirmation portable und signiert sein soll,
- Profile, Quests und QuestRuns als generische Real-Life-Stack-Items oder kompatible Item-Views modelliert,
- Angebote und Bedürfnisse in Pax v0.1 als einfache Profil-Tags behandeln kann, auch wenn sie zunächst aus dem WoT-Profil kommen und in der RLS-Referenz noch nicht vollständig implementiert sind,
- vereinfachte Confirmation-, Kontakt- oder UI-Objekte als Projektionen ausweist, nicht als portable Quelle der Wahrheit.

## Noch offen

- Maschinenlesbares Conformance-Manifest.
- Testfälle für Agentenverhalten.
- Schema-Validatoren für Datenmodelle.
- Checklisten für Playbooks und Rollout-Slices.
