# Operations Mapping

**Status:** Entwurf v0.1
**Datum:** 2026-05-07
**Scope:** Mapping der Pax-v0.1-Operationen auf App-Flows, Datenobjekte, Relationen, Claims, Quests, Agentenhilfe und Metriken.

---

## 1. Zweck

Dieses Dokument uebersetzt soziale Operationen in eine Form, die von Apps, Datenmodellen und KI-Agenten umgesetzt werden kann.

Es ist die Bruecke zwischen:

- [Pax Rollout Slice](../08-rollout/pax-rollout-slice.md)
- Real Life Stack App-Flows
- Web of Trust Identitaet, Verifikation und Attestations
- Quest-Systemen
- Agenten-Handlungslogik

## 2. Designregeln

Eine Implementierung dieses Mappings MUSS:

1. Identitaet lokal erzeugen, bevor Space-Beitritt moeglich ist.
2. Space-Beitritt als freiwillige Bestaetigung behandeln.
3. Sichtbarkeit explizit und aenderbar machen.
4. Quests als Einladungen formulieren.
5. Metriken nur als Netzwerk-Signale verwenden, nicht als Ranking von Menschen.
6. Agentenvorschlaege erklaerbar, ablehnbar und kontextbezogen machen.

## 3. Operation Index

| ID | Operation | Sozialer Zweck | P0 fuer Pax |
|---|---|---|---|
| `op.app.open` | App laden/oeffnen | Einstieg ins Werkzeug | ja |
| `op.identity.create` | Lokale Identitaet erzeugen | Selbstbesitz und Trust-Fundament | ja |
| `op.space.join` | Pax-Space beitreten | Gemeinsamer Festival-Kontext | ja |
| `op.profile.create` | Minimalprofil anlegen | Wiedererkennung und Ansprechbarkeit | ja |
| `op.visibility.set` | Sichtbarkeit setzen | Auffindbarkeit mit Zustimmung | ja |
| `op.people.discover` | Menschen entdecken | Begegnung wahrscheinlicher machen | ja |
| `op.encounter.record` | Begegnung festhalten | Beziehungskontext erfassen | optional/P1 |
| `op.verification.create` | Menschen verifizieren | Reale Begegnung bestaetigen | ja |
| `op.offer.need.publish` | Angebote/Beduerfnisse teilen | Kooperation und Ressourcenteilung ermoeglichen | ja |
| `op.quest.suggest` | Naechsten Schritt vorschlagen | Einladung zu sinnvoller Handlung | ja |
| `op.followup.create` | Verbunden bleiben | Anschluss nach Festival sichern | ja |

## 4. End-to-End Flow

```text
QR/Link
  -> App/Web-App oeffnen
  -> lokale Identitaet erzeugen oder finden
  -> Pax-Space-Invite anzeigen
  -> Pax-Space freiwillig beitreten
  -> Minimalprofil anlegen
  -> Sichtbarkeit setzen
  -> Menschen/Angebote/Beduerfnisse entdecken
  -> reale Begegnung
  -> optional verifizieren
  -> Quest/Folgeeinladung
  -> Follow-up nach Pax
```

## 5. App-Flow Mapping

