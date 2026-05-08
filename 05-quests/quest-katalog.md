# Quest-Katalog v0.1

**Status:** Entwurf v0.1
**Datum:** 2026-05-08
**Scope:** Erste freiwillige Handlungseinladungen für Pax-/Festival-Kontexte, lokale Kreise und App-v0.1-Nutzerführung.

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

Jede Quest in diesem Katalog MUSS:

1. freiwillig sein,
2. ablehnbar oder ausblendbar sein,
3. ohne negative Bewertung unvollendet bleiben dürfen,
4. einen sozialen Zweck haben,
5. klar machen, welche Daten sichtbar werden,
6. keine riskanten, beschämenden oder übergriffigen Nachweise verlangen.

Eine Quest DARF:

- als App-Karte,
- als Agentenvorschlag,
- als Crew-Einladung,
- als Checklistenpunkt,
- als Follow-up nach einem Event

erscheinen.

## 3. Operations-Namespace

Die Operationen `op.app.open`, `op.identity.create`, `op.space.join`, `op.profile.create`, `op.visibility.set`, `op.people.discover`, `op.verification.create`, `op.offer.need.publish`, `op.quest.suggest` und `op.followup.create` gehören zum Pax-P0-Mapping.

Weitere Operationen in diesem Katalog, z.B. `op.event.create`, `op.project.start` oder `op.commons.create`, sind vorläufige P1/P2-Operationsnamen. Sie beschreiben den sozialen Zweck, müssen aber vor einer strikten Implementierung noch in [../03-social-operations](../03-social-operations/) und [../06-data-model/operations-mapping.md](../06-data-model/operations-mapping.md) formalisiert werden.

## 4. Minimale Quest- und Teilnahme-View

Eine App DARF Quests als generische Real-Life-Stack-Items oder als lokale Suggestions abbilden. Persistenz ist für Pax v0.1 optional.

```json
{
  "type": "quest",
  "schema": "rlnp:quest",
  "schemaVersion": 1,
  "status": "published",
  "data": {
    "title": "Finde eine Person mit ähnlichem Interesse",
    "description": "Schau dir Profile im Pax-Space an und lade eine Person zu einem echten Gespräch ein.",
    "operation": "op.people.discover",
    "phase": "during-event",
    "optional": true,
    "tags": ["begegnung", "pax-2026"]
  }
}
```

Eine lokale Suggestion oder persönliche Durchführung verweist auf diese Quest:

```json
{
  "type": "quest-participation",
  "schema": "rlnp:quest-participation",
  "schemaVersion": 1,
  "questId": "q.pax.015",
  "actor": "did:example:alice",
  "status": "suggested",
  "completion": {
    "kind": "self-confirmed",
    "evidence": "none"
  }
}
```

**Norm:** Eine Quest-Completion ist ein lokaler Bedienzustand oder eine freiwillige Dokumentation einer konkreten Quest-Teilnahme. Sie ist kein globaler Quest-Status, kein Vertrauensbeweis und kein sozialer Score.

## 5. Katalog

### 5.1 Einstieg und Selbstbesitz

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.pax.001` | Öffne die App oder Web-App. | `op.app.open` | Stand-QR, Link, Crew-Einladung | App ist geöffnet | Kein Installationszwang |
| `q.pax.002` | Erzeuge deine eigene lokale ID. | `op.identity.create` | keine lokale DID vorhanden | DID/Schlüssel lokal erzeugt | Kein zentrales Konto suggerieren |
| `q.pax.003` | Lies kurz, was deine ID bedeutet. | `op.identity.create` | neue DID erzeugt | Hinweis wurde gesehen | Kurz, ehrlich, nicht technisch überladen |
| `q.pax.004` | Tritt freiwillig dem Pax-Space bei. | `op.space.join` | gültiger Pax-Invite | Space-Mitgliedschaft aktiv | Ablehnen bleibt normal |
| `q.pax.005` | Entscheide, ob du im Pax-Space sichtbar sein möchtest. | `op.visibility.set` | Space-Beitritt aktiv | Sichtbarkeitszustand gesetzt | Sichtbarkeit muss änderbar bleiben |
| `q.pax.006` | Bitte die Crew um eine analoge Einführung, wenn etwas unklar ist. | `op.app.open` | Unsicherheit, technischer Fehler | Frage gestellt oder Hilfe erhalten | Kein Druck zur Selbstbedienung |

### 5.2 Profil, Angebote und Bedürfnisse

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.pax.007` | Ergänze deinen Rufnamen. | `op.profile.create` | Profil leer oder minimal | Name/Rufname gespeichert | Pseudonym ist erlaubt |
| `q.pax.008` | Schreibe einen Satz: Was bewegt dich gerade? | `op.profile.create` | Profil vorhanden | kurzer Profiltext gespeichert | Keine intime Selbstoffenbarung erzwingen |
| `q.pax.009` | Trage ein Angebot als Tag ein. | `op.offer.need.publish` | Profil vorhanden | `offers[]` enthält mindestens einen Tag | Tags bleiben einfache Profilfelder |
| `q.pax.010` | Trage ein Bedürfnis oder eine Suche als Tag ein. | `op.offer.need.publish` | Profil vorhanden | `needs[]` enthält mindestens einen Tag | Bedürfnis darf offen und unfertig sein |
| `q.pax.011` | Ergänze eine Vision oder ein Thema, das dich ruft. | `op.profile.create` | Profil vorhanden | Vision/Interesse sichtbar oder privat gespeichert | Kein Missionierungsdruck |
| `q.pax.012` | Wähle eine grobe Region statt exaktem Standort. | `op.visibility.set` | Person will lokal auffindbar sein | Region oder Festival-Ort gesetzt | Exakte Standortdaten nicht verlangen |
| `q.pax.013` | Prüfe, welche Profilfelder sichtbar sind. | `op.visibility.set` | Profil enthält Daten | Sichtbarkeit bewusst bestätigt | Keine stillen Veröffentlichungen |

