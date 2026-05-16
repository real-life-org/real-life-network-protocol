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

Eine Quest DARF NICHT global als `completed` gelten, nur weil eine Person sie abgeschlossen hat. `completed`, `evidence-submitted`, `attestation-requested` oder `attested` beschreibt immer einen konkreten QuestRun, nicht die Quest als solche.

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
| `completed` | Abschluss wurde lokal markiert. |
| `evidence-submitted` | Eine Spur oder ein Selbst-Claim wurde eingereicht, aber noch nicht attestiert. |
| `attestation-requested` | Eine Attestation wurde angefragt, z.B. bei Host, Gruppe, Mentor oder System. |
| `attested` | Es gibt mindestens eine gültige WoT-Attestation, die diesen QuestRun oder Beitrag belegt. |
| `abandoned` | Begonnen, aber bewusst nicht weitergeführt. |

Nicht jede Umsetzung muss alle Status explizit speichern. Für Pax v0.1 reichen lokale Vorschläge und einfache Abschlusszustände, solange klar bleibt:

- Vorschlag, Annahme, lokale Completion, Evidence und Attestations gehören zum QuestRun.
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
- Completion, Evidence und Attestations beziehen sich auf den QuestRun.
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
| `data.requiredEvidence[]` | optional | Evidence, die für eine Attestation nötig oder empfohlen ist |
| `data.attestationPolicy` | optional | Regeln, welche Attestations als gültige Completion für diese Quest zählen |
| `data.completionAttestationTemplate` | optional | Claim- und Display-Vorlage für spätere Completion-Attestations |
| `data.safetyRequirements[]` | optional | Sicherheits-, Alters-, Begleitungs-, Sichtbarkeits- oder Kontextregeln |

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
    "requiredEvidence": [
      {
        "type": "self-claim",
        "required": false,
        "label": "Kurze Notiz, mit wem das Gespräch geführt wurde."
      }
    ],
    "attestationPolicy": {
      "allowedAttesters": [
        { "role": "peer", "minCount": 1 },
        { "role": "host" }
      ]
    },
    "completionAttestationTemplate": {
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
    ],
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

**Normen:**

- `requiredEvidence` beschreibt, welche Spur für eine spätere Attestation nötig oder hilfreich ist. Evidence ist noch kein portabler Beleg.
- `attestationPolicy` beschreibt, welche Attestations für diesen QuestRun als gültige Completion zählen. Das Web of Trust bleibt offen: Andere Menschen können trotzdem Attestations ausstellen, sie zählen dann aber nicht automatisch als Quest-Completion.
- `completionAttestationTemplate` ist eine Vorlage für Completion-Attestations. Die tatsächlich portable Anerkennung entsteht erst durch die signierte Attestation.
- `safetyRequirements` MÜSSEN vor oder während der Quest verständlich sichtbar sein, wenn sie für Teilnahme, Evidence oder Attestation relevant sind.

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
| `data.completion.claimedAt` | optional | Zeitpunkt der lokalen Completion oder Selbstmarkierung |
| `data.completion.evidence` | optional | eingereichte Spur, z.B. Foto, Text, QR-Scan, Dokumentation oder Systemereignis |
| `data.completion.attestationRequestedAt` | optional | Zeitpunkt, an dem eine Attestation angefragt wurde |
| `data.location` | optional | Ort oder Region der Durchführung |
| `data.time` | optional | Zeitpunkt, Zeitraum oder Phase der Durchführung |

Erforderliche Relations:

| Predicate | Ziel | Bedeutung |
|---|---|---|
| `runsQuest` | Quest | Run gehört zu dieser Quest |
| `actor` | Profile/Identity | Mensch, der den Run ausführt |

Optionale Kontext-Relations entsprechen der Quest: `partOf`, `locatedAt`, `locatedNear`.

Attestations, die einen QuestRun oder einen Beitrag belegen, SOLLTEN als eigene WoT-Attestation bzw. Attestation-View modelliert werden und per `attests`-Relation auf den QuestRun, den Beitrag oder das Ergebnis zeigen.