| Operation | Screen / Flow | Primary Action | Secondary Actions | Fehler-/Abbruchfall |
|---|---|---|---|---|
| `op.app.open` | QR Landing, App Start, Install/Open Choice | App/Web-App starten | Pilotinfo lesen, native App installieren | App laedt nicht -> Infoseite oder Crew-Demo |
| `op.identity.create` | Onboarding: Create Identity | lokale ID erzeugen | bestehende ID verwenden, Recovery-Hinweis lesen | Abbruch -> kein Space-Beitritt |
| `op.space.join` | Space Invite Screen | Pax-Space beitreten | mehr Info, spaeter entscheiden | Ablehnen -> kein Makel, App bleibt nutzbar |
| `op.profile.create` | Profile Wizard | Rufname und erste Felder speichern | spaeter ausfuellen, Avatar setzen | Skip -> Profil bleibt minimal/anonym |
| `op.visibility.set` | Visibility Settings | Space-/Map-Sichtbarkeit waehlen | private bleiben, Region statt genauer Ort | keine Sichtbarkeit -> nicht auffindbar |
| `op.people.discover` | Map/List/Search | Profil/Eintrag oeffnen | filtern, merken, ausblenden | keine Treffer -> Crew/Agent kann analoge Einladung geben |
| `op.encounter.record` | Encounter Note / Event Context | Begegnung kontextualisieren | spaeter dokumentieren | nicht dokumentieren -> Beziehung kann trotzdem entstehen |
| `op.verification.create` | QR Challenge / Scanner | Begegnung bestaetigen | Gegenverifikation, manuelle Code-Eingabe | Fehler -> spaeter erneut versuchen |
| `op.offer.need.publish` | Profile or Marketplace Edit | Angebot/Beduerfnis eintragen | Tags, Sichtbarkeit, Ablaufdatum | leer lassen -> kein Druck |
| `op.quest.suggest` | Quest Suggestion Card | Einladung annehmen | ablehnen, spaeter, ausblenden | Ablehnung wird nicht negativ gewertet |
| `op.followup.create` | Follow-up View | Kontakt halten / naechsten Schritt speichern | Nachricht, lokaler Kreis, Event | kein Follow-up -> Beziehung bleibt als Kontakt |

## 6. Data Object Catalog

Diese Objekte beschreiben die fachliche Ebene. Eine Implementierung darf sie direkt als Item-Typen, als Felder bestehender Typen oder als abgeleitete Views umsetzen.

| Objekt | Zweck | Bestehendes Primitive | Gap / Empfehlung |
|---|---|---|---|
| `Identity` | lokale DID und Schluessel | WoT Identity | vorhanden |
| `DeviceState` | lokaler Onboarding-/Installationszustand | App-local storage | lokal, nicht Space-Daten |
| `SpaceInvite` | Einladung in Pax-Space | WoT space invite | vorhanden/zu stabilisieren |
| `SpaceMembership` | Mitgliedschaft im Pax-Space | WoT/RLS Group | vorhanden |
| `Profile` | Rufname, Bio, Avatar, Angebote, Beduerfnisse, Vision | RLS `profile` | Vision/Region/Sichtbarkeit ergaenzen |
| `VisibilityPreference` | private/space/public/map Sichtbarkeit | teilweise Profil-Feldsichtbarkeit | explizit modellieren |
| `MapMarker` | auffindbarer Ort/Profil/Eintrag | RLS `place` | Profil-/Offer-/Need-Marker klaeren |
| `Offer` | etwas, das jemand geben/teilen kann | Profil `offers[]` | P0 als Profilfeld, spaeter eigener Item-Typ |
| `Need` | etwas, das jemand sucht/braucht | Profil `needs[]` | P0 als Profilfeld, spaeter eigener Item-Typ |
| `Encounter` | Kontext einer realen Begegnung | none / event context | P1, optional |
| `VerificationClaim` | bestaetigte Begegnung/Identitaet | WoT SignedClaim / Attestation | vorhanden |
| `AttestationClaim` | Beitrag/Gabe/Faehigkeit attestieren | WoT SignedClaim / Attestation | P1 fuer Pax |
| `Quest` | freiwillige Einladung zu einer Handlung | none / task-like | eigener Typ empfohlen |
| `FollowUp` | naechster Schritt nach Begegnung/Festival | task/post/event | eigener leichter Typ oder Task |
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
    "bio": "Ich interessiere mich fuer Gemeinschaftsgaerten.",
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
    "title": "Lerne eine Person mit aehnlichem Interesse kennen",
    "operation": "op.people.discover",
    "intent": "relationship",
    "description": "Finde jemanden im Pax-Space, dessen Vision dich beruehrt, und fuehre ein echtes Gespraech.",
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

