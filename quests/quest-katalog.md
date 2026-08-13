# Quest-Katalog v0.1

**Status:** Entwurf v0.1
**Datum:** 2026-05-08
**Scope:** Erste freiwillige Handlungseinladungen für das Festival-/Festival-Kontexte, lokale Kreise und App-v0.1-Nutzerführung.

---

## 1. Zweck

Dieser Katalog beschreibt erste Quests als freiwillige Handlungseinladungen. Sie sollen Menschen helfen:

- die App und ihre eigene Identität zu verstehen,
- reale Begegnungen wahrscheinlicher zu machen,
- Angebote, Bedürfnisse und Visionen sichtbar zu machen,
- Beziehungen per QR-Verifikation festzuhalten,
- nach einem Festival in lokalen Kreisen, Projekten und Commons weiterzugehen.

Quests sind keine Pflichten, keine Leistungsmessung und kein Ranking-System.

## 2. Quest-Regeln

Für jede Quest in diesem Katalog gelten die normativen Leitplanken aus [quest-mechanik.md](quest-mechanik.md), Abschnitt 3. Sie werden hier bewusst nicht wiederholt: Doppelt gepflegte Normen driften auseinander.

Eine Quest DARF:

- als App-Karte,
- als Agentenvorschlag,
- als Crew-Einladung,
- als Checklistenpunkt,
- als Follow-up nach einem Event

erscheinen.

## 3. Operations-Namespace

Die Operationen `op.app.open`, `op.identity.create`, `op.space.join`, `op.profile.create`, `op.share`, `op.people.discover`, `op.verification.create`, `op.offer.need.publish`, `op.quest.suggest` und `op.followup.create` gehören zum P0-Mapping.

Weitere Operationen in diesem Katalog, z.B. `op.confirmation.create`, `op.event.create`, `op.project.start` oder `op.commons.create`, sind vorläufige P1/P2-Operationsnamen. Sie beschreiben den sozialen Zweck, müssen aber vor einer strikten Implementierung noch in [../real-life-network-protocol.md](../real-life-network-protocol.md) (Abschnitt 8) und [../data-model/operations-mapping.md](../data-model/operations-mapping.md) formalisiert werden.

## 4. Minimale Quest- und QuestRun-View

Eine App DARF Quests als generische Real-Life-Stack-Items oder als lokale Suggestions abbilden. Persistenz ist für Rollout v0.1 optional.

```json
{
  "id": "quest:fest:meet-similar-interest",
  "type": "quest",
  "createdAt": "2026-05-07T10:05:00Z",
  "createdBy": "did:example:agent-or-host",
  "schema": "rlnp:quest",
  "schemaVersion": 1,
  "data": {
    "title": "Finde eine Person mit ähnlichem Interesse",
    "description": "Schau dir Profile im Festival-Space an und lade eine Person zu einem echten Gespräch ein.",
    "status": "published",
    "optional": true,
    "operation": "op.people.discover",
    "tags": ["begegnung", "festival"],
    "evidencePolicy": {
      "required": false,
      "acceptedTypes": ["self-claim", "text"]
    },
    "confirmationPolicy": {
      "allowedConfirmers": [
        { "role": "peer", "minCount": 1 },
        { "role": "host" }
      ],
      "acceptedTrustLevels": ["verifiable"]
    },
    "completionConfirmationTemplate": {
      "claim": "{actor} hat eine echte Begegnung im Festival-Space geführt.",
      "display": {
        "label": "Echte Begegnung",
        "color": "#4F7CFF",
        "shape": "circle"
      }
    },
    "safetyRequirements": [
      {
        "type": "consent",
        "required": true,
        "label": "Teile Gesprächsinhalte nur mit Zustimmung der beteiligten Person."
      }
    ],
    "time": {
      "phase": "during-event"
    }
  },
  "relations": [
    { "predicate": "visibleIn", "target": "space:festival" }
  ]
}
```

Ein QuestRun verweist per Relations auf diese Quest:

```json
{
  "id": "quest-run:fest:meet-similar-interest:alice",
  "type": "quest-run",
  "createdAt": "2026-05-07T10:06:00Z",
  "createdBy": "did:example:alice",
  "schema": "rlnp:quest-run",
  "schemaVersion": 1,
  "data": {
    "status": "completed",
    "completion": {
      "claimedAt": "2026-05-07T10:20:00Z",
      "claim": "Ich habe ein echtes Gespräch im Festival-Space geführt.",
      "evidenceRefs": []
    }
  },
  "relations": [
    { "predicate": "runsQuest", "target": "item:quest:fest:meet-similar-interest" },
    { "predicate": "actor", "target": "global:did:example:alice" }
  ]
}
```

**Norm:** Eine Fertig-Meldung gilt für sich und braucht keine Bestätigung. Sie ist aber kein globaler Quest-Status, kein Vertrauensbeweis und kein sozialer Score, und sie ist für Dritte nicht überprüfbar. Soll eine Aussage über den QuestRun portabel und unabhängig prüfbar sein, braucht sie eine signierte Attestation; dasselbe gilt für portable Badges.

## 5. Katalog

### 5.1 Einstieg und Selbstbesitz

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.fest.001` | Öffne die App oder Web-App. | `op.app.open` | Stand-QR, Link, Crew-Einladung | App ist geöffnet | Kein Installationszwang |
| `q.fest.002` | Erzeuge deine eigene lokale ID. | `op.identity.create` | keine lokale DID vorhanden | DID/Schlüssel lokal erzeugt | Kein zentrales Konto suggerieren |
| `q.fest.003` | Lies kurz, was deine ID bedeutet. | `op.identity.create` | neue DID erzeugt | Hinweis wurde gesehen | Kurz, ehrlich, nicht technisch überladen |
| `q.fest.004` | Tritt freiwillig dem Festival-Space bei. | `op.space.join` | gültiger Festival-Invite | Space-Mitgliedschaft aktiv | Ablehnen bleibt normal |
| `q.fest.005` | Entscheide, ob du im Festival-Space sichtbar sein möchtest. | `op.share` | Space-Beitritt aktiv | Sichtbarkeitszustand gesetzt | Sichtbarkeit muss änderbar bleiben |
| `q.fest.006` | Bitte die Crew um eine analoge Einführung, wenn etwas unklar ist. | `op.app.open` | Unsicherheit, technischer Fehler | Frage gestellt oder Hilfe erhalten | Kein Druck zur Selbstbedienung |

### 5.2 Profil, Angebote und Bedürfnisse

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.fest.007` | Ergänze deinen Rufnamen. | `op.profile.create` | Profil leer oder minimal | Name/Rufname gespeichert | Pseudonym ist erlaubt |
| `q.fest.008` | Schreibe einen Satz: Was bewegt dich gerade? | `op.profile.create` | Profil vorhanden | kurzer Profiltext gespeichert | Keine intime Selbstoffenbarung erzwingen |
| `q.fest.009` | Trage ein Angebot als Tag ein. | `op.offer.need.publish` | Profil vorhanden | `offers[]` enthält mindestens einen Tag | Tags bleiben einfache Profilfelder |
| `q.fest.010` | Trage ein Bedürfnis oder eine Suche als Tag ein. | `op.offer.need.publish` | Profil vorhanden | `needs[]` enthält mindestens einen Tag | Bedürfnis darf offen und unfertig sein |
| `q.fest.011` | Ergänze eine Vision oder ein Thema, das dich ruft. | `op.profile.create` | Profil vorhanden | Vision/Interesse sichtbar oder privat gespeichert | Kein Missionierungsdruck |
| `q.fest.012` | Wähle eine grobe Region für lokale Auffindbarkeit. | `op.share` | Person will lokal auffindbar sein | Region oder Festival-Ort gesetzt | Wie genau ein Ort gezeigt wird, ist keine Frage der Sichtbarkeit |
| `q.fest.013` | Prüfe, wen dein Profil erreicht. | `op.share` | Profil enthält Daten | bewusst bestätigt, wo es liegt | Keine stillen Veröffentlichungen |