### 5.3 Menschen entdecken und begegnen

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.pax.014` | Schau dir drei Profile im Pax-Space an. | `op.people.discover` | Space hat sichtbare Profile | Profile wurden geöffnet | Kein Ranking von Menschen |
| `q.pax.015` | Finde eine Person mit ähnlichem Interesse. | `op.people.discover` | passende Tags/Visionen sichtbar | Person gemerkt oder kontaktiert | Vorschlag bleibt Einladung |
| `q.pax.016` | Finde eine Person, deren Angebot zu deinem Bedürfnis passt. | `op.people.discover` | Offer-/Need-Tags vorhanden | mögliche Verbindung erkannt | Match nicht als Verpflichtung darstellen |
| `q.pax.017` | Lade jemanden zu einem echten Gespräch ein. | `op.people.discover` | passende Person gefunden | Einladung ausgesprochen oder gesendet | Nein muss leicht bleiben |
| `q.pax.018` | Geh zum Vernetzungszelt und sprich jemanden Neues an. | `op.people.discover` | Person ist vor Ort | Begegnung analog begonnen | Keine unangenehmen Mutproben |
| `q.pax.019` | Bitte die Crew um eine passende Vorstellung. | `op.people.discover` | Person sucht Anschluss | Crew/Agent schlägt Verbindung vor | Nur mit sichtbarem Kontext arbeiten |
| `q.pax.020` | Führe ein Gespräch über eure Visionen. | `op.people.discover` | Begegnung findet statt | Gespräch selbst bestätigt | Kein Gesprächsinhalt muss gespeichert werden |

### 5.4 QR-Verifikation und Beziehung

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.pax.021` | Verifiziert euch per QR, wenn ihr eure Begegnung festhalten wollt. | `op.verification.create` | reale Begegnung hat stattgefunden | Verification-Attestation VC-JWS erstellt | Verifikation bestätigt Begegnung, nicht globale Vertrauenswürdigkeit |
| `q.pax.022` | Lass dir erklären, was QR-Verifikation bedeutet. | `op.verification.create` | erste Verifikation | Erklärung gelesen oder Crew gefragt | Keine Kryptographie-Vorlesung im Flow |
| `q.pax.023` | Bestätige eine eingehende Gegenverifikation. | `op.verification.create` | eingehende Verification-Attestation | Gegenverifikation erstellt oder abgelehnt | Ablehnen bleibt möglich |
| `q.pax.024` | Ergänze optional Kontext zur Begegnung. | `op.verification.create` | Verifikation abgeschlossen | Ort/Event/Notiz lokal oder als Metadaten gesetzt | Kontext darf privat bleiben |
| `q.pax.025` | Sende eine konkrete Attestation für einen beobachteten Beitrag. | `op.attestation.create` | Person hat real etwas beigetragen | Attestation-VC-JWS erstellt | Nur konkret Beobachtetes attestieren |
| `q.pax.026` | Entscheide, ob du eine erhaltene Attestation anzeigen möchtest. | `op.attestation.visibility.set` | Attestation empfangen | Sichtbarkeit lokal gesetzt | Empfängerprinzip respektieren |

