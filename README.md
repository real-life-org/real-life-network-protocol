# Real Life Network Protocol

Spezifikation für dezentrale Gemeinschaftsbildung, Commons und gemeinsames Handeln.

**Status:** Entwurf, in aktiver Arbeit  
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
| [real-life-org/real-life-stack](https://github.com/real-life-org/real-life-stack) | App-/UI-Baukasten und technische Implementierung sozialer Werkzeuge |
| [real-life-org/real-life-network-protocol](https://github.com/real-life-org/real-life-network-protocol) | Soziale Spezifikation für Netzwerkaufbau, Quests, Praktiken, Agenten und Rollout |
| [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game) | Spielgestaltung auf Basis der Quest-Schicht: Storylines, Adventures, Progression und Game-Mechaniken |
| [real-life-org/real-life-agent-protocol](https://github.com/real-life-org/real-life-agent-protocol) | Agenten-Arbeitsprotokoll: Tasks, Runs, Reviews, Human Gates und Feedback in Specs |

Daneben steht die **technische Spezifikation**: Identität, Begegnung, Gruppen-Autorität und Transport, also Formate, Signaturen und Prüfbarkeit. Sie wird derzeit neu gefasst. Dieses Protokoll bindet sich deshalb an kein Format, sondern nennt Anforderungen: was eine Aussage leisten muss, damit sie portabel, signiert und unabhängig prüfbar ist. Welches Format das erfüllt, steht dort, nicht hier.

Die beiden stehen **nebeneinander, nicht übereinander**: Dieses Protokoll ist normativ für die **Bedeutung** eines Vorgangs — was ein Kreis, eine Rolle, eine Begegnung ist und welche Normen für sie gelten. Die technische Spezifikation ist normativ für die **Konstruktion**. Wo beide dasselbe Wort benutzen, gewinnt für die Bedeutung dieses Dokument, für die Umsetzung das andere.

## Spezifikations-Landkarte

| Bereich | Zweck |
|---|---|
| [real-life-network-protocol.md](real-life-network-protocol.md) | Die Gesamtspezifikation: Prinzipien, Entitäten, soziale Operationen, Praktiken, Agenten |
| [quests](quests/) | Freiwillige Handlungseinladungen, Quest-Katalog und Quest-Mechanik |
| [data-model](data-model/) | App- und Graphmodell für soziale Operationen |
| [rollout](rollout/) | Rollout-Slices, Inventuren und Pilot-Playbooks |
| [schemas](schemas/) | Maschinenlesbare Schemata |
| [playbooks](playbooks/) | Praktische Anleitungen für Hosts, Crews und Kreise |
| [examples](examples/) | Konkrete Beispielabläufe |
| [conformance](conformance/) | Prüfbarkeit und Protokoll-Konformität |

## Aktueller Arbeitsfokus

Die Gesamtspezifikation wurde im August 2026 überarbeitet: Kreis, Rolle, Bezeugen, Sichtbarkeit und das Feld haben ihre heutige Fassung bekommen. Woran als Nächstes gearbeitet wird:

1. Die Naht zur technischen Spezifikation beschreiben: welcher Begriff dort ein Gegenstück hat, welcher noch keines, und welcher bewusst nie eines bekommt.
2. Den Konfliktprozess (Abschnitt 13) ausarbeiten — er ist seit Mai unberührt.
3. Selbstbeschreibungen in der Praxis erproben und das erste Vokabular mit dem Game Pack abstimmen.
4. Playbooks schreiben: Vernetzungszelt, Kreis starten, Initiative andocken.
5. Konformität prüfbar machen: Manifest, Schemata, Testfälle.

Der Ordner [rollout](rollout/) enthält den Stand aus dem Frühjahr, entstanden für ein konkretes Festival und inzwischen generisch formuliert. Er wird nach den Erfahrungen der Saison 2026 überarbeitet.

## Arbeitsweise

Dieses Repo folgt einem spec-first Ansatz:

- Jede neue Praxis wird als soziale Operation beschrieben.
- Jede Operation wird auf Inputs, Ablauf, Outputs, Risiken, nächste Schritte, App-Unterstützung, Agenten-Unterstützung und Metriken gemappt.
- Quests sind Handlungseinladungen, keine Pflichten.
- Metriken dürfen Netzwerkaktivität sichtbar machen, aber Menschen nicht ranken.
- Agenten dürfen unterstützen, erinnern, verbinden und reflektieren, aber nicht steuern.
- Agentische Spec- und Softwarearbeit wird im [Real Life Agent Protocol](https://github.com/real-life-org/real-life-agent-protocol) beschrieben.

Was sich beim Schreiben bewährt hat: Bevor eine Mechanik geändert wird, das **Wort** prüfen. Mehrere Widersprüche im Dokument sind nicht aus falschen Entscheidungen entstanden, sondern daraus, dass Implementierende der Alltagsbedeutung eines Begriffs gefolgt sind statt seiner Definition.

## Lizenz

Noch zu entscheiden.
