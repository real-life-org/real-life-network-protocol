# Operations Mapping

**Status:** Entwurf v0.1
**Datum:** 2026-05-07
**Scope:** Mapping der Pax-v0.1-Operationen auf App-Flows, Datenobjekte, Relationen, Confirmations, Quests, Agentenhilfe und Metriken.

---

## 1. Zweck

Dieses Dokument übersetzt soziale Operationen in eine Form, die von Apps, Datenmodellen und KI-Agenten umgesetzt werden kann.

Es ist die Brücke zwischen:

- [Pax Rollout Slice](../08-rollout/pax-rollout-slice.md)
- Real Life Stack App-Flows
- Web of Trust Identität, Verifikation und Attestations
- Quest-Systemen
- Agenten-Handlungslogik

## 2. Designregeln

Eine Implementierung dieses Mappings MUSS:

1. Identität lokal erzeugen, bevor Space-Beitritt möglich ist.
2. Space-Beitritt als freiwillige Bestätigung behandeln.
3. Sichtbarkeit explizit und änderbar machen.
4. Quests als Einladungen formulieren.
5. Metriken nur als Netzwerk-Signale verwenden, nicht als Ranking von Menschen.
6. Agentenvorschläge erklärbar, ablehnbar und kontextbezogen machen.
7. Confirmations als backend-agnostische bestätigte Aussagen modellieren und ihre Trust-Stufe sichtbar machen.
8. Für portable, signierte Confirmations das Format der technischen Spezifikation verwenden und kein eigenes erfinden.
9. App-seitige Entitäten als generische Real-Life-Stack-Items oder Views modellieren, sofern sie keine Identität und keine signierte Attestation der technischen Spezifikation sind.

## 3. Operation Index

| ID | Operation | Sozialer Zweck | P0 für Pax |
|---|---|---|---|
| `op.app.open` | App laden/öffnen | Einstieg ins Werkzeug | ja |
| `op.identity.create` | Lokale Identität erzeugen | Selbstbesitz und Trust-Fundament | ja |
| `op.space.join` | Pax-Space beitreten | Gemeinsamer Festival-Kontext | ja |
| `op.profile.create` | Minimalprofil anlegen | Wiedererkennung und Ansprechbarkeit | ja |
| `op.share` | Etwas teilen: entscheiden, wo es liegt | Auffindbarkeit mit Zustimmung | ja |
| `op.people.discover` | Menschen entdecken | Begegnung wahrscheinlicher machen | ja |
| `op.verification.create` | Menschen verifizieren | Reale Begegnung bestätigen | ja |
| `op.confirmation.create` | Beitrag bestätigen | Beobachtete Handlung oder Completion bestätigen | nein |
| `op.confirmation.visibility.set` | Confirmation-Sichtbarkeit setzen | Empfängerprinzip und Kontext respektieren | nein |
| `op.offer.need.publish` | Angebote/Bedürfnisse teilen | Kooperation und Ressourcenteilung ermöglichen | ja |
| `op.quest.suggest` | Nächsten Schritt vorschlagen | Einladung zu sinnvoller Handlung | ja |
| `op.followup.create` | Verbunden bleiben | Anschluss nach Festival sichern | ja |

Reale Begegnungen werden nicht durch eine eigene `op.encounter.record`-Operation festgehalten. Eine Begegnung findet analog statt. Wenn sie im Netzwerk festgehalten werden soll, geschieht das durch QR-Verifikation in `op.verification.create`. Kontext wie Ort, Event oder Notiz kann als Metadaten an der Verifikation oder am Follow-up hängen.

## 4. End-to-End Flow

```text
QR/Link
  -> App/Web-App öffnen
  -> lokale Identität erzeugen oder finden
  -> Pax-Space-Invite anzeigen
  -> Pax-Space freiwillig beitreten
  -> Minimalprofil anlegen
  -> Sichtbarkeit setzen
  -> Menschen/Angebote/Bedürfnisse entdecken
  -> reale Begegnung
  -> QR-Verifikation, wenn die Begegnung festgehalten werden soll
  -> Quest/Folgeeinladung
  -> Follow-up nach Pax
```

## 5. App-Flow Mapping

