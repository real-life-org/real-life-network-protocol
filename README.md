# Real Life Network Protocol

Spezifikation für dezentrale Gemeinschaftsbildung, Commons und gemeinsames Handeln.

**Status:** Initialer Arbeitsstand  
**Start:** 2026-05-07  
**Ziel:** Das soziale Protokoll des Real Life Networks so beschreiben, dass Menschen, Apps und KI-Agenten damit praktisch arbeiten können.

---

## Zweck

Dieses Repository ist die Werkbank für das Real Life Network Protocol.

Es beschreibt nicht nur Werte oder Kultur, sondern wiederholbare soziale Operationen:

- Menschen kennenlernen, einladen, verifizieren, bestätigen und attestieren
- Veranstaltungen, Kreise und Rituale hosten
- Ressourcen teilen und Commons schaffen
- Projekte, Orte und lokale Strukturen aufbauen
- bestehende Initiativen verbinden
- Quests, App-Flows und Agenten-Handlungen daraus ableiten

Das Protokoll soll präzise genug sein, damit es in Apps, Datenmodellen, Playbooks und Agenten umgesetzt werden kann. Gleichzeitig muss es lesbar genug bleiben, dass Menschen es in realen Gemeinschaften anwenden können.

## Abgrenzung

| Repository | Rolle |
|---|---|
| [real-life-org/real-life-org-docs](https://github.com/real-life-org/real-life-org-docs) | Narrative Orientierung, Handbuch, Organisation, Netzwerktexte |
| [real-life-org/wot-spec](https://github.com/real-life-org/wot-spec) | Technische Spezifikation für Identität, Trust, Sync und Conformance |
| [real-life-org/real-life-stack](https://github.com/real-life-org/real-life-stack) | App-/UI-Baukasten und technische Implementierung sozialer Werkzeuge |
| [real-life-org/real-life-network-protocol](https://github.com/real-life-org/real-life-network-protocol) | Soziale Spezifikation für Netzwerkaufbau, Quests, Praktiken, Agenten und Rollout |
| [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game) | Spielgestaltung auf Basis der Quest-Schicht: Storylines, Adventures, Progression und Game-Mechaniken |
| [real-life-org/real-life-agent-protocol](https://github.com/real-life-org/real-life-agent-protocol) | Agenten-Arbeitsprotokoll: Tasks, Runs, Reviews, Human Gates und Feedback in Specs |

## Spezifikations-Landkarte

| Bereich | Zweck |
|---|---|
| [real-life-network-protocol.md](real-life-network-protocol.md) | Initiale Gesamtspezifikation |
| [01-principles](01-principles/) | Grundprinzipien und Nicht-Ziele |
| [02-entities](02-entities/) | Soziale Entitäten des Netzwerks |
| [03-social-operations](03-social-operations/) | Kernoperationen des Netzwerkaufbaus |
| [04-practices-and-rituals](04-practices-and-rituals/) | Wiederkehrende Formate und Rituale |
| [05-quests](05-quests/) | Freiwillige Handlungseinladungen, Quest-Katalog und Quest-Mechanik |
| [06-data-model](06-data-model/) | App- und Graphmodell für soziale Operationen |
| [07-agent-protocol](07-agent-protocol/) | Handlungsrahmen für KI-Agenten im Netzwerk |
| [08-rollout](08-rollout/) | Rollout-Slices, Inventuren und Pilot-Playbooks |
| [schemas](schemas/) | Maschinenlesbare Schemata |
| [playbooks](playbooks/) | Praktische Anleitungen für Hosts, Crews und Kreise |
| [examples](examples/) | Konkrete Beispielabläufe |
| [conformance](conformance/) | Prüfbarkeit und Protokoll-Konformität |

## Aktueller Arbeitsfokus

Der erste Fokus ist ein praktischer Rollout-Slice für Pax/Festival-Kontexte:

1. [Pax-MVP-Slice definieren](08-rollout/pax-rollout-slice.md)
2. [soziale Operationen auf App-Flows und Datenmodelle mappen](06-data-model/operations-mapping.md)
3. [Quest-Katalog v0.1 und Quest-Mechanik schärfen](05-quests/)
4. Vernetzungszelt-Playbook erstellen
5. Agenten-Handlungsrahmen mit [real-life-org/real-life-agent-protocol](https://github.com/real-life-org/real-life-agent-protocol) verbinden

Siehe [08-rollout/rollout-inventur.md](08-rollout/rollout-inventur.md).

## Arbeitsweise

Dieses Repo folgt einem spec-first Ansatz:

- Jede neue Praxis wird als soziale Operation beschrieben.
- Jede Operation wird auf Inputs, Ablauf, Outputs, Risiken, nächste Schritte, App-Unterstützung, Agenten-Unterstützung und Metriken gemappt.
- Quests sind Handlungseinladungen, keine Pflichten.
- Metriken dürfen Netzwerkaktivität sichtbar machen, aber Menschen nicht ranken.
- Agenten dürfen unterstützen, erinnern, verbinden und reflektieren, aber nicht steuern.
- Agentische Spec- und Softwarearbeit wird im [Real Life Agent Protocol](https://github.com/real-life-org/real-life-agent-protocol) beschrieben.

## Lizenz

Noch zu entscheiden.
