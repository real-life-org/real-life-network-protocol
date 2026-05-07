# Pax Rollout Slice

**Status:** Entwurf v0.1
**Datum:** 2026-05-07
**Scope:** Minimaler sozialer und technischer Ablauf für Pax/Festival-Kontexte

---

## 1. Zweck

Dieser Slice beschreibt, welche minimalen sozialen Operationen auf Pax oder in vergleichbaren Festival-Kontexten zuverlässig funktionieren müssen.

Der Slice ist bewusst praktisch. Er beantwortet nicht alle Fragen des Real Life Network Protocols, sondern definiert den ersten realen Einsatzpfad:

> Eine Person kommt ans Vernetzungszelt, öffnet die App, erzeugt eine eigene Identität, tritt dem Pax-Space bei, wird sichtbar, begegnet Menschen, verifiziert Beziehungen und bleibt nach dem Festival verbunden.

## 2. Grundannahme

Der Pax-Space ist nicht der erste Schritt.

Bevor eine Person einem Space beitreten kann, MUSS sie:

1. die App oder Web-App öffnen können,
2. lokal eine eigene Identität erzeugen,
3. mindestens verstehen, dass diese Identität ihr gehört.

Erst danach DARF der Pax-Space-Beitritt stattfinden.

## 3. Nicht-Ziele

Dieser Slice implementiert nicht:

- vollständige Governance für Spaces,
- komplexe Commons-Verwaltung,
- fortgeschrittene Agenten-Automation,
- vollständige DIDComm-/SSI-Interop,
- ausgereifte Jugend-/Kinderschutz-Flows,
- vollständige Recovery- und Multi-Device-UX.

## 4. Minimaler Happy Path

### 4.1 Einladung / Einstieg

**Situation:** Eine Person steht am Vernetzungszelt oder sieht einen QR-Code.

**Ablauf:**

1. Person scannt QR-Code oder öffnet einen Link.
2. Der Link führt zur App/Web-App oder zu einer Installationsseite.
3. Die Person bekommt eine kurze, ehrliche Pilot-Erklärung.

**Output:** App-Zugang ist gestartet.

**Norm:** Der Einstieg MUSS ohne technisches Vorwissen möglich sein.

### 4.2 App laden oder öffnen

**Zweck:** Die Person braucht eine laufende App-Umgebung.

**Ablauf:**

1. Wenn die App schon vorhanden ist, wird sie geöffnet.
2. Wenn keine App vorhanden ist, wird die Web-App oder Installationsoption angeboten.
3. Die App prüft, ob bereits eine lokale Identität existiert.

**Output:** App läuft auf dem Gerät.

**Risiken:** schlechtes Netz, alte Browser, App-Installationshürden, kein Speicherplatz, Kamera-Berechtigung fehlt.

### 4.3 Lokale Identität erzeugen

**Zweck:** Die Person braucht eine eigene dezentrale Identität, bevor sie einem Space beitreten oder verifiziert werden kann.

**Ablauf:**

1. App erzeugt lokale Schlüssel und DID.
2. App erklärt knapp: "Diese Identität gehört dir und bleibt auf deinem Gerät."
3. App fragt nur nach dem minimal nötigen Schutz- oder Recovery-Schritt für den Pilotkontext.

**Output:** Lokale Identität ist vorhanden.

**Normen:**

- Identität MUSS vor Space-Beitritt erzeugt werden.
- Identität DARF NICHT an eine zentrale Registrierung gekoppelt sein.
- Die UX MUSS deutlich machen, dass der Space-Beitritt nicht die Identität erzeugt, sondern die vorhandene Identität in einen Raum einlädt.

### 4.4 Pax-Space beitreten

**Zweck:** Die Person landet in dem gemeinsamen digitalen Raum für den Festival-Kontext.

**Inputs:** lokale Identität, Pax-Space-Einladung, ggf. Space-Key oder Invite-Token.

**Ablauf:**

1. App erkennt den Pax-Space-Invite aus QR-Code oder Link.
2. Person sieht: "Du trittst dem Pax-Space bei."
3. Person bestätigt freiwillig.
4. App speichert Space-Mitgliedschaft und nötige Space-Daten.

**Output:** Person ist Mitglied des Pax-Space.

**Normen:**

- Space-Beitritt MUSS freiwillig bestätigt werden.
- Nicht-Beitritt DARF nicht als Fehler oder sozialer Makel dargestellt werden.
- Die Person SOLLTE auch verstehen, welche Inhalte im Space sichtbar werden können.

### 4.5 Minimalprofil anlegen

**Zweck:** Andere Menschen können die Person wiedererkennen und ansprechen.

**Minimalfelder:**

- Name oder Rufname
- optional Avatar/Bild
- kurzer Satz: "Was bewegt mich?"
- Angebote
- Bedürfnisse
- Vision oder Interesse
- optional Region/Ort