| Operation | Screen / Flow | Primary Action | Secondary Actions | Fehler-/Abbruchfall |
|---|---|---|---|---|
| `op.app.open` | QR Landing, App Start, Install/Open Choice | App/Web-App starten | Pilotinfo lesen, native App installieren | App lädt nicht -> Infoseite oder Crew-Demo |
| `op.identity.create` | Onboarding: Create Identity | lokale ID erzeugen | bestehende ID verwenden, Recovery-Hinweis lesen | Abbruch -> kein Space-Beitritt |
| `op.space.join` | Space Invite Screen | Pax-Space beitreten | mehr Info, später entscheiden | Ablehnen -> kein Makel, App bleibt nutzbar |
| `op.profile.create` | Profile Wizard | Rufname und erste Felder speichern | später ausfüllen, Avatar setzen | Skip -> Profil bleibt minimal/anonym |
| `op.share` | Teilen-Dialog | Kreis wählen, in dem die Sache liegen soll | zusätzlich spiegeln, veröffentlichen, ungeteilt lassen | nicht geteilt -> bleibt beim Autor |
| `op.people.discover` | Map/List/Search | Profil/Eintrag öffnen | filtern, merken, ausblenden | keine Treffer -> Crew/Agent kann analoge Einladung geben |
| `op.verification.create` | QR Challenge / Scanner | reale Begegnung per QR bestätigen | Gegenverifikation, Ort/Event als Kontext, manuelle Code-Eingabe | Fehler -> später erneut versuchen |
| `op.confirmation.create` | Confirmation Flow | beobachteten Beitrag bestätigen | Evidence ansehen, Trust-Stufe anzeigen, später signieren | Keine Bestätigung ohne Beobachtung oder ausreichenden Kontext |
| `op.confirmation.visibility.set` | Confirmation Visibility | erhaltene Confirmation anzeigen oder verbergen | privat halten, kontextbezogen teilen | Sichtbarkeit bleibt Entscheidung der empfangenden Person |
| `op.offer.need.publish` | Profile or Marketplace Edit | Angebot/Bedürfnis eintragen | Tags, Sichtbarkeit, Ablaufdatum | leer lassen -> kein Druck |
| `op.quest.suggest` | Quest Suggestion Card | Einladung annehmen | ablehnen, später, ausblenden | Ablehnung wird nicht negativ gewertet |
| `op.followup.create` | Follow-up View | Kontakt halten / nächsten Schritt speichern | Nachricht, lokaler Kreis, Event | kein Follow-up -> Beziehung bleibt als Kontakt |

## 6. Data Object Catalog

Diese Objekte beschreiben die fachliche Ebene. Eine Implementierung darf sie direkt als Item-Typen, als Felder bestehender Typen oder als abgeleitete Views umsetzen. Confirmations sind die backend-agnostische RLNP-Sicht auf bestätigte Aussagen. Kanonische Objekte der technischen Spezifikation bleiben, was sie sind; App-Views dürfen sie anzeigen, aber nicht als alternatives Protokollformat ersetzen.

