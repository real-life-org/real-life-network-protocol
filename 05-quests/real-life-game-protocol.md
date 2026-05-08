# Real Life Game Protocol

**Status:** Entwurf v0.1
**Datum:** 2026-05-08
**Scope:** Grundmechanik des Real Life Game als Ausbaustufe auf WoT, Real Life Stack und Real Life Network Protocol.

---

## 1. Zweck

Das Real Life Game ist eine spielerische Ausbaustufe des Real Life Networks.

Es begreift die reale Welt und das eigene Leben als kooperatives Spielfeld: Menschen gestalten ihr Leben, ihre Beziehungen, ihre Orte, ihre Projekte und ihre Umgebung aktiv und mit Freude. Veränderung und Verantwortung sollen nicht schwer, moralisch oder bürokratisch wirken, sondern wie eine Einladung zum Spielen.

Das Spiel setzt auf:

- **WoT** für Identität, QR-Verifikation, Kontakte, Attestations und Empfängerprinzip,
- **Real Life Stack** für App-Shell, Spaces, generische Items, Karte, Kalender, Feed, Profile und Module,
- **Real Life Network Protocol** für soziale Operationen, Freiwilligkeit, Sichtbarkeit, Commons, Playbooks und Agentenleitplanken.

## 2. Abgrenzung

Dieses Dokument beschreibt die Basismechanik, die in das Real Life Network Protocol gehört.

Sprachlich gilt:

```text
Quest = kleinste interoperable reale Einladung im Netzwerkprotokoll.
Game  = spielerischer Rahmen, der Quests, Orte, Ressourcen, Rollen und Geschichten verbindet.
```

Eine Quest kann ohne Game existieren. Das Game benutzt Quests als kleinste reale Handlungseinheit.

Es beschreibt NICHT abschließend:

- XP-Kurven,
- Levelsysteme,
- Skill-Trees,
- Avatar-Items,
- Drop-Raten,
- Balancing,
- konkrete Story-Kampagnen,
- vollständige Kinder-/Jugendlichen-Mechaniken.

Diese Elemente gehören in das eigenständige Repo [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game) oder in spätere Game-Design-Konzepte, weil sie starke Anreizwirkungen haben und sorgfältig gestaltet werden müssen.

## 3. Spielprinzip

Das Real Life Game folgt dem WinWinWin-Prinzip:

- **Win für dich:** Du entdeckst und entfaltest deine Potenziale.
- **Win für uns:** Beziehungen, Gemeinschaften und Projekte werden lebendiger.
- **Win für die Welt:** Orte, Ressourcen, Commons und Ökosysteme werden gepflegt und gestärkt.

Manifestation bedeutet in diesem Kontext: Menschen erschaffen proaktiv aus sich heraus. Eine Idee, ein Bedürfnis, ein Talent oder eine Vision wird zu einer realen Handlung, einem Erlebnis, einem Ort, einer Beziehung, einem Projekt oder einem Commons.

Das Spiel kann man nicht im klassischen Sinn gewinnen. Der Gewinn liegt in wachsender Lebendigkeit, besseren Beziehungen, realen Erfahrungen, sichtbaren Beiträgen, gemeinsamen Strukturen und höherer Lebensqualität.

## 4. Nicht-Ziele

Das Real Life Game DARF NICHT:

- Menschen global ranken,
- sozialen Druck erzeugen,
- Konkurrenz als Hauptmechanik verwenden,
- Profilfortschritt als Menschenwert darstellen,
- echte Verantwortung durch oberflächliche Punkte ersetzen,
- gefährliche, illegale oder altersunangemessene Challenges fördern,
- private Entwicklung ohne Zustimmung öffentlich machen.

## 5. Quest-Grundmodell

Eine Quest ist eine freiwillige Einladung zu einer realen Handlung.

Im Real Life Game kann grundsätzlich alles zur Quest werden:

- eine kleine persönliche Handlung,
- gegenseitige Hilfe,
- Lernen oder Üben,
- ein gemeinsamer Einsatz an Ort und Zeit,
- ein Abenteuer,
- ein Projektauftrag,
- die Übernahme einer Rolle,
- der Aufbau oder die Pflege eines Ortes,
- die Verwaltung einer Ressource,
- ein Commons-Beitrag,
- eine Dokumentation,
- ein Dankeschön.

Eine Quest ist immer spielerische Einladung, nicht Pflicht.

## 6. Quest-Autorenschaft

Jede Quest MUSS einen Autor haben.

Zulässige Autoren in der Basisversion:

- eine menschliche Identität,
- eine System-/Agenten-Identität.

Ein Space, Ort, Projekt oder eine Initiative DARF als Kontext oder Herausgeber erscheinen. Die signierende oder erstellende Autorität bleibt aber eine erkennbare Identität, z.B. eine Person, ein Host-Agent oder eine System-DID.

Systemquests können hostlos wirken, sind aber nicht autorlos. Sie werden von einer System-/Agenten-Identität in die Welt gebracht.

## 7. Host und Questmaster

Eine Quest KANN einen Host oder Questmaster haben, muss es aber nicht.

| Fall | Bedeutung |
|---|---|
| Host-Quest | Eine Person oder Gruppe begleitet Durchführung und Abschluss. |
| Systemquest | Die App oder ein Agent schlägt eine allgemeine Handlung vor. |
| Offene Quest | Die Quest kann ohne konkreten Host durchgeführt werden. |
| Gruppenquest | Eine Gruppe trägt die Durchführung gemeinsam. |
| Projektquest | Die Quest gehört zu einem Projekt oder Commons. |

Auch hostlose Quests brauchen klare Regeln, wie Abschluss und Sichtbarkeit funktionieren.

## 8. Sichtbarkeit und Veröffentlichung

Eine neu erstellte Quest SOLLTE zunächst privat sein.

Danach kann sie sichtbar gemacht werden für:

- nur mich,
- einzelne Kontakte,
- einen Space,
- eine Gruppe oder ein Projekt,
- eine Region,
- öffentlich.

Dieses Muster folgt dem Real-Life-Stack-Prinzip, dass Items Sichtbarkeit und Sharing-Kontext haben können. Eine Quest DARF NICHT automatisch öffentlich werden, nur weil sie erstellt wurde.

## 9. Quest-Typen

Die folgenden Quest-Typen sind im Basisprotokoll erlaubt. Sie sind keine abschließende Taxonomie.

| Typ | Beschreibung | Beispiel |
|---|---|---|
| `personal` | Eine Person tut etwas für sich. | "Schreibe auf, was du wirklich lernen willst." |
| `help` | Eine Person hilft einer anderen. | "Hilf Mira beim Aufbau der Küche." |
| `group` | Mehrere Menschen tun etwas gemeinsam. | "Kocht zusammen für den Kreis." |
| `mission` | Gemeinsamer Einsatz an Ort und Zeit. | "Baut am Samstag die Werkbank auf." |
| `adventure` | Erlebnisorientierte Quest. | "Geht gemeinsam klettern, wandern oder radfahren." |
| `learning` | Fähigkeit wird geübt oder geteilt. | "Lerne die Grundlagen des Lötens." |
| `project` | Aufgabe in einem Projekt. | "Erstelle den ersten Beetplan." |
| `role` | Verantwortung oder Rolle wird übernommen. | "Übernimm für ein Treffen die Moderation." |
| `stewardship` | Pflege von Ort, Ressource oder Commons. | "Bring das Zelt trocken zurück." |
| `documentation` | Sichtbarmachung dessen, was passiert ist. | "Schreibe einen kurzen Erfahrungsbericht." |
| `gratitude` | Dank oder Wertschätzung wird ausgedrückt. | "Danke einer Person per Attestation." |
| `system` | Allgemeine Einladung durch App oder Agent. | "Verifiziere eine reale Begegnung per QR." |

