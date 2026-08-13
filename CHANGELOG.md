# Changelog

## Unreleased

- Initiales Repository für das Real Life Network Protocol angelegt.
- Initiale Gesamtspezifikation aus `real-life-org-docs/netzwerk-protokoll.md` übernommen.
- Rollout-Inventur in `08-rollout/rollout-inventur.md` übernommen.
- Erste Struktur für Prinzipien, Entitäten, soziale Operationen, Praktiken, Quests, Datenmodell, Agenten, Rollout, Schemas, Playbooks, Beispiele und Conformance angelegt.
- Pax-Rollout-Slice angelegt und Reihenfolge geklärt: App/Web-App laden, lokale Identität erzeugen, dann Pax-Space beitreten.
- Operations-Mapping für Pax v0.1 angelegt: App-Flows, Datenobjekte, Relationen, Confirmations, Quests, Agentenhilfe und Metriken.
- Quest-Katalog v0.1 mit 40 freiwilligen Einladungen für Pax/Festival, lokale Kreise und App-v0.1-Nutzerführung angelegt.
- Quest-Mechanik v0.1 angelegt: Quest-Autorenschaft, Host/Systemquests, Sichtbarkeit, Completion, Badges als Confirmation-Display, Orts-/Zeitbezug, Forks und klare Abgrenzung zum Game-Repo.
- Quest-Lebenszyklus in Quest-Status und QuestRun getrennt, damit mehrere Menschen dieselbe Quest unabhängig voneinander durchführen können.
- QuestRun als eigenes RLS-Item mit Relations zur Quest und zum Menschen modelliert.
- Sichtbarkeit geschärft: Region ist Auffindbarkeits-/Kartenkontext, keine eigene Sichtbarkeitsstufe.
- Badges als visuell dargestellte Confirmations präzisiert; portable Badges brauchen eine signierte Attestation; Selbst-Claims oder Evidence erzeugen keinen portablen Badge.
- Pax v0.1 auf lokale Handlungseinladungen/Suggestions begrenzt; vollwertige Quest-/QuestRun-Items bleiben optional.
- Orts-, Zeit- und Kontextbezug von Quests und QuestRuns geschärft: Kontext bevorzugt per Relation, Ort/Zeit steuern Auffindbarkeit statt Sichtbarkeit.
- Quest-Typen geglättet: keine harte Taxonomie im Basisprotokoll; Klassifizierung läuft über Operationen, Intentionen, Tags und Templates.
- Minimale RLS-Item-Felder für `quest` und `quest-run` festgezogen und Beispiele auf `data.status`, `data.visibility`, lokale Completion und Evidence vereinheitlicht.
- Completion-Logik geschärft: lokale Completion, Evidence, Confirmation und portable Attestation getrennt.
- Quest-seitige Completion-Regeln ergänzt: `evidencePolicy`, `confirmationPolicy`, `completionConfirmationTemplate` und `safetyRequirements` gehören zur RLNP-Quest-Logik, nicht zur Game-Schicht.
- Quest-Evidence geglättet: konkrete Evidence gehört zum QuestRun oder Werk-Kontext; Quests definieren nur eine Evidence Policy mit optionalem `required` und akzeptierten Typen.
- Auf [real-life-org/real-life-agent-protocol](https://github.com/real-life-org/real-life-agent-protocol) als eigenes Repository für agentische Spec- und Softwarearbeit verwiesen.
- Kreis (§6.4) ausgebaut: Form und Zugang als zwei unabhängige, veränderbare Wahlmöglichkeiten jedes Kreises; Kopplung entsteht durch Menschen in mehreren Kreisen statt durch übergeordnete Kreise; Teilung bei Wachstum; kein Durchgriff des Ursprungskreises; ein Kreis kann sich eine Rechtsform als Gefäß geben, deren Organe Rollen des Kreises sind.
- Rolle als Grundentität (§6.13) und Glossareintrag ergänzt: übernommene Verantwortung gegenüber einem Kreis, freiwillig und zurückgebbar, abgegrenzt von der Selbstbeschreibung eines Menschen.
- Soziale Operation „Rollen benennen und übernehmen" (§8.13) ergänzt und damit die letzte fehlende Operation des Handschlag-Paars geschlossen. Norm: Ein Kreis bezeugt nicht als Ganzes, es bezeugen die Menschen, die dabei waren.
- Die Ordner `01-principles`, `02-entities`, `03-social-operations`, `04-practices-and-rituals` und `07-agent-protocol` entfernt. Sie enthielten nur Wegweiser auf die Gesamtspezifikation; deren Aufteilung war geplant, ist nie erfolgt und ist auch nicht beabsichtigt: Die Gesamtspezifikation soll in einem Zug lesbar bleiben.
- §11.2 von einer Feldliste auf Prosa umgestellt. Die Gesamtspezifikation nennt keine Datenfelder mehr; Felder und Formate stehen in `05-quests/quest-mechanik.md`.
- Alle Verweise auf die abgelöste `wot-spec` und auf das WoT-Trust-VC-JWS-Format entfernt. Das Protokoll nennt jetzt **Anforderungen statt Formate**: Eine Confirmation, die portabel sein soll, MUSS als signierte, unabhängig prüfbare Attestation ausgestellt werden; welches Format das erfüllt, legt die technische Spezifikation fest. Betroffen: `CONFORMANCE.md` (`rlnp-data@0.1`), `GLOSSARY.md` (Attestation, Badge), `README.md`, `06-data-model/operations-mapping.md` (Designregeln, Objektkatalog, §9.2/§9.3 samt der beiden Beispiel-Credentials), `05-quests/quest-mechanik.md`, `05-quests/quest-katalog.md`, `08-rollout/pax-rollout-slice.md`, `schemas/README.md`, `examples/README.md`, `06-data-model/README.md`. Hintergrund: Das bisher vorgeschriebene Format wird von der neuen technischen Spezifikation zurückgewiesen; eine danach konforme Umsetzung hätte ungültige Credentials erzeugt. Auf die neue Spezifikation wird bewusst noch nicht verwiesen, solange sie sich bewegt.