| Objekt | Zweck | Bestehendes Primitive | Gap / Empfehlung |
|---|---|---|---|
| `Identity` | lokale DID und Schlüssel | WoT Identity | vorhanden |
| `DeviceState` | lokaler Onboarding-/Installationszustand | App-local storage | lokal, nicht Space-Daten |
| `SpaceInvite` | Einladung in Pax-Space | WoT space invite | vorhanden/zu stabilisieren |
| `SpaceMembership` | Mitgliedschaft im Pax-Space | WoT/RLS Group | vorhanden |
| `Profile` | Rufname, Bio, Avatar, Angebote, Bedürfnisse, Vision | WoT Profile / RLS Item-View `type: "profile"` | RLS-Referenz setzt aktuell vor allem Name/Bio/Avatar um; Offers/Needs/Vision/Region/Sichtbarkeit ergänzen |
| `Mirror` | Sache liegt zusätzlich in einem weiteren Kreis oder bei einem Menschen | autor-signierter Snapshot, ein Home, read-only | spezifiziert in `real-life-stack/docs/spec/09-mirror-bridge.md`; Ziel „einzelner Mensch" ist offen |
| `MapMarker` | auffindbarer Ort/Profil/Eintrag | RLS `place` / abgeleitete View | Profil-, Tag- und Ressourcenmarker klären |
| `OfferTag` | etwas, das jemand geben/teilen kann | WoT Profile `offers[]`; Ziel: RLS `data.offers[]` | P0 als einfache Tags, RLS-Referenz noch nachziehen |
| `NeedTag` | etwas, das jemand sucht/braucht | WoT Profile `needs[]`; Ziel: RLS `data.needs[]` | P0 als einfache Tags, RLS-Referenz noch nachziehen |
| `VerificationConfirmation` | bestätigte Begegnung/Identität | Confirmation-View | backend-agnostische View; die portable Form legt die technische Spezifikation fest |
| `VerificationContext` | optionaler Ort/Event-Kontext einer QR-Verifikation | VC-Erweiterungsfeld oder lokale Metadaten | kein eigener P0-Typ |
| `Confirmation` | Beitrag, Gabe, Fähigkeit, Teilnahme oder Abschluss bezeugen | RLS/RLNP Confirmation-View | ist entweder behauptet oder prüfbar |
| `Attestation` | portable signierte Confirmation | Format der technischen Spezifikation | P1 für Pax |
| `Quest` | freiwillige Einladung zu einer Handlung | RLS generisches Item | `type: "quest"` oder task-kompatible View |
| `QuestRun` | konkrete Durchführung einer Quest durch einen Menschen | RLS generisches Item mit Relations | `type: "quest-run"`; verweist per `runsQuest` auf Quest und per `actor` auf DID/Profile |
| `FollowUp` | nächster Schritt nach Begegnung/Festival | RLS generisches Item (`task`, `event`, `post`, `quest`) | leichter Item-Schnitt statt Sonderformat |
| `MetricEvent` | aggregierbares Netzwerksignal | none | lokal/aggregiert, keine Rankings |

## 7. Real-Life-Stack Item Views

Der Real-Life-Stack arbeitet mit generischen Items:

```typescript
interface Item {
  id: string
  type: string
  createdAt: string
  createdBy: string
  schema?: string
  schemaVersion?: number
  data: Record<string, unknown>
  relations?: Relation[]
}
```

Die folgenden Beispiele sind deshalb keine neuen Top-Level-Protokollobjekte, sondern Real-Life-Stack-Item-Views. `title`, `description`, `offers`, `needs`, `visibility` und ähnliche Felder leben in `data`.

Wichtig für Pax v0.1: Das RLS-`data-interface` kennt Profile als generische Items und `ProfileItemData` enthält optionale `offers`/`needs`. Die aktuelle RLS-Referenz-/WoT-Connector-Projection setzt das eigene Profil aber vor allem mit `name`, `bio` und `avatar` um. Die WoT-App hat `offers` und `needs` bereits als Profilfelder. Eine Pax-Implementierung SOLLTE diese WoT-Profilfelder verwenden und sie in eine RLS-kompatible Profile-Item-View mappen, sobald der Connector sie durchreicht.

### 7.1 `profile`

Pax-v0.1 SOLLTE Profile als generische Item-View `type: "profile"` behandeln. Angebote und Bedürfnisse bleiben für P0 einfache Tags im Profil; praktisch kommen sie zunächst aus dem WoT-Profil und werden später in der RLS-Profile-View vollständig durchgereicht.

```json
{
  "id": "profile:mira",
  "type": "profile",
  "createdAt": "2026-05-07T10:00:00Z",
  "createdBy": "did:key:z6Mk...mira",
  "schema": "rlnp:profile",
  "schemaVersion": 1,
  "data": {
    "name": "Mira",
    "bio": "Ich interessiere mich für Gemeinschaftsgärten.",
    "avatar": "optional-url",
    "offers": ["kochen", "moderation", "gartenarbeit"],
    "needs": ["werkstattzugang", "menschen-in-leipzig"],
    "vision": "Ich will in meiner Region mehr gemeinsame Orte aufbauen.",
    "region": "Leipzig",
    "locationPrecision": "region"
  }
}
```

**Normen:**

