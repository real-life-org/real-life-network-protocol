# Quest-Mechanik

**Status:** Entwurf v0.1
**Datum:** 2026-05-08
**Scope:** Interoperable Quest-Schicht des Real Life Network Protocols.

---

## 1. Zweck

Dieses Dokument beschreibt Quests als Teil des Real Life Network Protocols.

Eine Quest ist eine freiwillige Handlungseinladung. Sie lädt zu einer konkreten realen Handlung im Kontext des Netzwerks ein. Sie kann in einer App, durch eine Crew, durch einen Host, durch einen lokalen Kreis oder durch einen Agenten vorgeschlagen werden. Sie bleibt immer ablehnbar und darf nicht zu Pflicht, Score oder sozialer Kontrolle werden.

Die Quest-Mechanik soll präzise genug sein, damit Apps, Datenmodelle, Playbooks und Agenten damit arbeiten können:

- Quests erstellen,
- Quests vorschlagen,
- Quests sichtbar machen,
- QuestRuns dokumentieren,
- Abschlüsse von QuestRuns bestätigen,
- Beiträge als Attestations anerkennen,
- Quests kopieren oder lokal anpassen.

## 2. Abgrenzung zum Game

Sprachlich gilt:

```text
Quest = standardisierte freiwillige Handlungseinladung.
Game  = spielerischer Rahmen, der Quests, Orte, Ressourcen, Rollen und Geschichten verbindet.
```

Eine Quest kann ohne Game existieren. Das Game benutzt Quests als standardisierte Handlungseinheiten.

Dieses Repository definiert nur die Quest-Schicht. Es definiert NICHT:

- XP,
- Level,
- Skill-Trees,
- Avatar-Items,
- Inventory,
- Quest-Reihen,
- Adventures,
- Storylines,
- Campaigns,
- Game Master Tools,
- Balancing,
- Spielästhetik,
- vollständige Kinder-/Jugendlichen-Mechaniken.

Diese Themen gehören in [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game).

## 3. Normative Leitplanken

Eine Quest MUSS:

1. freiwillig sein,
2. ablehnbar oder ausblendbar sein,
3. ohne negative Bewertung unvollendet bleiben dürfen,
4. ihren sozialen Zweck erkennen lassen,
5. Sichtbarkeit und Zustimmung respektieren,
6. keine riskanten, beschämenden oder übergriffigen Nachweise verlangen.

Eine Quest DARF NICHT:

- Menschen global ranken,
- sozialen Druck erzeugen,
- Profilfortschritt als Menschenwert darstellen,
- echte Verantwortung durch oberflächliche Punkte ersetzen,
- private Entwicklung ohne Zustimmung öffentlich machen.

## 4. Quest und QuestRun

Eine Quest ist die Handlungseinladung selbst. Mehrere Menschen können dieselbe Quest unabhängig voneinander sehen, ausblenden, annehmen, durchführen, abschließen oder bestätigt bekommen.

Darum MUSS zwischen zwei Ebenen unterschieden werden:

| Ebene | Bedeutung | Beispiel |
|---|---|---|
| Quest | Die wiederverwendbare Handlungseinladung. | "Verifiziere eine reale Begegnung per QR." |
| QuestRun | Die konkrete Durchführung einer Quest durch einen Menschen. | "Anton hat diese Quest abgeschlossen." |

Eine Quest DARF NICHT global als `completed` gelten, nur weil eine Person sie abgeschlossen hat. `completed` oder `verified` beschreibt immer einen konkreten QuestRun, nicht die Quest als solche.

### 4.1 Quest-Status

Der Quest-Status beschreibt Veröffentlichung und Verwendbarkeit der Handlungseinladung.

| Status | Bedeutung |
|---|---|
| `draft` | Entwurf, zunächst privat. |
| `published` | Für einen gewählten Kontext sichtbar. |
| `paused` | Vorübergehend nicht aktiv vorgeschlagen. |
| `archived` | Nicht mehr aktiv, bleibt aber dokumentierbar oder forkbar. |

### 4.2 QuestRun-Status

Der QuestRun-Status beschreibt den Fortschritt eines Menschen zu einer Quest.

| Status | Bedeutung |
|---|---|
| `suggested` | Einer Person vorgeschlagen. |
| `dismissed` | Ausgeblendet oder abgelehnt. |
| `accepted` | Person möchte sie angehen. |
| `in-progress` | Durchführung hat begonnen. |
| `completed` | Abschluss wurde lokal markiert oder dokumentiert. |
| `verification-requested` | Bestätigung wurde angefragt, z.B. durch Host, Gruppe oder Dokumentation. |
| `verified` | Abschluss wurde bestätigt, z.B. per QR, Host, Gruppe oder Attestation. |
| `abandoned` | Begonnen, aber bewusst nicht weitergeführt. |