**Output:** Profil ist im Pax-Space sichtbar, soweit die Person zustimmt.

**Normen:**

- Profilfelder SOLLTEN optional bleiben, außer ein Feld ist für den Flow zwingend.
- Sichtbarkeit MUSS erklärt und änderbar sein.

### 4.6 Auf Karte oder Liste sichtbar werden

**Zweck:** Begegnung wird wahrscheinlicher, weil Menschen, Interessen, Angebote und Bedürfnisse auffindbar werden.

**Ablauf:**

1. Person entscheidet, ob und wie sie sichtbar sein will.
2. App kann eine ungefähre Region, einen Festival-Ort oder keinen Ort verwenden.
3. Angebote, Bedürfnisse und Interessen werden filterbar.

**Output:** Person oder Profil ist im Pax-Kontext auffindbar.

**Norm:** Exakte Standortdaten DÜRFEN NICHT erzwungen werden.

### 4.7 Menschen kennenlernen

**Zweck:** Der digitale Raum führt in reale Begegnung.

**Ablauf:**

1. Person sieht passende Menschen, Angebote, Bedürfnisse, Orte oder Programmpunkte.
2. App, Crew oder Agent kann eine leichte Einladung vorschlagen.
3. Begegnung findet analog statt.

**Output:** Neue Beziehung oder Kontaktmöglichkeit.

### 4.8 Menschen verifizieren

**Zweck:** Eine reale Begegnung wird per QR-Verifikation im Netzwerk festgehalten und als Identitätsbeziehung bestätigt.

**Ablauf:**

1. Zwei Menschen begegnen sich.
2. Eine Person zeigt QR-Code oder Challenge.
3. Die andere scannt und bestätigt.
4. Optional erfolgt Gegenbestätigung.

**Output:** Verifizierte Beziehung.

**Norm:** Verifikation bestätigt Begegnung/Identität, nicht globale Vertrauenswürdigkeit. Eine Begegnung braucht keine separate `op.encounter.record`-Operation; sobald sie digital festgehalten werden soll, geschieht das durch QR-Verifikation.

### 4.9 Angebote, Bedürfnisse und Visionen entdecken

**Zweck:** Aus Begegnung können konkrete nächste Schritte entstehen.

**Ablauf:**

1. Person durchsucht oder sieht Profile, Angebote und Bedürfnisse im Pax-Space.
2. App oder Agent schlägt passende, freiwillige nächste Schritte vor.
3. Menschen können sich treffen, helfen, Ressourcen teilen oder Projekte anstoßen.

**Output:** mögliche Kooperation, Einladung, Ressourcenteilen oder Projektidee.

### 4.10 Nach dem Festival verbunden bleiben

**Zweck:** Pax erzeugt nicht nur Festivalkontakte, sondern lokale Anschlussfähigkeit.

**Ablauf:**

1. Person sieht nach dem Festival ihre Kontakte, Verifikationen und Pax-Space-Verbindungen.
2. App oder Agent schlägt lokale oder thematische nächste Schritte vor.
3. Crew kann Follow-up-Nachrichten, regionale Kreise oder Projektideen dokumentieren.

**Output:** Beziehungen überdauern den Festivalkontext.

## 5. P0-Operationen im Pax-Slice

| Reihenfolge | Operation | Muss funktionieren, wenn... | Minimaler Output |
|---|---|---|---|
| 1 | App laden/öffnen | Person scannt Stand-QR oder öffnet Link | App/Web-App läuft |
| 2 | Identität erzeugen | keine lokale ID vorhanden ist | DID/Schlüssel lokal erzeugt |
| 3 | Pax-Space beitreten | lokale ID vorhanden und Invite gültig ist | Space-Mitgliedschaft |
| 4 | Profil anlegen | Person im Space ansprechbar sein will | Minimalprofil |
| 5 | Sichtbarkeit setzen | Person gefunden werden will | Map-/Listen-/Profil-Sichtbarkeit |
| 6 | Menschen kennenlernen | passende Personen oder Interessen sichtbar sind | Begegnung oder Kontakt |
| 7 | Menschen verifizieren | reale Begegnung stattgefunden hat | Verification-Attestation als VC-JWS |
| 8 | Angebote/Bedürfnisse teilen | Person beitragen oder fragen will | Offer-/Need-Tags im Profil |
| 9 | Nächsten Schritt finden | genug Kontext für Einladung existiert | Quest-Item, Einladung oder Follow-up |
| 10 | Verbunden bleiben | Festival vorbei ist | Kontakte, regionale Anschlussoption |

## 6. Operation-to-App-Mapping v0.1

Das detaillierte Daten- und App-Mapping lebt in [../06-data-model/operations-mapping.md](../06-data-model/operations-mapping.md).