- `createdBy` MUSS die User-ID/DID des Profilinhabers sein.
- `offers` und `needs` sind in Pax v0.1 einfache `string[]`-Tags, keine eigenen Items.
- Wenn ein RLS-Connector `offers`/`needs` noch nicht implementiert, MUSS die App das als fehlende Fähigkeit behandeln und darf keine leeren Felder als bewusste Aussage der Person interpretieren.
- `vision`, `region` und `locationPrecision` sind Pax-/RLNP-Erweiterungen im `data`-Objekt. `locationPrecision` sagt, wie genau der Ort gezeigt wird, nicht wer ihn sieht.
- Das Profile-Item trägt **keine** Sichtbarkeitsangabe. Wen es erreicht, folgt daraus, in welche Spaces es geteilt und ob es veröffentlicht wurde (RLNP §6.16).
- Was getrennt geteilt werden soll, ist ein eigenes Item. Kontaktdaten wie Telefonnummer oder Adresse gehören deshalb NICHT in dieses Profil-Item, sondern werden für sich geteilt. Ein Profil ist die Sicht auf alles, was den Betrachter erreicht hat, nicht ein Datensatz mit Berechtigungen.
- Ein Connector DARF `User.displayName` und `User.avatarUrl` aus diesem Profil cachen; der Cache ist nicht die Quelle der Wahrheit.

### 7.2 `quest`

Quests SOLLTEN als generische RLS-Items modelliert werden. Wenn ein Connector noch keinen eigenen Quest-Renderer hat, DARF er sie task-kompatibel darstellen; die semantische Kennzeichnung erfolgt über `type` und/oder `schema`.

```json
{
  "id": "quest:pax:meet-similar-interest",
  "type": "quest",
  "createdAt": "2026-05-07T10:05:00Z",
  "createdBy": "did:key:z6Mk...agent-or-host",
  "schema": "rlnp:quest",
  "schemaVersion": 1,
  "data": {
    "title": "Lerne eine Person mit ähnlichem Interesse kennen",
    "description": "Finde jemanden im Pax-Space, dessen Vision dich berührt, und führe ein echtes Gespräch.",
    "status": "published",
    "optional": true,
    "operation": "op.people.discover",
    "intent": "relationship",
    "tags": ["begegnung", "pax-2026"],
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
      "claim": "{actor} hat eine echte Begegnung im Pax-Space geführt.",
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
    ]
  },
  "relations": [
    { "predicate": "visibleIn", "target": "space:pax-2026" }
  ]
}
```

**Normen:**

- `optional` MUSS für protokollkonforme Quests wahr sein.
- Quest-Status beschreibt Veröffentlichung und Verwendbarkeit, nicht persönlichen Fortschritt.
- Quest-Klassifizierung SOLLTE über `operation`, `intent`, `tags` oder `templateId` erfolgen, nicht über eine harte Quest-Typ-Taxonomie.
- `visibility` im `data`-Objekt beschreibt die gewünschte App-/Sharing-Sichtbarkeit; technische Durchsetzung kann zusätzlich über Connector-Berechtigungen erfolgen.
- `evidencePolicy`, `confirmationPolicy`, `completionConfirmationTemplate` und `safetyRequirements` gehören zur Quest-Completion-Logik, nicht zur Game-Schicht.

### 7.3 `quest-run`