Nicht jede Umsetzung muss alle Status explizit speichern. Für Pax v0.1 reichen lokale Vorschläge und einfache Abschlusszustände, solange klar bleibt:

- Vorschlag, Annahme, Completion und Verifikation gehören zum QuestRun.
- Veröffentlichung, Pausierung und Archivierung gehören zur Quest.
- Aggregierte Aussagen wie "12 Menschen haben diese Quest abgeschlossen" sind abgeleitete Views aus sichtbaren QuestRuns oder Attestations.
- Eine Agenten-Empfehlung DARF einen lokalen QuestRun oder eine Suggestion erzeugen, aber nicht den globalen Quest-Status verändern.

## 5. Autorenschaft

Jede Quest MUSS einen Autor haben.

Zulässige Autoren in der Basisversion:

- eine menschliche Identität,
- eine System-/Agenten-Identität.

Ein Space, Ort, Projekt oder eine Initiative DARF als Kontext oder Herausgeber erscheinen. Die signierende oder erstellende Autorität bleibt aber eine erkennbare Identität, z.B. eine Person, ein Host-Agent oder eine System-DID.

Systemquests können hostlos wirken, sind aber nicht autorlos. Sie werden von einer System-/Agenten-Identität in die Welt gebracht.

## 6. Host und Begleitung

Eine Quest KANN einen Host oder eine begleitende Person haben, muss es aber nicht.

| Fall | Bedeutung |
|---|---|
| Host-Quest | Eine Person oder Gruppe begleitet Durchführung und Abschluss. |
| Systemquest | App oder Agent schlägt eine allgemeine Handlung vor. |
| Offene Quest | Die Quest kann ohne konkreten Host durchgeführt werden. |

Auch hostlose Quests brauchen klare Regeln, wie Abschluss und Sichtbarkeit funktionieren.

## 7. Sichtbarkeit und Veröffentlichung

Eine neu erstellte Quest SOLLTE zunächst privat sein.

Danach kann sie sichtbar gemacht werden für:

- nur mich,
- einzelne Kontakte,
- einen Space,
- öffentlich.

Dieses Muster folgt dem Real-Life-Stack-Prinzip, dass Items Sichtbarkeit und Sharing-Kontext haben können. Eine Quest DARF NICHT automatisch öffentlich werden, nur weil sie erstellt wurde.

## 8. Klassifizierung, Tags und Templates

Das Basisprotokoll definiert keine feste Quest-Typ-Taxonomie.

Für Interoperabilität ist nur entscheidend:

- Eine Quest ist als freiwillige Handlungseinladung modelliert.
- Ein QuestRun ist die konkrete Durchführung durch einen Menschen.
- Completion und Verifikation beziehen sich auf den QuestRun.
- Sichtbarkeit, Ort, Zeit und Kontext bleiben explizit.

Apps, Agenten und Playbooks DÜRFEN Quests klassifizieren. Diese Klassifizierung SOLLTE aber als optionale Metadaten modelliert werden, nicht als harte Protokollklasse.

| Ebene | Feld | Bedeutung | Beispiel |
|---|---|---|---|
| Operation | `data.operation` | Bezug zu einer sozialen Operation | `op.people.discover` |
| Intention | `data.intent` | sozialer Zweck oder Wirkung | `relationship`, `commons`, `learning` |
| Tags | `data.tags[]` | Suche, Filter, einfache Sortierung | `begegnung`, `pax-2026` |
| Template | `data.templateId` | wiederverwendbare Vorlage | `pax-meet-person` |

Häufige Quest-Templates können sein:

- persönlicher Schritt,
- Hilfe oder gegenseitige Unterstützung,
- gemeinsame Handlung,
- Event- oder Ortsbezug,
- Lernen oder Üben,
- Projekt- oder Commons-Aufgabe,
- Rolle oder Verantwortung,
- Dokumentation,
- Dank oder Wertschätzung,
- allgemeiner System- oder Agentenvorschlag.

Diese Begriffe DÜRFEN als Tags, Templates oder UI-Gruppen verwendet werden. Sie DÜRFEN NICHT vorausgesetzt werden, damit eine Quest protokollkonform ist.

