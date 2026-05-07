# Operations Mapping

**Status:** Entwurf v0.1
**Datum:** 2026-05-07
**Scope:** Mapping der Pax-v0.1-Operationen auf App-Flows, Datenobjekte, Relationen, Claims, Quests, Agentenhilfe und Metriken.

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

## 3. Operation Index

| ID | Operation | Sozialer Zweck | P0 für Pax |
|---|---|---|---|
| `op.app.open` | App laden/öffnen | Einstieg ins Werkzeug | ja |
| `op.identity.create` | Lokale Identität erzeugen | Selbstbesitz und Trust-Fundament | ja |
| `op.space.join` | Pax-Space beitreten | Gemeinsamer Festival-Kontext | ja |
| `op.profile.create` | Minimalprofil anlegen | Wiedererkennung und Ansprechbarkeit | ja |
| `op.visibility.set` | Sichtbarkeit setzen | Auffindbarkeit mit Zustimmung | ja |
| `op.people.discover` | Menschen entdecken | Begegnung wahrscheinlicher machen | ja |
| `op.encounter.record` | Begegnung festhalten | Beziehungskontext erfassen | optional/P1 |
| `op.verification.create` | Menschen verifizieren | Reale Begegnung bestätigen | ja |
| `op.offer.need.publish` | Angebote/Bedürfnisse teilen | Kooperation und Ressourcenteilung ermöglichen | ja |
| `op.quest.suggest` | Nächsten Schritt vorschlagen | Einladung zu sinnvoller Handlung | ja |
| `op.followup.create` | Verbunden bleiben | Anschluss nach Festival sichern | ja |

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
  -> optional verifizieren
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
| `op.visibility.set` | Visibility Settings | Space-/Map-Sichtbarkeit wählen | private bleiben, Region statt genauer Ort | keine Sichtbarkeit -> nicht auffindbar |
| `op.people.discover` | Map/List/Search | Profil/Eintrag öffnen | filtern, merken, ausblenden | keine Treffer -> Crew/Agent kann analoge Einladung geben |
| `op.encounter.record` | Encounter Note / Event Context | Begegnung kontextualisieren | später dokumentieren | nicht dokumentieren -> Beziehung kann trotzdem entstehen |
| `op.verification.create` | QR Challenge / Scanner | Begegnung bestätigen | Gegenverifikation, manuelle Code-Eingabe | Fehler -> später erneut versuchen |
| `op.offer.need.publish` | Profile or Marketplace Edit | Angebot/Bedürfnis eintragen | Tags, Sichtbarkeit, Ablaufdatum | leer lassen -> kein Druck |
| `op.quest.suggest` | Quest Suggestion Card | Einladung annehmen | ablehnen, später, ausblenden | Ablehnung wird nicht negativ gewertet |
| `op.followup.create` | Follow-up View | Kontakt halten / nächsten Schritt speichern | Nachricht, lokaler Kreis, Event | kein Follow-up -> Beziehung bleibt als Kontakt |

## 6. Data Object Catalog

Diese Objekte beschreiben die fachliche Ebene. Eine Implementierung darf sie direkt als Item-Typen, als Felder bestehender Typen oder als abgeleitete Views umsetzen.

| Objekt | Zweck | Bestehendes Primitive | Gap / Empfehlung |
|---|---|---|---|
| `Identity` | lokale DID und Schlüssel | WoT Identity | vorhanden |
| `DeviceState` | lokaler Onboarding-/Installationszustand | App-local storage | lokal, nicht Space-Daten |
| `SpaceInvite` | Einladung in Pax-Space | WoT space invite | vorhanden/zu stabilisieren |
| `SpaceMembership` | Mitgliedschaft im Pax-Space | WoT/RLS Group | vorhanden |
| `Profile` | Rufname, Bio, Avatar, Angebote, Bedürfnisse, Vision | RLS `profile` | Vision/Region/Sichtbarkeit ergänzen |
| `VisibilityPreference` | private/space/public/map Sichtbarkeit | teilweise Profil-Feldsichtbarkeit | explizit modellieren |
| `MapMarker` | auffindbarer Ort/Profil/Eintrag | RLS `place` | Profil-/Offer-/Need-Marker klären |
| `Offer` | etwas, das jemand geben/teilen kann | Profil `offers[]` | P0 als Profilfeld, später eigener Item-Typ |
| `Need` | etwas, das jemand sucht/braucht | Profil `needs[]` | P0 als Profilfeld, später eigener Item-Typ |
| `Encounter` | Kontext einer realen Begegnung | none / event context | P1, optional |
| `VerificationClaim` | bestätigte Begegnung/Identität | WoT SignedClaim / Attestation | vorhanden |
| `AttestationClaim` | Beitrag/Gabe/Fähigkeit attestieren | WoT SignedClaim / Attestation | P1 für Pax |
| `Quest` | freiwillige Einladung zu einer Handlung | none / task-like | eigener Typ empfohlen |
| `FollowUp` | nächster Schritt nach Begegnung/Festival | task/post/event | eigener leichter Typ oder Task |
| `MetricEvent` | aggregierbares Netzwerksignal | none | lokal/aggregiert, keine Rankings |