### 5.3 Menschen entdecken und begegnen

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.fest.014` | Schau dir drei Profile im Festival-Space an. | `op.people.discover` | Space hat sichtbare Profile | Profile wurden geöffnet | Kein Ranking von Menschen |
| `q.fest.015` | Finde eine Person mit ähnlichem Interesse. | `op.people.discover` | passende Tags/Visionen sichtbar | Person gemerkt oder kontaktiert | Vorschlag bleibt Einladung |
| `q.fest.016` | Finde eine Person, deren Angebot zu deinem Bedürfnis passt. | `op.people.discover` | Offer-/Need-Tags vorhanden | mögliche Verbindung erkannt | Match nicht als Verpflichtung darstellen |
| `q.fest.017` | Lade jemanden zu einem echten Gespräch ein. | `op.people.discover` | passende Person gefunden | Einladung ausgesprochen oder gesendet | Nein muss leicht bleiben |
| `q.fest.018` | Geh zum Vernetzungszelt und sprich jemanden Neues an. | `op.people.discover` | Person ist vor Ort | Begegnung analog begonnen | Keine unangenehmen Mutproben |
| `q.fest.019` | Bitte die Crew um eine passende Vorstellung. | `op.people.discover` | Person sucht Anschluss | Crew/Agent schlägt Verbindung vor | Nur mit sichtbarem Kontext arbeiten |
| `q.fest.020` | Führe ein Gespräch über eure Visionen. | `op.people.discover` | Begegnung findet statt | Gespräch selbst bestätigt | Kein Gesprächsinhalt muss gespeichert werden |

### 5.4 QR-Verifikation und Beziehung

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.fest.021` | Verifiziert euch per QR, wenn ihr eure Begegnung festhalten wollt. | `op.verification.create` | reale Begegnung hat stattgefunden | Verification-Confirmation erstellt; portabel als signierte Attestation | Verifikation bestätigt Begegnung, nicht globale Vertrauenswürdigkeit |
| `q.fest.022` | Lass dir erklären, was QR-Verifikation bedeutet. | `op.verification.create` | erste Verifikation | Erklärung gelesen oder Crew gefragt | Keine Kryptographie-Vorlesung im Flow |
| `q.fest.023` | Bestätige eine eingehende Gegenverifikation. | `op.verification.create` | eingehende Verification-Confirmation | Gegenverifikation erstellt oder abgelehnt | Ablehnen bleibt möglich |
| `q.fest.024` | Ergänze optional Kontext zur Begegnung. | `op.verification.create` | Verifikation abgeschlossen | Ort/Event/Notiz lokal oder als Metadaten gesetzt | Kontext darf privat bleiben |
| `q.fest.025` | Sende eine konkrete Confirmation für einen beobachteten Beitrag. | `op.confirmation.create` | Person hat real etwas beigetragen | Confirmation erstellt; portabel als signierte Attestation | Nur konkret Beobachtetes bestätigen |
| `q.fest.026` | Entscheide, ob du eine erhaltene Confirmation anzeigen möchtest. | `op.confirmation.visibility.set` | Confirmation empfangen | Sichtbarkeit lokal gesetzt | Empfängerprinzip respektieren |