Erlebnisorientierte Quests, Wanderungen, Klettertage oder Gruppenspiele bleiben im Basisprotokoll normale Handlungseinladungen mit Ort, Zeit, Kontext und Tags. Das Game-Repo kann daraus später Adventures oder andere Spielrahmen ableiten.

## 9. Minimale RLS-Item-Felder

Eine App DARF Quests als generische Real-Life-Stack-Items oder als lokale Suggestions abbilden. Persistenz ist für Pax v0.1 optional.

Wenn Quests persistiert oder zwischen Implementierungen ausgetauscht werden, SOLLTEN sie als RLS-Item-Views modelliert werden. Die folgenden Felder sind die minimale interoperable Sicht, keine vollständige neue RLS-Schema-Festlegung.

### 9.1 Quest

| Feld | Pflicht | Bedeutung |
|---|---|---|
| `type: "quest"` | ja | RLS-Item-Typ |
| `schema: "rlnp:quest"` | empfohlen | semantische Kennzeichnung |
| `schemaVersion: 1` | empfohlen | Version der RLNP-Quest-View |
| `createdBy` | ja | Identität, die die Quest erstellt hat |
| `data.title` | ja | kurze Handlungseinladung |
| `data.description` | empfohlen | Kontext, Sinn und mögliche Durchführung |
| `data.status` | ja | `draft`, `published`, `paused` oder `archived` |
| `data.optional: true` | ja | UI-Guard gegen Pflichtlogik |
| `data.operation` | empfohlen | soziale Operation, die unterstützt wird |
| `data.tags[]` | optional | Suche, Filter, einfache Klassifizierung |
| `data.intent` | optional | sozialer Zweck oder erwarteter Netzwerk-Effekt |
| `data.templateId` | optional | wiederverwendbare Vorlage |
| `data.visibility.mode` | empfohlen | gewünschte Sichtbarkeit: `private`, `contacts`, `space`, `public` |
| `data.location` | optional | Ort, Region oder grober Kartenkontext |
| `data.time` | optional | Termin, Zeitraum, Phase oder Rhythmus |

Empfohlene Relations:

| Predicate | Ziel | Bedeutung |
|---|---|---|
| `visibleIn` | Space | Quest ist in diesem Space sichtbar |
| `partOf` | Event/Project/Commons/Space | Quest gehört zu einem Kontext |
| `locatedAt` / `locatedNear` | Place/Region | Quest hat Ortsbezug |
| `forkedFrom` | Quest | Quest ist eine lokale Kopie oder Anpassung |

```json
{
  "id": "quest:pax:meet-similar-interest",
  "type": "quest",
  "createdAt": "2026-05-07T10:05:00Z",
  "createdBy": "did:key:z6Mk...agent-or-host",
  "schema": "rlnp:quest",
  "schemaVersion": 1,
  "data": {
    "title": "Finde eine Person mit ähnlichem Interesse",
    "description": "Schau dir Profile im Pax-Space an und lade eine Person zu einem echten Gespräch ein.",
    "status": "published",
    "optional": true,
    "operation": "op.people.discover",
    "intent": "relationship",
    "tags": ["begegnung", "pax-2026"],
    "visibility": {
      "mode": "space"
    },
    "time": {
      "phase": "during-event"
    },
    "location": {
      "label": "Pax Friedensfestival",
      "region": "pax-2026"
    }
  },
  "relations": [
    { "predicate": "visibleIn", "target": "space:pax-2026" }
  ]
}
```

### 9.2 QuestRun

Ein QuestRun verweist per Relations auf die Quest und den Menschen. `createdBy` beschreibt, wer das Item erstellt hat; die ausführende Person steht in der `actor`-Relation.

| Feld | Pflicht | Bedeutung |
|---|---|---|
| `type: "quest-run"` | ja | RLS-Item-Typ |
| `schema: "rlnp:quest-run"` | empfohlen | semantische Kennzeichnung |
| `schemaVersion: 1` | empfohlen | Version der RLNP-QuestRun-View |
| `createdBy` | ja | Identität, App oder Agent, die den Run angelegt hat |
| `data.status` | ja | QuestRun-Status |
| `data.visibility.mode` | empfohlen | Sichtbarkeit dieses persönlichen Runs |
| `data.completion.method` | ab `completed` | Completion-Methode |
| `data.completion.evidence` | optional | lokaler Nachweistyp oder Hinweis |
| `data.completion.completedAt` | optional | Zeitpunkt der lokalen Completion |
| `data.location` | optional | Ort oder Region der Durchführung |
| `data.time` | optional | Zeitpunkt, Zeitraum oder Phase der Durchführung |