## 7. Minimal Item Types

### 7.1 `profile`

Pax-v0.1 SOLLTE mit einem erweiterten Profil arbeiten:

```json
{
  "type": "profile",
  "data": {
    "name": "Mira",
    "avatar": "optional-url",
    "bio": "Ich interessiere mich für Gemeinschaftsgärten.",
    "vision": "Ich will in meiner Region mehr gemeinsame Orte aufbauen.",
    "offers": ["Kochen", "Moderation", "Gartenarbeit"],
    "needs": ["Werkstattzugang", "Menschen in Leipzig"],
    "region": "Leipzig",
    "visibility": {
      "profile": "space",
      "map": "region",
      "offers": "space",
      "needs": "space"
    }
  }
}
```

### 7.2 `quest`

Quests SOLLTEN als eigene Einladungsobjekte modelliert werden.

```json
{
  "type": "quest",
  "data": {
    "title": "Lerne eine Person mit ähnlichem Interesse kennen",
    "operation": "op.people.discover",
    "intent": "relationship",
    "description": "Finde jemanden im Pax-Space, dessen Vision dich berührt, und führe ein echtes Gespräch.",
    "status": "suggested",
    "optional": true,
    "context": {
      "spaceId": "pax-2026",
      "source": "agent"
    },
    "completion": {
      "kind": "self-confirmed",
      "evidence": "none"
    }
  }
}
```

**Normen:**

- `optional` MUSS für protokollkonforme Quests wahr sein.
- `status` DARF NICHT als Leistungsskala verwendet werden.
- `completion` DARF keine riskanten oder übergriffigen Nachweise verlangen.

### 7.3 `offer` und `need`

P0 DARF Angebote und Bedürfnisse als Profilfelder abbilden. Sobald Suche, Verfügbarkeit, Ablaufdatum oder mehrere Owner nötig werden, SOLLTEN sie eigene Items werden.

```json
{
  "type": "offer",
  "data": {
    "title": "Ich kann beim Kochen helfen",
    "description": "Gerne für Gemeinschaftsessen am Abend.",
    "tags": ["kochen", "essen", "festival"],
    "availability": "during-pax",
    "visibility": "space"
  },
  "relations": [
    { "predicate": "offeredBy", "target": "global:did:example:mira" },
    { "predicate": "visibleIn", "target": "space:pax-2026" }
  ]
}
```

## 8. Relation Taxonomy

| Predicate | Von | Zu | Bedeutung |
|---|---|---|---|
| `memberOf` | Profile/Identity | Space | Person/Agent ist Mitglied eines Spaces |
| `visibleIn` | Item/Profile | Space | Item ist in einem Space sichtbar |
| `locatedAt` | Event/Place/Marker | Place | findet an Ort statt |
| `locatedNear` | Profile/Offer/Need | Place/Region | ungefähre räumliche Nähe |
| `offeredBy` | Offer | Profile | Angebot gehört zu Person/Agent |
| `neededBy` | Need | Profile | Bedürfnis gehört zu Person/Agent |
| `metAt` | Encounter/Verification | Event/Place | Begegnungskontext |
| `verified` | VerificationClaim | Profile/Identity | bestätigte Identitätsbeziehung |
| `attests` | AttestationClaim | Profile/Identity | Aussage über Beitrag/Gabe/Fähigkeit |
| `suggestedTo` | Quest | Profile/Identity | Quest wurde vorgeschlagen |
| `relatedTo` | Item | Item | allgemeiner Bezug |
| `followUpFor` | FollowUp | Encounter/Event/Quest | Anschluss an vorherige Erfahrung |
| `documentedBy` | Event/Encounter/Project | Post/Media | Dokumentation eines Geschehens |

**Norm:** Relationen MÜSSEN beschreiben, was passiert ist oder vorgeschlagen wird. Sie DÜRFEN NICHT implizieren, dass ein Mensch wertvoller ist als ein anderer.

## 9. Claim Mapping

### 9.1 Verification Claim

Verifikation bestätigt Begegnung oder Identitätsbeziehung.

Empfohlene Claim-Form:

```json
{
  "claim": "physical-meeting",
  "tags": ["verification", "pax-2026"],
  "from": "did:example:alice",
  "to": "did:example:bob",
  "context": {
    "spaceId": "pax-2026",
    "event": "Pax Friedensfestival 2026"
  }
}
```

### 9.2 Attestation Claim

Attestations sind für Pax v0.1 nicht zwingend, aber anschlussfähig.