| Operation | App-Flow | Datenobjekte | Agentenhilfe | Metrik |
|---|---|---|---|---|
| App laden/öffnen | QR -> Web/App -> Startscreen | none / install state | erklärt Pilot und Einstieg | gestartete Sessions |
| Identität erzeugen | Onboarding -> Generate ID | DID, key material, device state | erklärt Selbstbesitz der ID | erzeugte IDs |
| Pax-Space beitreten | Invite screen -> accept | space invite, membership | erklärt Space und Sichtbarkeit | Space-Mitglieder |
| Profil anlegen | Profile wizard | profile item | hilft beim Formulieren | Profile mit Mindestfeldern |
| Sichtbarkeit setzen | Visibility screen | profile visibility, map marker | erklärt Optionen | sichtbare Profile/Marker |
| Menschen kennenlernen | Map/List/Profile browse | profile, relation hint | schlägt passende Begegnungen vor | neue Kontakte |
| Verifizieren | QR challenge/scan | Verification-Attestation VC-JWS | erklärt Unterschied zu Vertrauen | Verifikationen |
| Angebote/Bedürfnisse teilen | Profile/Marketplace edit | profile `offers[]`/`needs[]` tags | erkennt passende Matches | Offer-/Need-Tags |
| Nächsten Schritt finden | Quest suggestion | generisches Quest-Item, relation, event | macht Einladungsvorschläge | angenommene Einladungen |
| Verbunden bleiben | Follow-up view | contacts, attestations, events | schlägt regionale Anschlussoptionen vor | Follow-ups |

## 7. Stand-Crew-Unterstützung

Die Stand-Crew SOLLTE für jede Phase eine einfache Antwort haben:

- "Was ist das?" -> Ein Netzwerk für echte Begegnung, lokale Gemeinschaft und geteilte Ressourcen.
- "Warum brauche ich eine ID?" -> Damit deine Beziehungen und Daten dir gehören und nicht einem zentralen Konto.
- "Was ist der Pax-Space?" -> Der gemeinsame digitale Raum für Menschen, Begegnungen und Angebote auf diesem Festival.
- "Was ist sichtbar?" -> Nur das, was du einträgst und sichtbar machst.
- "Muss ich mitmachen?" -> Nein. Es ist eine Einladung.

## 8. Fallbacks

| Problem | Fallback |
|---|---|
| Kein Netz | App lokal vorbereiten, später syncen; analog Kontakt notieren |
| App lädt nicht | QR zu Infoseite, Crew-Gerät für Demo, Papierkarte |
| Kamera geht nicht | Code manuell eingeben |
| Person will keine App | analog vernetzen, später Link senden |
| ID wurde schon erstellt | bestehende ID verwenden, nicht neu erzeugen |
| Recovery zu schwer | minimaler Pilot-Hinweis, später vertiefen |
| Person will nicht sichtbar sein | Space beitreten ohne Map-/Profil-Öffentlichkeit |

## 9. Erste Quests im Pax-Slice

Diese Quests sind freiwillige Einladungen:

1. Öffne die App.
2. Erzeuge deine eigene ID.
3. Tritt dem Pax-Space bei.
4. Ergänze dein Profil mit einem Satz, der dich bewegt.
5. Trage ein Angebot ein.
6. Trage ein Bedürfnis ein.
7. Finde eine Person mit ähnlichem Interesse.
8. Führe ein echtes Gespräch.
9. Verifiziert euch gegenseitig.
10. Lade jemanden zu einem Kreis, Essen oder Feuer ein.
11. Dokumentiere ein Learning vom Festival.
12. Finde nach Pax eine lokale Anschlussmöglichkeit.

## 10. Definition of Done für Pax v0.1

Pax v0.1 ist rollout-ready, wenn:

- eine fremde Person per QR in die App kommt,
- ohne Vorwissen eine lokale Identität erzeugen kann,
- dem Pax-Space freiwillig beitreten kann,
- ein Minimalprofil anlegen kann,
- sichtbar oder bewusst unsichtbar bleiben kann,
- mindestens eine andere Person finden und verifizieren kann,
- Angebot, Bedürfnis oder Vision ausdrücken kann,
- nach dem Festival ihre Kontakte und nächsten Schritte wiederfindet,
- die Stand-Crew den gesamten Flow erklären und bei Fehlern auffangen kann.

## 11. Offene Fragen

- Ist der primäre Einstieg Web-App, native App, F-Droid oder eine Auswahlseite?
- Wie viel Recovery ist im Festival-Onboarding zumutbar?
- Muss ein Minimalprofil vor Space-Beitritt existieren oder reicht ein späterer Profil-Step?
- Welche Felder sind im Pax-Space öffentlich, space-intern oder privat?
- Wie wird der Pax-Space vorbefüllt?
- Wie werden analoge Kontakte nachträglich in digitale Verbindungen überführt?