QuestRuns SOLLTEN als eigene RLS-Items modelliert werden, weil sie eigenen Status, Sichtbarkeit, lokale Completion, Evidence und Confirmations haben können.

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
    "completion": {
      "claimedAt": "2026-05-07T10:20:00Z",
      "claim": "Ich habe ein echtes Gespräch im Pax-Space geführt.",
      "evidenceRefs": []
    }
  },
  "relations": [
    { "predicate": "runsQuest", "target": "item:quest:pax:meet-similar-interest" },
    { "predicate": "actor", "target": "global:did:key:z6Mk...mira" }
  ]
}
```

**Normen:**

- Die ausführende Person MUSS über die `actor`-Relation erkennbar sein; `createdBy` ist nur die Identität, die das Item erstellt hat.
- QuestRun-Status DARF NICHT als Leistungsskala verwendet werden.
- `completion` und `evidence` DÜRFEN keine riskanten oder übergriffigen Nachweise verlangen.
- QuestRuns sind Einladungshilfe und Dokumentation, kein Menschen-Score.

### 7.4 `offer` und `need` als Tags

Pax v0.1 definiert keine eigenen `offer`- oder `need`-Items. Angebote und Bedürfnisse sind zunächst einfache Tags im Profil. In der WoT-App sind sie bereits Teil des Profils; in RLS sind sie Ziel-Felder der Profile-Item-View und müssen in der Referenzimplementierung noch vollständig umgesetzt werden.

```json
{
  "type": "profile",
  "data": {
    "offers": ["kochen", "moderation", "gartenarbeit"],
    "needs": ["werkstattzugang", "menschen-in-leipzig"]
  }
}
```

Eigene Offer-/Need-Items sind P1/P2, sobald Verfügbarkeit, mehrere Owner, Ablaufdaten, Ressourcenlogik, Reservierung oder Commons-Verwaltung gebraucht werden.

## 8. Relation Taxonomy

| Predicate | Von | Zu | Bedeutung |
|---|---|---|---|
| `memberOf` | Profile/Identity | Space | Person/Agent ist Mitglied eines Spaces |
| `visibleIn` | Item/Profile | Space | Item ist in einem Space sichtbar |
| `locatedAt` | Event/Place/Marker | Place | findet an Ort statt |
| `locatedNear` | Profile / P1 Offer-/Need-Item | Place/Region | ungefähre räumliche Nähe |
| `partOf` | Quest/QuestRun/Item | Event/Project/Commons/Space | gehört zu einem Kontext |
| `offeredBy` | P1 Offer-Item | Profile | Angebot gehört zu Person/Agent |
| `neededBy` | P1 Need-Item | Profile | Bedürfnis gehört zu Person/Agent |
| `metAt` | Verification-Confirmation-View | Event/Place | Ort oder Event der QR-verifizierten Begegnung |
| `verified` | Verification-Confirmation-View | Profile/Identity | bestätigte Identitätsbeziehung |
| `attests` | Confirmation-View oder Attestation-View | Profile/Identity/Item | Aussage über Beitrag/Gabe/Fähigkeit |
| `runsQuest` | QuestRun | Quest | Run gehört zu dieser Quest |
| `actor` | QuestRun | Profile/Identity | Mensch, der den Run ausführt |
| `forkedFrom` | Quest | Quest | Quest ist lokale Kopie oder Anpassung |
| `relatedTo` | Item | Item | allgemeiner Bezug |
| `followUpFor` | FollowUp-Item | Verification-Confirmation/Event/Quest | Anschluss an vorherige Erfahrung |
| `documentedBy` | Event/Verification-Confirmation/Project | Post/Media | Dokumentation eines Geschehens |

**Norm:** Relationen MÜSSEN beschreiben, was passiert ist oder vorgeschlagen wird. Sie DÜRFEN NICHT implizieren, dass ein Mensch wertvoller ist als ein anderer. Eine bestätigte QuestRun-Completion SOLLTE durch eine `attests`-Relation von einer Confirmation-View auf den QuestRun, Beitrag oder das Ergebnis sichtbar werden. Portable Completion braucht eine signierte Attestation-View.

## 9. Confirmation und Attestation Mapping

### 9.1 Backend-agnostische Confirmation-View

RLNP definiert keine eigene portable Claim-Serialisierung. Für App- und Connector-Views braucht es trotzdem eine neutrale Sicht auf bestätigte Aussagen.

```ts
type ConfirmationTrustLevel =
  | "asserted"    // man muss dem Aussteller oder seinem Server glauben
  | "verifiable"  // signiert und unabhängig nachrechenbar