```json
{
  "id": "quest-run:pax:meet-similar-interest:mira",
  "type": "quest-run",
  "createdAt": "2026-05-07T10:06:00Z",
  "createdBy": "did:key:z6Mk...mira",
  "schema": "rlnp:quest-run",
  "schemaVersion": 1,
  "data": {
    "status": "evidence-submitted",
    "visibility": {
      "mode": "private"
    },
    "completion": {
      "claimedAt": "2026-05-07T10:20:00Z",
      "evidence": {
        "type": "self-claim",
        "summary": "Mira hat das Gespräch lokal als erledigt markiert."
      }
    }
  },
  "relations": [
    { "predicate": "runsQuest", "target": "item:quest:pax:meet-similar-interest" },
    { "predicate": "actor", "target": "global:did:key:z6Mk...mira" }
  ]
}
```

Diese Mindestfelder helfen Apps, Agenten und RLS-Connectoren dabei, Quest-Definition, persönliche Durchführung, Sichtbarkeit und Completion nicht zu vermischen.

## 10. Completion, Evidence und Attestation

Quest-Abschluss meint immer den Abschluss eines konkreten QuestRuns. Das Protokoll unterscheidet drei Ebenen:

| Ebene | Bedeutung |
|---|---|
| Lokale Completion | Die ausführende Person oder App markiert, dass ein QuestRun für sie abgeschlossen ist. |
| Evidence | Eine Spur oder ein Selbst-Claim wird eingereicht, z.B. Foto, Text, QR-Scan, Dokumentation oder Systemereignis. |
| Attestation | Eine signierte WoT-Attestation bestätigt eine konkrete Aussage über QuestRun, Beitrag, Rolle, Teilnahme oder Ergebnis. |

Eine lokale Completion und eingereichte Evidence sind noch kein portabler Beleg. Ein QuestRun gilt nur dann als belegte oder portable Completion, wenn mindestens eine gültige WoT-Attestation existiert, die auf den QuestRun, den Beitrag oder das Ergebnis verweist.

### 10.1 Evidence-Arten

Evidence kann je nach Quest unterschiedlich aussehen:

| Evidence-Art | Bedeutung |
|---|---|
| `self-claim` | Person erklärt lokal, dass sie etwas getan hat. |
| `text` | Textnotiz oder Reflexion. |
| `media` | Foto, Video oder Audio. |
| `qr-scan` | QR-Scan als Spur einer realen Begegnung, Teilnahme oder eines Check-ins. |
| `system-event` | App oder System hat ein Ereignis beobachtet. |
| `external-document` | Link oder Verweis auf externes Dokument. |

Evidence ist eine Einladung zur Prüfung oder Erinnerung. Sie DARF NICHT automatisch als öffentliche Wahrheit, portable Anerkennung oder Badge behandelt werden.

### 10.2 Attester

Eine Attestation kann aus verschiedenen Rollen kommen:

| Attester | Bedeutung |
|---|---|
| Host | Host, Crew, Lehrkraft, Mentor oder Veranstalter bestätigt eine beobachtete Handlung. |
| Peer oder Gruppe | Beteiligte bestätigen einander oder einen gemeinsamen Beitrag. |
| Expert:in | Eine Person mit anerkannter fachlicher Rolle bestätigt eine Fähigkeit oder ein Ergebnis. |
| System oder Agent | Eine erkennbare System- oder Agenten-DID attestiert nach nachvollziehbarer Regel. |

Die konkreten Regeln, welche Attestations für die Completion einer Quest zählen, KÖNNEN in `data.attestationPolicy` stehen. Die Basisnorm bleibt: Attestations MÜSSEN konkret, beobachtbar, signiert und kontextbezogen sein.

### 10.3 Attestation Policy

Eine Quest KANN eine `attestationPolicy` definieren. Diese Policy begrenzt nicht, wer im Web of Trust eine Attestation ausstellen darf. Sie beschreibt nur, welche Attestations für diesen QuestRun als gültige Quest-Completion gelten.

