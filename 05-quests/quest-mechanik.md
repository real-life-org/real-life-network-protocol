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
- Quest-Teilnahmen dokumentieren,
- Abschlüsse von Quest-Teilnahmen bestätigen,
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

## 4. Quest und Quest-Teilnahme

Eine Quest ist die Handlungseinladung selbst. Mehrere Menschen oder Gruppen können dieselbe Quest unabhängig voneinander sehen, ausblenden, annehmen, durchführen, abschließen oder bestätigt bekommen.

Darum MUSS zwischen zwei Ebenen unterschieden werden:

| Ebene | Bedeutung | Beispiel |
|---|---|---|
| Quest | Die wiederverwendbare Handlungseinladung. | "Verifiziere eine reale Begegnung per QR." |
| Quest-Teilnahme | Der persönliche oder gruppenbezogene Fortschritt zu einer Quest. | "Anton hat diese Quest abgeschlossen." |

Eine Quest DARF NICHT global als `completed` gelten, nur weil eine Person sie abgeschlossen hat. `completed` oder `verified` beschreibt immer eine konkrete Quest-Teilnahme, nicht die Quest als solche.

### 4.1 Quest-Status

Der Quest-Status beschreibt Veröffentlichung und Verwendbarkeit der Handlungseinladung.

| Status | Bedeutung |
|---|---|
| `draft` | Entwurf, zunächst privat. |
| `published` | Für einen gewählten Kontext sichtbar. |
| `paused` | Vorübergehend nicht aktiv vorgeschlagen. |
| `archived` | Nicht mehr aktiv, bleibt aber dokumentierbar oder forkbar. |

### 4.2 Teilnahme-Status

Der Teilnahme-Status beschreibt die Beziehung einer Person oder Gruppe zu einer Quest.

| Status | Bedeutung |
|---|---|
| `suggested` | Einer Person oder Gruppe vorgeschlagen. |
| `dismissed` | Ausgeblendet oder abgelehnt. |
| `accepted` | Person oder Gruppe möchte sie angehen. |
| `in-progress` | Durchführung hat begonnen. |
| `completed` | Abschluss wurde lokal markiert oder dokumentiert. |
| `verification-requested` | Bestätigung wurde angefragt, z.B. durch Host, Gruppe oder Dokumentation. |
| `verified` | Abschluss wurde bestätigt, z.B. per QR, Host, Gruppe oder Attestation. |
| `abandoned` | Begonnen, aber bewusst nicht weitergeführt. |

Nicht jede Umsetzung muss alle Status explizit speichern. Für Pax v0.1 reichen lokale Vorschläge und einfache Abschlusszustände, solange klar bleibt:

- Vorschlag, Annahme, Completion und Verifikation gehören zur Quest-Teilnahme.
- Veröffentlichung, Pausierung und Archivierung gehören zur Quest.
- Aggregierte Aussagen wie "12 Menschen haben diese Quest abgeschlossen" sind abgeleitete Views aus sichtbaren Teilnahmen oder Attestations.
- Eine Agenten-Empfehlung DARF eine lokale Quest-Teilnahme oder Suggestion erzeugen, aber nicht den globalen Quest-Status verändern.

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
| Gruppenquest | Eine Gruppe trägt die Durchführung gemeinsam. |
| Projektquest | Die Quest gehört zu einem Projekt oder Commons. |

Auch hostlose Quests brauchen klare Regeln, wie Abschluss und Sichtbarkeit funktionieren.

## 7. Sichtbarkeit und Veröffentlichung

Eine neu erstellte Quest SOLLTE zunächst privat sein.

Danach kann sie sichtbar gemacht werden für:

- nur mich,
- einzelne Kontakte,
- einen Space,
- öffentlich.

Dieses Muster folgt dem Real-Life-Stack-Prinzip, dass Items Sichtbarkeit und Sharing-Kontext haben können. Eine Quest DARF NICHT automatisch öffentlich werden, nur weil sie erstellt wurde.

## 8. Quest-Typen

Die folgenden Quest-Typen sind im Basisprotokoll erlaubt. Sie sind keine abschließende Taxonomie.

| Typ | Beschreibung | Beispiel |
|---|---|---|
| `personal` | Eine Person tut etwas für sich. | "Schreibe auf, was du wirklich lernen willst." |
| `help` | Eine Person hilft einer anderen. | "Hilf Mira beim Aufbau der Küche." |
| `group` | Mehrere Menschen tun etwas gemeinsam. | "Kocht zusammen für den Kreis." |
| `event` | Handlung ist an eine Veranstaltung gebunden. | "Hilf am Samstag beim Aufbau." |
| `learning` | Fähigkeit wird geübt oder geteilt. | "Lerne die Grundlagen des Lötens." |
| `project` | Aufgabe in einem Projekt. | "Erstelle den ersten Beetplan." |
| `role` | Verantwortung oder Rolle wird übernommen. | "Übernimm für ein Treffen die Moderation." |
| `stewardship` | Pflege von Ort, Ressource oder Commons. | "Bring das Zelt trocken zurück." |
| `documentation` | Sichtbarmachung dessen, was passiert ist. | "Schreibe einen kurzen Erfahrungsbericht." |
| `gratitude` | Dank oder Wertschätzung wird ausgedrückt. | "Danke einer Person per Attestation." |
| `system` | Allgemeine Handlungseinladung durch App oder Agent. | "Verifiziere eine reale Begegnung per QR." |