```json
{
  "claim": "Mira hat beim gemeinsamen Abendessen für die Gruppe gekocht.",
  "tags": ["attestation", "contribution", "cooking", "pax-2026"],
  "from": "did:example:jonas",
  "to": "did:example:mira"
}
```

**Norm:** Attestations SOLLTEN konkret, beobachtbar und kontextbezogen sein.

## 10. Visibility Model

| Level | Bedeutung | Beispiel |
|---|---|---|
| `private` | nur lokal sichtbar | Entwurf, nicht veröffentlicht |
| `contacts` | für verifizierte/aktive Kontakte sichtbar | Telefonnummer |
| `space` | im Pax-Space sichtbar | Angebot, Bedürfnis, Vision |
| `public` | öffentlich sichtbar | freiwillige Profilseite |
| `region` | ungefähre räumliche Sichtbarkeit | "Leipzig" statt GPS |

**Normen:**

- Sichtbarkeit MUSS vor oder beim Veröffentlichen erkennbar sein.
- Exakte Standortdaten DÜRFEN NICHT Voraussetzung für Teilnahme sein.
- Eine Person MUSS Sichtbarkeit später reduzieren können.

## 11. Quest Mapping

| Quest | Operation | Trigger | Completion | Agentenhilfe |
|---|---|---|---|---|
| App öffnen | `op.app.open` | QR gescannt | App gestartet | Einstieg erklären |
| Eigene ID erzeugen | `op.identity.create` | keine ID vorhanden | DID vorhanden | Selbstbesitz erklären |
| Pax-Space beitreten | `op.space.join` | Invite erkannt | Mitgliedschaft aktiv | Sichtbarkeit erklären |
| Profil ergänzen | `op.profile.create` | leeres Profil | Mindestfelder gesetzt | Formulierungsvorschlag |
| Angebot eintragen | `op.offer.need.publish` | Profil vorhanden | Offer sichtbar | Beispiele anbieten |
| Bedürfnis eintragen | `op.offer.need.publish` | Profil vorhanden | Need sichtbar | ermutigen, konkret zu werden |
| Person kennenlernen | `op.people.discover` | Matching-Signal | Begegnung selbst bestätigt | passende Person vorschlagen |
| Verifizieren | `op.verification.create` | reale Begegnung | Claim erstellt | QR-Flow erklären |
| Nächsten Schritt speichern | `op.followup.create` | Begegnung/Match | Follow-up erstellt | lokale Anschlussoption |

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
- eine Verifikation, Attestation oder Einladung im Namen eines Menschen ohne Zustimmung auslösen.

## 13. Metrics

Metriken sind Netzwerk-Signale, keine Leistungsbewertung.

| Metrik | Quelle | Zweck | Risiko |
|---|---|---|---|
| gestartete App-Sessions | `op.app.open` | Einstiegshürden erkennen | Tracking-Übergriff |
| erzeugte IDs | `op.identity.create` | Onboarding-Fortschritt | falsche Erfolgsmetrik |
| Pax-Space-Mitglieder | `op.space.join` | Pilotgröße | Wachstum um jeden Preis |
| Profile mit Angeboten/Bedürfnissen | `op.offer.need.publish` | Kooperationspotential | Selbstvermarktungsdruck |
| Verifikationen | `op.verification.create` | reale Begegnungsdichte | Vertrauensmissverständnis |
| Follow-ups | `op.followup.create` | Anschlussfähigkeit | soziale Kontrolle |
| Quests vorgeschlagen/angenommen | `op.quest.suggest` | Benutzerführung verbessern | Gamification-Druck |

**Norm:** Metriken SOLLTEN aggregiert und kontextbezogen betrachtet werden. Sie DÜRFEN NICHT als Score für Menschen verwendet werden.

## 14. MVP Implementation Notes

Für Pax v0.1 ist folgender pragmatischer Schnitt ausreichend:

1. `profile` erweitern statt sofort eigene `offer`/`need` Items erzwingen.
2. `space invite` und `group membership` für Pax-Space nutzen.
3. `SignedClaim` für Verifikation verwenden.
4. Quests zunächst als lokale/sichtbare Suggestions abbilden, nicht als hartes Belohnungssystem.
5. Map in v0.1 darf eine Listen-/Regionenansicht sein, solange Begegnung und Auffindbarkeit funktionieren.
6. Metrics nur lokal/aggregiert für Pilot-Lernen verwenden.

## 15. Open Questions

- Werden `Offer` und `Need` für Pax eigene Items oder Profilfelder?
- Muss `Quest` bereits ein persistierter Item-Typ sein oder reicht eine abgeleitete Suggestion?
- Welche Sichtbarkeitsstufen unterstützt der erste App-Slice wirklich?
- Wie wird `region` ohne exakte Standortdaten erfasst?
- Wie werden analoge Kontakte ohne App nachträglich gemappt?
- Welche Daten darf ein Agent im Pax-Space standardmäßig sehen?