Erforderliche Relations:

| Predicate | Ziel | Bedeutung |
|---|---|---|
| `runsQuest` | Quest | Run gehört zu dieser Quest |
| `actor` | Profile/Identity | Mensch, der den Run ausführt |

Optionale Kontext-Relations entsprechen der Quest: `partOf`, `locatedAt`, `locatedNear`.

```json
{
  "id": "quest-run:pax:meet-similar-interest:mira",
  "type": "quest-run",
  "createdAt": "2026-05-07T10:06:00Z",
  "createdBy": "did:key:z6Mk...mira",
  "schema": "rlnp:quest-run",
  "schemaVersion": 1,
  "data": {
    "status": "completed",
    "visibility": {
      "mode": "private"
    },
    "completion": {
      "method": "self-confirmation",
      "evidence": "none",
      "completedAt": "2026-05-07T10:20:00Z"
    }
  },
  "relations": [
    { "predicate": "runsQuest", "target": "item:quest:pax:meet-similar-interest" },
    { "predicate": "actor", "target": "global:did:key:z6Mk...mira" }
  ]
}
```

Diese Mindestfelder helfen Apps, Agenten und RLS-Connectoren dabei, Quest-Definition, persönliche Durchführung, Sichtbarkeit und Completion nicht zu vermischen.

## 10. Completion und Verifikation

Quest-Abschluss meint den Abschluss eines konkreten QuestRuns. Er kann je nach Quest unterschiedlich belegt werden.

| Completion-Methode | Bedeutung | Geeignet für |
|---|---|---|
| `qr-verification` | QR-Code wird vor Ort gescannt. | Teilnahme, Begegnung, Check-in |
| `host-confirmation` | Host bestätigt Abschluss. | Workshops, Einsätze, Lernquests |
| `mutual-confirmation` | Beteiligte bestätigen einander. | Hilfe, Gruppenquests, Zusammenarbeit |
| `attestation` | Eine Person oder ein System stellt eine signierte Aussage aus. | Badge, Beitrag, Rolle, Dank |
| `documentation-plus-confirmation` | Foto/Video/Text lädt andere zur Bestätigung ein. | sichtbare Ergebnisse, Projekte, Orte |
| `system-event` | App erkennt ein Ereignis. | "5 Menschen verifiziert", "Event erstellt" |
| `self-confirmation` | Person bestätigt lokal für sich selbst. | private Reflexion, persönliche Schritte |

**Normen:**

- Foto- oder Videodokumentation ist zunächst eine Einladung an andere, den Abschluss zu bestätigen. Sie ist nicht automatisch ein öffentlicher Beweis.
- Selbstbestätigung KANN einen QuestRun auf `completed` setzen.
- Selbstbestätigung erzeugt keine portable Attestation und kein öffentliches Badge.
- Öffentliche oder portable Anerkennung SOLLTE über Attestations laufen.
- Completion-Daten gehören zum QuestRun und MÜSSEN Sichtbarkeit und Zustimmung respektieren.

## 11. Badges als Attestations

Ein Badge ist eine visuell dargestellte WoT-Attestation.