Erlebnisorientierte Quests, Wanderungen, Klettertage oder Gruppenspiele können im Basisprotokoll als `event`, `group` oder `personal` beschrieben und mit Tags versehen werden. Das Game-Repo kann daraus später Adventures oder andere Spielrahmen ableiten.

## 9. Minimale Quest-Item-View

Eine App DARF Quests als generische Real-Life-Stack-Items oder als lokale Suggestions abbilden. Persistenz ist für Pax v0.1 optional.

```json
{
  "type": "quest",
  "schema": "rlnp:quest",
  "schemaVersion": 1,
  "visibility": {
    "mode": "private"
  },
  "createdBy": "did:example:alice",
  "status": "published",
  "data": {
    "title": "Finde eine Person mit ähnlichem Interesse",
    "description": "Schau dir Profile im Pax-Space an und lade eine Person zu einem echten Gespräch ein.",
    "operation": "op.people.discover",
    "questType": "personal",
    "phase": "during-event",
    "optional": true,
    "tags": ["begegnung", "pax-2026"],
    "context": {
      "spaceId": "pax-2026"
    }
  }
}
```

Eine persönliche Teilnahme oder lokale Suggestion kann darauf verweisen:

```json
{
  "type": "quest-participation",
  "schema": "rlnp:quest-participation",
  "schemaVersion": 1,
  "questId": "quest:pax-find-similar-interest",
  "actor": "did:example:bob",
  "status": "suggested",
  "visibility": {
    "mode": "private"
  },
  "completion": {
    "method": "self-confirmation",
    "evidence": "none"
  }
}
```

Diese Views sind keine abschließende RLS-Schema-Festlegung. Sie beschreiben die Mindestinformationen, die eine App braucht, um Quest-Definition, persönliche Suggestion, Sichtbarkeit und Completion nicht zu vermischen.

## 10. Completion und Verifikation

Quest-Abschluss meint den Abschluss einer konkreten Quest-Teilnahme. Er kann je nach Quest unterschiedlich belegt werden.

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
- Selbstbestätigung ist für private oder niedrigschwellige Quests möglich, aber als Grundlage für öffentliche Badges noch offen.
- Öffentliche oder portable Anerkennung SOLLTE über Attestations laufen.
- Completion-Daten gehören zur Quest-Teilnahme und MÜSSEN Sichtbarkeit und Zustimmung respektieren.

## 11. Badges und Attestations

Im Basisprotokoll sind Badges gleichbedeutend mit oder abgeleitet aus Attestations.

Ein Badge kann ausdrücken:

- hat teilgenommen,
- hat eine Quest erfüllt,
- hat eine Veranstaltung organisiert,
- hat eine Rolle übernommen,
- hat einen Beitrag geleistet,
- hat Dank oder Wertschätzung erhalten,
- hat eine Fähigkeit in einem Kontext gezeigt.

Ein portables Badge MUSS als WoT-Attestation oder aus einer WoT-Attestation ableitbar sein.

Wenn ein Badge automatisch vom System vergeben wird, MUSS klar sein:

- welche System-/Agenten-Identität signiert,
- welche Regel ausgelöst wurde,
- welche Daten dafür verwendet wurden,
- ob das Badge öffentlich, privat oder nur lokal ist.

Ohne erkennbare Signatur ist ein Badge nur ein lokaler UI-Status und keine portable Anerkennung.

## 12. Orts- und Zeitbezug

Eine Quest KANN Orts- oder Zeitbezug haben.

Ortsbezug kann bedeuten:

- konkreter Ort,
- grobe Region,
- Veranstaltung,
- Space,
- Projektort,
- Commons,
- Route oder Treffpunkt.

Zeitbezug kann bedeuten:

- konkreter Termin,
- Zeitraum,
- wiederkehrender Rhythmus,
- Bezug zu einer Veranstaltung oder einem Projektabschnitt.

Wenn eine Quest relevante Ortsdaten hat, KANN sie als Karten-Item erscheinen. Die Kartenlogik bleibt eine Real-Life-Stack- oder App-Projektion. Spielbrett-Metaphern und erweiterte Kartenmechaniken gehören in [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game).

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

- Wird `self-confirmation` für öffentliche Badges grundsätzlich ausgeschlossen oder nur als schwächeres Signal markiert?
- Welche System-/Agenten-DID darf automatische Badges signieren?
- Wie werden automatische Badge-Regeln auditierbar?
- Wird `badge` ein eigener Item-Typ, eine Attestation-View oder beides?
- Welche minimalen Quest-Felder braucht RLS v0.1?
- Wie werden Quest-Forks im Datenmodell referenziert?
