# Changelog

## Unreleased

- Initiales Repository für das Real Life Network Protocol angelegt.
- Initiale Gesamtspezifikation aus `real-life-org-docs/netzwerk-protokoll.md` übernommen.
- Rollout-Inventur in `08-rollout/rollout-inventur.md` übernommen.
- Erste Struktur für Prinzipien, Entitäten, soziale Operationen, Praktiken, Quests, Datenmodell, Agenten, Rollout, Schemas, Playbooks, Beispiele und Conformance angelegt.
- Pax-Rollout-Slice angelegt und Reihenfolge geklärt: App/Web-App laden, lokale Identität erzeugen, dann Pax-Space beitreten.
- Operations-Mapping für Pax v0.1 angelegt: App-Flows, Datenobjekte, Relationen, Claims, Quests, Agentenhilfe und Metriken.
- Quest-Katalog v0.1 mit 40 freiwilligen Einladungen für Pax/Festival, lokale Kreise und App-v0.1-Nutzerführung angelegt.
- Quest-Mechanik v0.1 angelegt: Quest-Autorenschaft, Host/Systemquests, Sichtbarkeit, Completion, Badges als Attestations, Orts-/Zeitbezug, Forks und klare Abgrenzung zum Game-Repo.
- Quest-Lebenszyklus in Quest-Status und QuestRun getrennt, damit mehrere Menschen dieselbe Quest unabhängig voneinander durchführen können.
- QuestRun als eigenes RLS-Item mit Relations zur Quest und zum Menschen modelliert.
- Sichtbarkeit geschärft: Region ist Auffindbarkeits-/Kartenkontext, keine eigene Sichtbarkeitsstufe.
- Badges als visuell dargestellte WoT-Attestations präzisiert; Selbst-Claims oder Evidence erzeugen keinen portablen Badge.
- Pax v0.1 auf lokale Handlungseinladungen/Suggestions begrenzt; vollwertige Quest-/QuestRun-Items bleiben optional.
- Orts-, Zeit- und Kontextbezug von Quests und QuestRuns geschärft: Kontext bevorzugt per Relation, Ort/Zeit steuern Auffindbarkeit statt Sichtbarkeit.
- Quest-Typen geglättet: keine harte Taxonomie im Basisprotokoll; Klassifizierung läuft über Operationen, Intentionen, Tags und Templates.
- Minimale RLS-Item-Felder für `quest` und `quest-run` festgezogen und Beispiele auf `data.status`, `data.visibility`, lokale Completion und Evidence vereinheitlicht.
- Completion-Logik geschärft: lokale Completion, Evidence und Attestation getrennt; portable Completion und Badges entstehen nur aus WoT-Attestations.
- Quest-seitige Completion-Regeln ergänzt: `attestationPolicy`, `requiredEvidence`, `completionAttestationTemplate` und `safetyRequirements` gehören zur RLNP-Quest-Logik, nicht zur Game-Schicht.
- Auf [real-life-org/real-life-agent-protocol](https://github.com/real-life-org/real-life-agent-protocol) als eigenes Repository für agentische Spec- und Softwarearbeit verwiesen.