```json
{
  "attestationPolicy": {
    "allowedAttesters": [
      { "role": "host" },
      { "role": "peer", "minCount": 2 },
      { "role": "system", "ruleId": "pax-qr-checkin" }
    ],
    "requiresAcceptedEvidence": true
  }
}
```

`allowedAttesters.role` ist ein Kontextbegriff. Häufige Rollen sind `host`, `peer`, `group`, `mentor`, `expert`, `system`, `agent` oder `issuer`. Ein konkreter Space, eine Veranstaltung, ein Projekt, eine Schule oder ein Host-Tool kann diese Rollen auf DIDs, Gruppen oder Issuer-Listen abbilden.

### 10.4 Required Evidence

Eine Quest KANN `requiredEvidence` definieren. Diese Anforderungen beschreiben, welche Evidence eingereicht werden muss oder empfohlen ist, bevor eine Attestation angefragt oder ausgestellt wird.

```json
{
  "requiredEvidence": [
    {
      "type": "media",
      "required": true,
      "label": "Foto des fertigen Werkstücks"
    },
    {
      "type": "text",
      "required": false,
      "label": "Kurze Reflexion: Was war schwierig?"
    }
  ]
}
```

Evidence-Anforderungen DÜRFEN keine riskanten, beschämenden oder übergriffigen Nachweise verlangen.

### 10.5 Completion Attestation Template

Eine Quest KANN eine `completionAttestationTemplate` definieren. Sie beschreibt, welche Claim- und Display-Vorlage eine gültige Completion-Attestation verwenden soll.

```json
{
  "completionAttestationTemplate": {
    "claim": "{actor} hat den Hochbeet-Rahmen verschraubt.",
    "display": {
      "label": "Rahmen verschraubt",
      "color": "#8B5A2B",
      "shape": "circle"
    }
  }
}
```

Die Vorlage selbst ist kein Badge. Erst eine signierte WoT-Attestation mit dieser oder einer daraus abgeleiteten Darstellung kann als portable Badge-View erscheinen.

### 10.6 Safety Requirements

Eine Quest KANN `safetyRequirements` definieren. Diese Anforderungen beschreiben Sicherheits-, Alters-, Begleitungs-, Sichtbarkeits- oder Kontextregeln.

```json
{
  "safetyRequirements": [
    {
      "type": "tool",
      "required": true,
      "label": "Akkuschrauber nur nach Einweisung nutzen."
    },
    {
      "type": "supervision",
      "required": true,
      "label": "Für Minderjährige nur mit erwachsener Begleitung."
    }
  ]
}
```

Häufige Typen sind `age`, `tool`, `place`, `supervision`, `consent`, `visibility`, `privacy`, `legal` und `cost`. Apps SOLLTEN diese Regeln vor Annahme der Quest sichtbar machen.

### 10.7 Normen

- Öffentliche, portable oder Badge-relevante Completion MUSS über WoT-Attestations laufen.
- Ein Selbst-Claim oder eine hochgeladene Spur ist keine Self-Attestation.
- Foto-, Video- oder Textdokumentation ist zunächst Evidence und kann andere zur Attestation einladen.
- QR-Scans, Host-Bestätigungen, gegenseitige Bestätigungen und Systemereignisse sind keine eigenen Wahrheitsarten; sie sind Evidence, Trigger oder Issuer-Rollen für Attestations.
- Eine System- oder Agenten-Attestation MUSS eine erkennbare DID, eine nachvollziehbare Regel und einen auslösenden Trigger haben.
- Completion-Daten, Evidence und Attestations MÜSSEN Sichtbarkeit, Zustimmung und Kontext respektieren.
- `attestationPolicy`, `requiredEvidence`, `completionAttestationTemplate` und `safetyRequirements` gehören zur Quest-Completion-Logik des Basisprotokolls. Sie sind keine Game-Mechaniken.

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

Ein Badge entsteht durch eine WoT-Attestation:

- ausgestellt durch eine menschliche Identität,
- ausgestellt durch eine Agenten-Identität,
- ausgestellt durch eine System-Identität.

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