## 10. Completion und Verifikation

Quest-Abschluss kann je nach Quest unterschiedlich belegt werden.

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
- Completion-Daten MÜSSEN Sichtbarkeit und Zustimmung respektieren.

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

## 12. Karte als Spielbrett

Alles mit Geobezug KANN auf der Karte erscheinen:

- Quests,
- Abenteuer,
- Veranstaltungen,
- Orte,
- Ressourcen,
- Commons,
- Projekte,
- Initiativen,
- sichtbare Profile oder ungefähre Regionen.

Die Karte wird dadurch zum Spielbrett der realen Welt. Ein Item erscheint auf der Karte nicht wegen seines Typs, sondern weil es relevante Ortsdaten oder einen Ortsbezug hat.

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

## 14. Storylines

Das Basisprotokoll ist story-neutral.

Ein Real Life Game kann verschiedene Storylines haben:

- Heldenreise,
- lokale Resilienz,
- Commons-Aufbau,
- Macher-/Handwerksreise,
- Natur- und Abenteuerpfade,
- Heilung und Beziehung,
- Festival-Kampagnen,
- regionale Missionen.

Storylines DÜRFEN Quests rahmen, aber sie DÜRFEN NICHT zur ideologischen Verpflichtung werden.

## 15. KI-Agenten

KI-Agenten sind optional.

Sie können:

- Quest-Erstellung unterstützen,
- Quest-Texte formulieren,
- passende Quests vorschlagen,
- Spielleiter oder Hosts unterstützen,
- Dokumentation zusammenfassen,
- Verbindungen zwischen Menschen, Orten, Ressourcen und Projekten erkennen,
- Reflexionsgespräche führen.

Sie dürfen nicht:

- Quests im Namen eines Menschen ohne Zustimmung veröffentlichen,
- Completion oder Badge ohne nachvollziehbare Grundlage behaupten,
- Menschen bewerten oder ranken,
- Druck erzeugen,
- Sichtbarkeit ausweiten, ohne dass der Mensch zustimmt.

## 16. Kinder und Jugendliche

Die erste Fassung des Real Life Game ist für Erwachsene gedacht.

Anwendungsfälle mit Kindern und Jugendlichen brauchen ein eigenes Schutz- und Begleitmodell. Dazu gehören mindestens:

- Zustimmung und Einblick durch Erziehungsberechtigte,
- Schutz vor gefährlichen Challenges,
- altersgerechte Sichtbarkeit,
- sichere Kommunikation,
- besondere Regeln für Foto/Video-Dokumentation,
- klare Verantwortung von Hosts und Institutionen.

## 17. Verhältnis zum Game-Repo

Dieses Dokument definiert nur die interoperable Basis.

Das Repo [real-life-org/real-life-game](https://github.com/real-life-org/real-life-game) kann darauf aufbauen und erforschen:

- XP,
- Level,
- Skill-Trees,
- Avatar-Items,
- Quest-Reihen,
- Adventure-Design,
- Kampagnen,
- Storywelten,
- Balancing,
- UI/UX,
- konkrete Spielinhalte.

Diese Mechaniken DÜRFEN das Basisprotokoll nicht verletzen: Freiwilligkeit, Sichtbarkeit, Zustimmung, kein Ranking von Menschen und keine soziale Kontrolle bleiben verbindlich.

## 18. Offene Fragen

- Wird `self-confirmation` für öffentliche Badges grundsätzlich ausgeschlossen oder nur als schwächeres Signal markiert?
- Welche System-/Agenten-DID darf automatische Badges signieren?
- Wie werden automatische Badge-Regeln auditierbar?
- Wird `badge` ein eigener Item-Typ, eine Attestation-View oder beides?
- Welche minimalen Quest-Felder braucht RLS v0.1?
- Wie werden Quest-Forks im Datenmodell referenziert?
- Welche Storyline ist der erste konkrete Game-Slice?