Die visuelle Darstellung folgt der RLS Display Extension in [real-life-org/wot-spec](https://github.com/real-life-org/wot-spec/blob/main/04-rls-extensions/R01-badges.md), z.B. über `display.emoji`, `display.color` und `display.shape`.

Ein Badge kann ausdrücken:

- hat teilgenommen,
- hat eine Quest erfüllt,
- hat eine Veranstaltung organisiert,
- hat eine Rolle übernommen,
- hat einen Beitrag geleistet,
- hat Dank oder Wertschätzung erhalten,
- hat eine Fähigkeit in einem Kontext gezeigt.

Ein portables Badge MUSS eine WoT-Attestation sein. Eine reine UI-Darstellung ohne signierte Attestation ist kein portables Badge.

Ein Badge entsteht durch Bestätigung:

- durch eine menschliche Identität,
- durch eine Agenten-Identität,
- durch eine System-Identität.

Wenn ein Badge automatisch oder agentisch vergeben wird, MUSS klar sein:

- welche DID signiert,
- welche Regel ausgelöst wurde (`ruleId`, optional `ruleVersion`),
- welcher Trigger verwendet wurde,
- ob das Badge öffentlich, privat oder nur lokal ist.

Ohne erkennbare Signatur ist ein Badge nur ein lokaler UI-Status und keine portable Anerkennung.

## 12. Orts- und Zeitbezug

Eine Quest und ein QuestRun KÖNNEN jeweils eigenen Orts-, Zeit- oder Kontextbezug haben.

Kontext beschreibt, wozu die Handlungseinladung oder Durchführung gehört:

- Veranstaltung,
- Space,
- Projekt,
- Commons,
- Ort.

Wenn der Kontext als Item existiert, SOLLTE er per Relation modelliert werden. Einfache Orts- oder Zeitangaben DÜRFEN im Item stehen, wenn kein eigenes Kontext-Item existiert.

Zeitbezug kann bedeuten:

- konkreter Termin,
- Zeitraum,
- wiederkehrender Rhythmus,
- Bezug zu einer Veranstaltung oder einem Projektabschnitt.

Ort, Zeit und Kontext steuern Auffindbarkeit, Karte und Kalender. Sie sind keine Sichtbarkeitsstufen.

Wenn eine Quest oder ein QuestRun relevante Ortsdaten hat, KANN das jeweilige Item auf der Karte erscheinen. Wenn es relevante Zeitdaten hat, KANN es im Kalender erscheinen. Die Karten- und Kalenderlogik bleibt eine Real-Life-Stack- oder App-Projektion. Spielbrett-Metaphern und erweiterte Kartenmechaniken gehören in [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game).

Exakte Standortdaten DÜRFEN NICHT Voraussetzung für Teilnahme sein.

## 13. Kopieren und Forken

Quests SOLLTEN kopierbar oder forkbar sein.

Das ist besonders wichtig, wenn eine Quest:

- an einem Ort funktioniert hat,
- zu einer anderen Zeit wiederholt werden soll,
- in einer anderen Region angepasst werden soll,
- Teil einer wachsenden Quest-Bibliothek ist.

Ein Fork SOLLTE den Ursprung referenzieren, aber lokal angepasst werden dürfen.

Beispiel:

```text
Wildkräuterwanderung Alsterpark
  -> Fork: Wildkräuterwanderung Englischer Garten
  -> Fork: Wildkräuterwanderung Leipzig Auwald
```

## 14. Agentenverhalten

KI-Agenten können Quest-Flows unterstützen.

Sie können:

- Quest-Erstellung unterstützen,
- Quest-Texte formulieren,
- passende Quests vorschlagen,
- Hosts unterstützen,
- Dokumentation zusammenfassen,
- Verbindungen zwischen Menschen, Orten, Ressourcen und Projekten erkennen,
- Reflexionsgespräche führen.

Sie dürfen nicht:

- Quests im Namen eines Menschen ohne Zustimmung veröffentlichen,
- Completion oder Badge ohne nachvollziehbare Grundlage behaupten,
- Menschen bewerten oder ranken,
- Druck erzeugen,
- Sichtbarkeit ausweiten, ohne dass der Mensch zustimmt.

## 15. Kinder und Jugendliche

Die erste Fassung dieser Quest-Mechanik ist für erwachsene Nutzungskontexte gedacht.

Anwendungsfälle mit Kindern und Jugendlichen brauchen ein eigenes Schutz- und Begleitmodell. Dazu gehören mindestens:

- Zustimmung und Einblick durch Erziehungsberechtigte,
- Schutz vor gefährlichen Challenges,
- altersgerechte Sichtbarkeit,
- sichere Kommunikation,
- besondere Regeln für Foto/Video-Dokumentation,
- klare Verantwortung von Hosts und Institutionen.

## 16. Verhältnis zum Game-Repo

Dieses Dokument definiert nur die interoperable Quest-Basis.

Das Repo [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game) kann darauf aufbauen und erforschen:

- Storylines,
- Adventures,
- Journeys,
- Campaigns,
- XP,
- Level,
- Skill-Trees,
- Avatar-Items,
- Inventory,
- Game Modes,
- Game Master Tools,
- AI Game Master,
- World State,
- Balancing,
- UI/UX,
- konkrete Spielinhalte.

Diese Mechaniken DÜRFEN die Quest-Basis nicht verletzen: Freiwilligkeit, Sichtbarkeit, Zustimmung, kein Ranking von Menschen und keine soziale Kontrolle bleiben verbindlich.

## 17. Offene Fragen

- Welche Quest-Templates werden für Pax v0.1 als UI-Karten gebraucht?
- Welche System-/Agenten-DIDs dürfen automatische oder agentische Badge-Attestations signieren?
- Welche Badge-Regeln werden im ersten Pax-/RLN-Kontext gebraucht?