type ConfirmationView = {
  id: string
  subjectId: string
  issuerId?: string
  claim: string
  schema?: string
  tags?: string[]
  relations?: Relation[]
  createdAt: string
  trustLevel: ConfirmationTrustLevel
  source?: string
  isAccepted?: boolean
}
```

Eine Confirmation-View ist keine neue Quelle der Wahrheit. Sie ist die RLNP-/RLS-Projektion einer bestätigten Aussage aus einem konkreten Backend: lokale Daten, Serverzustand, Space-Host, Systemregel oder signierte Attestation.

### 9.2 Verification-Confirmation

Verifikation bestätigt Begegnung oder Identitätsbeziehung.

Für Pax v0.1 ist QR-Verifikation der Mechanismus, durch den reale Begegnungen im Netzwerk festgehalten werden.

Backend-agnostisch ist das eine Verification-Confirmation. Soll die Verifikation portabel und unabhängig prüfbar sein, wird sie als signierte Attestation ausgestellt. Sie hält dann mindestens fest, wer bestätigt, wen es betrifft, was bestätigt wird, wann es war und in welchem Kontext.

**Norm:** Das Format signierter Attestationen legt die technische Spezifikation fest. Dieses Dokument DARF kein eigenes Format definieren und SOLLTE auch keines fest verdrahten, solange die technische Spezifikation neu gefasst wird. Eine Real-Life-Stack-UI DARF eine vereinfachte Confirmation- oder Kontakt-View ableiten; die portable Quelle der Wahrheit bleibt die signierte Attestation.

### 9.3 Attestation

Attestations sind portable, signierte Confirmations. Sie sind für Pax v0.1 nicht zwingend, aber anschlussfähig. Eine Attestation über einen Beitrag hält dieselben Angaben fest wie eine Verification-Confirmation; nur ist die bestätigte Aussage ein konkreter Beitrag statt einer Begegnung, zum Beispiel „Mira hat beim gemeinsamen Abendessen für die Gruppe gekocht".

**Norm:** Confirmations SOLLTEN konkret, beobachtbar und kontextbezogen sein. Eine Confirmation, die portabel sein soll, MUSS als signierte Attestation im Format der technischen Spezifikation erzeugt, transportiert und geprüft werden; vereinfachte App-Objekte sind nur Projektionen.

## 10. Visibility Model

Sichtbarkeit ist keine Eigenschaft eines Items, sondern folgt daraus, wo es liegt (RLNP §6.16). Ein Item hat deshalb keine Sichtbarkeitsstufe, sondern einen Ort:

| Weg | Mechanismus | Stand |
|---|---|---|
| in einem Kreis | Item liegt in einer Group; Mitgliedschaft entscheidet | gebaut |
| gespiegelt in einen weiteren Kreis | Mirror mit autor-signiertem Snapshot, ein Home, read-only | spezifiziert, siehe `real-life-stack/docs/spec/09-mirror-bridge.md` |
| gespiegelt zu einem einzelnen Menschen | derselbe Mechanismus mit einem Menschen als Ziel | **offen** — dieselbe Lücke wie 1:1-/1:n-Sharing im Stack und abtretbare Rechte für Nicht-Mitglieder in der technischen Spezifikation |
| veröffentlicht | ohne Identität und Zugehörigkeit lesbar; im Stack heute nur `getPublicProfile` | teilweise |

`region` ist ein Orts- und Auffindbarkeitsfeld, keine Sichtbarkeitsangabe. Wie genau ein Ort gezeigt wird, gehört zur Ortsangabe, nicht zur Sichtbarkeit.

**Normen:**

- Sichtbarkeit MUSS vor oder beim Teilen erkennbar sein.
- Exakte Standortdaten DÜRFEN NICHT Voraussetzung für Teilnahme sein.
- Sichtbarkeit MUSS sich für die Zukunft zurücknehmen lassen. Systeme DÜRFEN NICHT den Eindruck erwecken, Veröffentlichtes ließe sich zurückholen.
- Wer auf ein Item antworten, zusagen oder etwas anhängen können soll, MUSS Zugang zu seinem Ursprungsort haben. Ein Spiegel trägt nichts zurück.

## 11. Quest Mapping

| Quest | Operation | Trigger | Completion | Agentenhilfe |
|---|---|---|---|---|
| App öffnen | `op.app.open` | QR gescannt | App gestartet | Einstieg erklären |
| Eigene ID erzeugen | `op.identity.create` | keine ID vorhanden | DID vorhanden | Selbstbesitz erklären |
| Pax-Space beitreten | `op.space.join` | Invite erkannt | Mitgliedschaft aktiv | Sichtbarkeit erklären |
| Profil ergänzen | `op.profile.create` | leeres Profil | Mindestfelder gesetzt | Formulierungsvorschlag |
| Angebot eintragen | `op.offer.need.publish` | Profil vorhanden | Offer-Tag im Profil sichtbar | Beispiele anbieten |
| Bedürfnis eintragen | `op.offer.need.publish` | Profil vorhanden | Need-Tag im Profil sichtbar | ermutigen, konkret zu werden |
| Person kennenlernen | `op.people.discover` | Matching-Signal | Begegnung selbst bestätigt | passende Person vorschlagen |
| Verifizieren | `op.verification.create` | reale Begegnung | Verification-Confirmation erstellt; portabel als signierte Attestation | QR-Flow erklären |
| Nächsten Schritt speichern | `op.followup.create` | Begegnung/Match | Follow-up-Item erstellt | lokale Anschlussoption |

## 12. Agent Support Contract

Ein Agent DARF:

- erklären, was gerade passiert,
- beim Formulieren von Profil, Angebot, Bedürfnis oder Vision helfen,
- passende Menschen, Orte, Ressourcen oder Events vorschlagen,
- Follow-ups erinnern,
- Crew und Hosts bei Nachbereitung unterstützen.

Ein Agent MUSS:

- Vorschläge als Einladungen formulieren,
- Gründe für Vorschläge nennen,
- Ablehnung und Nicht-Reaktion akzeptieren,
- Sichtbarkeit und Kontext respektieren,
- unsichere Annahmen als unsicher markieren.

Ein Agent DARF NICHT:

- Menschen ranken,
- Druck erzeugen,
- intime oder sensible Schlüsse ohne explizite Grundlage ziehen,
- eine Verifikation, Confirmation, Attestation oder Einladung im Namen eines Menschen ohne Zustimmung auslösen.

## 13. Metrics

Metriken sind Netzwerk-Signale, keine Leistungsbewertung.

| Metrik | Quelle | Zweck | Risiko |
|---|---|---|---|
| gestartete App-Sessions | `op.app.open` | Einstiegshürden erkennen | Tracking-Übergriff |
| erzeugte IDs | `op.identity.create` | Onboarding-Fortschritt | falsche Erfolgsmetrik |
| Pax-Space-Mitglieder | `op.space.join` | Pilotgröße | Wachstum um jeden Preis |
| Profile mit Offer-/Need-Tags | `op.offer.need.publish` | Kooperationspotential | Selbstvermarktungsdruck |
| Verifikationen | `op.verification.create` | reale Begegnungsdichte | Vertrauensmissverständnis |
| Follow-ups | `op.followup.create` | Anschlussfähigkeit | soziale Kontrolle |
| Quests vorgeschlagen/angenommen | `op.quest.suggest` | Benutzerführung verbessern | Gamification-Druck |

**Norm:** Metriken SOLLTEN aggregiert und kontextbezogen betrachtet werden. Sie DÜRFEN NICHT als Score für Menschen verwendet werden.

## 14. MVP Implementation Notes

Für Pax v0.1 ist folgender pragmatischer Schnitt ausreichend:

1. `profile` erweitern statt sofort eigene `offer`/`need` Items erzwingen.
2. `space invite` und `group membership` für Pax-Space nutzen.
3. QR-Verifikation als Verification-Confirmation behandeln; portabel als signierte Attestation ausstellen; `SignedClaim` ist nur eine alte App-Projection.
4. Handlungseinladungen als lokale/sichtbare Suggestions abbilden; vollwertige `quest`-/`quest-run`-Items sind für Pax v0.1 optional.
5. Map in v0.1 darf eine Listen-/Regionenansicht sein, solange Begegnung und Auffindbarkeit funktionieren.
6. Metrics nur lokal/aggregiert für Pilot-Lernen verwenden.

## 15. Open Questions

- Wann wachsen `offers[]` und `needs[]` von Profil-Tags zu eigenen Items?
- Welche lokalen Suggestions sollen nach Pax in persistierte `quest`-/`quest-run`-Items überführt werden?
- Ab wann kann ein Spiegel einen einzelnen Menschen als Ziel haben? Das ist dieselbe Lücke wie 1:1-/1:n-Sharing im Stack und abtretbare Rechte für Nicht-Mitglieder in der technischen Spezifikation.
- Wie wird `region` ohne exakte Standortdaten erfasst?
- Wie werden analoge Kontakte ohne App nachträglich gemappt?
- Welche Daten darf ein Agent im Pax-Space standardmäßig sehen?