### 5.5 Ressourcen, Orte und Veranstaltungen

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.fest.027` | Frage nach einer Ressource, die du gerade brauchst. | `op.offer.need.publish` | konkretes Bedürfnis vorhanden | Need-Tag oder Nachricht erstellt | Bedürfnis nicht bewerten |
| `q.fest.028` | Biete etwas an, das du gerne teilst. | `op.offer.need.publish` | Person will beitragen | Offer-Tag erstellt | Kein Selbstvermarktungsdruck |
| `q.fest.029` | Dokumentiere einen Ort, der für Begegnung wichtig ist. | `op.place.create` | Ort existiert oder wird genutzt | Place-/Marker-Item oder Notiz erstellt | Eigentum, Pflege und Sichtbarkeit klären |
| `q.fest.030` | Trage ein Gemeinschaftsessen oder Treffen ein. | `op.event.create` | Event geplant oder spontan | Event-/Post-/Calendar-Item erstellt | Keine Teilnahmeüberwachung |
| `q.fest.031` | Lade Menschen zu einem Vollmondfeuer, Essen oder Kreis ein. | `op.event.invite` | Host will einladen | Einladung/Event sichtbar | Einladung statt Verpflichtung |
| `q.fest.032` | Dokumentiere, was entstanden ist. | `op.documentation.create` | Event, Projekt oder Ort hat stattgefunden | Post/Foto/Text freiwillig erstellt | Zustimmung bei Fotos und Namen beachten |

### 5.6 Follow-up und lokale Kreise

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.fest.033` | Speichere einen nächsten Schritt zu einer Begegnung. | `op.followup.create` | Verifikation, Gespräch oder Match | Follow-up-Item oder lokale Erinnerung erstellt | Kein automatisches Nachfassen ohne Zustimmung |
| `q.fest.034` | Finde Menschen aus deiner Region. | `op.people.discover` | Region oder Ort gesetzt | regionale Kontakte angezeigt | Region grob halten |
| `q.fest.035` | Lade drei Menschen zu einem ersten lokalen Essen ein. | `op.event.invite` | genug regionale Kontakte vorhanden | Einladung erstellt oder analog ausgesprochen | Kleine Gruppen reichen |
| `q.fest.036` | Starte einen lokalen Kreis mit vier Treffen. | `op.circle.start` | Gruppe will weitergehen | Kreis-/Event-Serie dokumentiert | Kreis bleibt selbstorganisiert |
| `q.fest.037` | Schlage ein erstes gemeinsames Projekt vor. | `op.project.start` | Gruppe hat gemeinsames Thema | Projekt-Item oder Task erstellt | Projekt darf klein beginnen |
| `q.fest.038` | Macht eine Ressource zum Commons. | `op.commons.create` | Gegenstand, Ort oder Material wird geteilt | Commons-/Resource-Notiz erstellt | Hüter/Pflege nur explizit machen, wenn nötig |
| `q.fest.039` | Lade eine bestehende Initiative ein, sichtbar zu werden. | `op.initiative.connect` | Initiative passt zum Netzwerk | Kontakt, Profil oder Ort dokumentiert | Nicht vereinnahmen |
| `q.fest.040` | Erzähle nach dem Festival, was weiterlebt. | `op.documentation.create` | Festival vorbei | kurzer Bericht, Bild oder Update erstellt | Keine Erfolgspflicht erzeugen |

## 6. Priorisierung für Rollout v0.1

Für einen ersten öffentlichen Einsatz sind nicht alle Quests gleich wichtig.

**P0: Muss im ersten App-/Crew-Slice funktionieren**

- `q.fest.001` bis `q.fest.005`
- `q.fest.007` bis `q.fest.010`
- `q.fest.014` bis `q.fest.017`
- `q.fest.021`
- `q.fest.033`

**P1: Sollte durch Agent, Crew oder einfache UI möglich sein**

- `q.fest.011` bis `q.fest.013`
- `q.fest.018` bis `q.fest.020`
- `q.fest.022` bis `q.fest.024`
- `q.fest.027` bis `q.fest.032`
- `q.fest.034` und `q.fest.035`

**P2: Anschluss nach dem Festival / lokaler Netzwerkaufbau**

- `q.fest.025` und `q.fest.026`
- `q.fest.036` bis `q.fest.040`

## 7. Agentenlogik

Ein Agent SOLLTE Quests nur vorschlagen, wenn mindestens eine der folgenden Bedingungen erfüllt ist:

- Die Person befindet sich sichtbar in einem passenden Flow.
- Die Person hat um Hilfe, Vorschläge oder Reflexion gebeten.
- Ein lokaler Kontext macht den Vorschlag offensichtlich sinnvoll, z.B. Festival-Space, Vernetzungszelt, gemeinsamer Ort oder bestehendes Follow-up.

Ein Agent MUSS bei Quest-Vorschlägen erklären können:

- warum diese Quest jetzt vorgeschlagen wird,
- welche Daten dafür verwendet wurden,
- wie die Person ablehnen oder ausblenden kann,
- welche Sichtbarkeit durch den nächsten Schritt entsteht.

## 8. Offene Fragen

- Welche Quests werden in der App persistiert und welche bleiben lokale Suggestions?
- Welche Quest-Texte brauchen eine kürzere App-Card-Version?
- Welche Quests darf ein Agent automatisch vorschlagen und welche nur nach Nachfrage?
- Welche Quests brauchen Crew-Fallbacks auf Papier?
- Welche Quests sind für Kinder/Jugendliche ungeeignet oder brauchen besondere Schutzmechanismen?