### 5.5 Ressourcen, Orte und Veranstaltungen

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.pax.027` | Frage nach einer Ressource, die du gerade brauchst. | `op.offer.need.publish` | konkretes Bedürfnis vorhanden | Need-Tag oder Nachricht erstellt | Bedürfnis nicht bewerten |
| `q.pax.028` | Biete etwas an, das du gerne teilst. | `op.offer.need.publish` | Person will beitragen | Offer-Tag erstellt | Kein Selbstvermarktungsdruck |
| `q.pax.029` | Dokumentiere einen Ort, der für Begegnung wichtig ist. | `op.place.create` | Ort existiert oder wird genutzt | Place-/Marker-Item oder Notiz erstellt | Eigentum, Pflege und Sichtbarkeit klären |
| `q.pax.030` | Trage ein Gemeinschaftsessen oder Treffen ein. | `op.event.create` | Event geplant oder spontan | Event-/Post-/Calendar-Item erstellt | Keine Teilnahmeüberwachung |
| `q.pax.031` | Lade Menschen zu einem Vollmondfeuer, Essen oder Kreis ein. | `op.event.invite` | Host will einladen | Einladung/Event sichtbar | Einladung statt Verpflichtung |
| `q.pax.032` | Dokumentiere, was entstanden ist. | `op.documentation.create` | Event, Projekt oder Ort hat stattgefunden | Post/Foto/Text freiwillig erstellt | Zustimmung bei Fotos und Namen beachten |

### 5.6 Follow-up und lokale Kreise

| ID | Einladung | Operation | Auslöser | Abschluss | Leitplanke |
|---|---|---|---|---|---|
| `q.pax.033` | Speichere einen nächsten Schritt zu einer Begegnung. | `op.followup.create` | Verifikation, Gespräch oder Match | Follow-up-Item oder lokale Erinnerung erstellt | Kein automatisches Nachfassen ohne Zustimmung |
| `q.pax.034` | Finde Menschen aus deiner Region. | `op.people.discover` | Region oder Ort gesetzt | regionale Kontakte angezeigt | Region grob halten |
| `q.pax.035` | Lade drei Menschen zu einem ersten lokalen Essen ein. | `op.event.invite` | genug regionale Kontakte vorhanden | Einladung erstellt oder analog ausgesprochen | Kleine Gruppen reichen |
| `q.pax.036` | Starte einen lokalen Kreis mit vier Treffen. | `op.circle.start` | Gruppe will weitergehen | Kreis-/Event-Serie dokumentiert | Kreis bleibt selbstorganisiert |
| `q.pax.037` | Schlage ein erstes gemeinsames Projekt vor. | `op.project.start` | Gruppe hat gemeinsames Thema | Projekt-Item oder Task erstellt | Projekt darf klein beginnen |
| `q.pax.038` | Macht eine Ressource zum Commons. | `op.commons.create` | Gegenstand, Ort oder Material wird geteilt | Commons-/Resource-Notiz erstellt | Hüter/Pflege nur explizit machen, wenn nötig |
| `q.pax.039` | Lade eine bestehende Initiative ein, sichtbar zu werden. | `op.initiative.connect` | Initiative passt zum Netzwerk | Kontakt, Profil oder Ort dokumentiert | Nicht vereinnahmen |
| `q.pax.040` | Erzähle nach dem Festival, was weiterlebt. | `op.documentation.create` | Festival vorbei | kurzer Bericht, Bild oder Update erstellt | Keine Erfolgspflicht erzeugen |

## 6. Priorisierung für Pax v0.1

Für einen ersten öffentlichen Einsatz sind nicht alle Quests gleich wichtig.

**P0: Muss im ersten App-/Crew-Slice funktionieren**

- `q.pax.001` bis `q.pax.005`
- `q.pax.007` bis `q.pax.010`
- `q.pax.014` bis `q.pax.017`
- `q.pax.021`
- `q.pax.033`

**P1: Sollte durch Agent, Crew oder einfache UI möglich sein**

- `q.pax.011` bis `q.pax.013`
- `q.pax.018` bis `q.pax.020`
- `q.pax.022` bis `q.pax.024`
- `q.pax.027` bis `q.pax.032`
- `q.pax.034` und `q.pax.035`

**P2: Anschluss nach Pax / lokaler Netzwerkaufbau**

- `q.pax.025` und `q.pax.026`
- `q.pax.036` bis `q.pax.040`

## 7. Agentenlogik

Ein Agent SOLLTE Quests nur vorschlagen, wenn mindestens eine der folgenden Bedingungen erfüllt ist:

- Die Person befindet sich sichtbar in einem passenden Flow.
- Die Person hat um Hilfe, Vorschläge oder Reflexion gebeten.
- Ein lokaler Kontext macht den Vorschlag offensichtlich sinnvoll, z.B. Pax-Space, Vernetzungszelt, gemeinsamer Ort oder bestehendes Follow-up.

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