- `optional` MUSS fuer protokollkonforme Quests wahr sein.
- `status` DARF NICHT als Leistungsskala verwendet werden.
- `completion` DARF keine riskanten oder uebergriffigen Nachweise verlangen.

### 7.3 `offer` und `need`

P0 DARF Angebote und Beduerfnisse als Profilfelder abbilden. Sobald Suche, Verfuegbarkeit, Ablaufdatum oder mehrere Owner noetig werden, SOLLTEN sie eigene Items werden.

```json
{
  "type": "offer",
  "data": {
    "title": "Ich kann beim Kochen helfen",
    "description": "Gerne fuer Gemeinschaftsessen am Abend.",
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
| `locatedNear` | Profile/Offer/Need | Place/Region | ungefaehre raeumliche Naehe |
| `offeredBy` | Offer | Profile | Angebot gehoert zu Person/Agent |
| `neededBy` | Need | Profile | Beduerfnis gehoert zu Person/Agent |
| `metAt` | Encounter/Verification | Event/Place | Begegnungskontext |
| `verified` | VerificationClaim | Profile/Identity | bestaetigte Identitaetsbeziehung |
| `attests` | AttestationClaim | Profile/Identity | Aussage ueber Beitrag/Gabe/Faehigkeit |
| `suggestedTo` | Quest | Profile/Identity | Quest wurde vorgeschlagen |
| `relatedTo` | Item | Item | allgemeiner Bezug |
| `followUpFor` | FollowUp | Encounter/Event/Quest | Anschluss an vorherige Erfahrung |
| `documentedBy` | Event/Encounter/Project | Post/Media | Dokumentation eines Geschehens |

**Norm:** Relationen MUESSEN beschreiben, was passiert ist oder vorgeschlagen wird. Sie DUERFEN NICHT implizieren, dass ein Mensch wertvoller ist als ein anderer.

## 9. Claim Mapping

### 9.1 Verification Claim

Verifikation bestaetigt Begegnung oder Identitaetsbeziehung.

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

Attestations sind fuer Pax v0.1 nicht zwingend, aber anschlussfaehig.

```json
{
  "claim": "Mira hat beim gemeinsamen Abendessen fuer die Gruppe gekocht.",
  "tags": ["attestation", "contribution", "cooking", "pax-2026"],
  "from": "did:example:jonas",
  "to": "did:example:mira"
}
```

**Norm:** Attestations SOLLTEN konkret, beobachtbar und kontextbezogen sein.

## 10. Visibility Model

| Level | Bedeutung | Beispiel |
|---|---|---|
| `private` | nur lokal sichtbar | Entwurf, nicht veroeffentlicht |
| `contacts` | fuer verifizierte/aktive Kontakte sichtbar | Telefonnummer |
| `space` | im Pax-Space sichtbar | Angebot, Beduerfnis, Vision |
| `public` | oeffentlich sichtbar | freiwillige Profilseite |
| `region` | ungefaehre raeumliche Sichtbarkeit | "Leipzig" statt GPS |

**Normen:**

- Sichtbarkeit MUSS vor oder beim Veroeffentlichen erkennbar sein.
- Exakte Standortdaten DUERFEN NICHT Voraussetzung fuer Teilnahme sein.
- Eine Person MUSS Sichtbarkeit spaeter reduzieren koennen.

## 11. Quest Mapping

| Quest | Operation | Trigger | Completion | Agentenhilfe |
|---|---|---|---|---|
| App oeffnen | `op.app.open` | QR gescannt | App gestartet | Einstieg erklaeren |
| Eigene ID erzeugen | `op.identity.create` | keine ID vorhanden | DID vorhanden | Selbstbesitz erklaeren |
| Pax-Space beitreten | `op.space.join` | Invite erkannt | Mitgliedschaft aktiv | Sichtbarkeit erklaeren |
| Profil ergaenzen | `op.profile.create` | leeres Profil | Mindestfelder gesetzt | Formulierungsvorschlag |
| Angebot eintragen | `op.offer.need.publish` | Profil vorhanden | Offer sichtbar | Beispiele anbieten |
| Beduerfnis eintragen | `op.offer.need.publish` | Profil vorhanden | Need sichtbar | ermutigen, konkret zu werden |
| Person kennenlernen | `op.people.discover` | Matching-Signal | Begegnung selbst bestaetigt | passende Person vorschlagen |
| Verifizieren | `op.verification.create` | reale Begegnung | Claim erstellt | QR-Flow erklaeren |
| Naechsten Schritt speichern | `op.followup.create` | Begegnung/Match | Follow-up erstellt | lokale Anschlussoption |

## 12. Agent Support Contract

Ein Agent DARF:

- erklaeren, was gerade passiert,
- beim Formulieren von Profil, Angebot, Beduerfnis oder Vision helfen,
- passende Menschen, Orte, Ressourcen oder Events vorschlagen,
- Follow-ups erinnern,
- Crew und Hosts bei Nachbereitung unterstuetzen.

Ein Agent MUSS:

- Vorschlaege als Einladungen formulieren,
- Gruende fuer Vorschlaege nennen,
- Ablehnung und Nicht-Reaktion akzeptieren,
- Sichtbarkeit und Kontext respektieren,
- unsichere Annahmen als unsicher markieren.

Ein Agent DARF NICHT:

- Menschen ranken,
- Druck erzeugen,
- intime oder sensible Schluesse ohne explizite Grundlage ziehen,
- eine Verifikation, Attestation oder Einladung im Namen eines Menschen ohne Zustimmung ausloesen.

## 13. Metrics

Metriken sind Netzwerk-Signale, keine Leistungsbewertung.

| Metrik | Quelle | Zweck | Risiko |
|---|---|---|---|
| gestartete App-Sessions | `op.app.open` | Einstiegshuerden erkennen | Tracking-Uebergriff |
| erzeugte IDs | `op.identity.create` | Onboarding-Fortschritt | falsche Erfolgsmetrik |
| Pax-Space-Mitglieder | `op.space.join` | Pilotgroesse | Wachstum um jeden Preis |
| Profile mit Angeboten/Beduerfnissen | `op.offer.need.publish` | Kooperationspotential | Selbstvermarktungsdruck |
| Verifikationen | `op.verification.create` | reale Begegnungsdichte | Vertrauensmissverstaendnis |
| Follow-ups | `op.followup.create` | Anschlussfaehigkeit | soziale Kontrolle |
| Quests vorgeschlagen/angenommen | `op.quest.suggest` | Benutzerfuehrung verbessern | Gamification-Druck |

**Norm:** Metriken SOLLTEN aggregiert und kontextbezogen betrachtet werden. Sie DUERFEN NICHT als Score fuer Menschen verwendet werden.

## 14. MVP Implementation Notes

Fuer Pax v0.1 ist folgender pragmatischer Schnitt ausreichend:

1. `profile` erweitern statt sofort eigene `offer`/`need` Items erzwingen.
2. `space invite` und `group membership` fuer Pax-Space nutzen.
3. `SignedClaim` fuer Verifikation verwenden.
4. Quests zunaechst als lokale/sichtbare Suggestions abbilden, nicht als hartes Belohnungssystem.
5. Map in v0.1 darf eine Listen-/Regionenansicht sein, solange Begegnung und Auffindbarkeit funktionieren.
6. Metrics nur lokal/aggregiert fuer Pilot-Lernen verwenden.

## 15. Open Questions

- Werden `Offer` und `Need` fuer Pax eigene Items oder Profilfelder?
- Muss `Quest` bereits ein persistierter Item-Typ sein oder reicht eine abgeleitete Suggestion?
- Welche Sichtbarkeitsstufen unterstuetzt der erste App-Slice wirklich?
- Wie wird `region` ohne exakte Standortdaten erfasst?
- Wie werden analoge Kontakte ohne App nachtraeglich gemappt?
- Welche Daten darf ein Agent im Pax-Space standardmaessig sehen?
