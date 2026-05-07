# Pax Rollout Slice

**Status:** Entwurf v0.1
**Datum:** 2026-05-07
**Scope:** Minimaler sozialer und technischer Ablauf fuer Pax/Festival-Kontexte

---

## 1. Zweck

Dieser Slice beschreibt, welche minimalen sozialen Operationen auf Pax oder in vergleichbaren Festival-Kontexten zuverlaessig funktionieren muessen.

Der Slice ist bewusst praktisch. Er beantwortet nicht alle Fragen des Real Life Network Protocols, sondern definiert den ersten realen Einsatzpfad:

> Eine Person kommt ans Vernetzungszelt, oeffnet die App, erzeugt eine eigene Identitaet, tritt dem Pax-Space bei, wird sichtbar, begegnet Menschen, verifiziert Beziehungen und bleibt nach dem Festival verbunden.

## 2. Grundannahme

Der Pax-Space ist nicht der erste Schritt.

Bevor eine Person einem Space beitreten kann, MUSS sie:

1. die App oder Web-App oeffnen koennen,
2. lokal eine eigene Identitaet erzeugen,
3. mindestens verstehen, dass diese Identitaet ihr gehoert.

Erst danach DARF der Pax-Space-Beitritt stattfinden.

## 3. Nicht-Ziele

Dieser Slice implementiert nicht:

- vollstaendige Governance fuer Spaces,
- komplexe Commons-Verwaltung,
- fortgeschrittene Agenten-Automation,
- vollstaendige DIDComm-/SSI-Interop,
- ausgereifte Jugend-/Kinderschutz-Flows,
- vollstaendige Recovery- und Multi-Device-UX.

## 4. Minimaler Happy Path

### 4.1 Einladung / Einstieg

**Situation:** Eine Person steht am Vernetzungszelt oder sieht einen QR-Code.

**Ablauf:**

1. Person scannt QR-Code oder oeffnet einen Link.
2. Der Link fuehrt zur App/Web-App oder zu einer Installationsseite.
3. Die Person bekommt eine kurze, ehrliche Pilot-Erklaerung.

**Output:** App-Zugang ist gestartet.

**Norm:** Der Einstieg MUSS ohne technisches Vorwissen moeglich sein.

### 4.2 App laden oder oeffnen

**Zweck:** Die Person braucht eine laufende App-Umgebung.

**Ablauf:**

1. Wenn die App schon vorhanden ist, wird sie geoeffnet.
2. Wenn keine App vorhanden ist, wird die Web-App oder Installationsoption angeboten.
3. Die App prueft, ob bereits eine lokale Identitaet existiert.

**Output:** App laeuft auf dem Geraet.

**Risiken:** schlechtes Netz, alte Browser, App-Installationshuerden, kein Speicherplatz, Kamera-Berechtigung fehlt.

### 4.3 Lokale Identitaet erzeugen

**Zweck:** Die Person braucht eine eigene dezentrale Identitaet, bevor sie einem Space beitreten oder verifiziert werden kann.

**Ablauf:**

1. App erzeugt lokale Schluessel und DID.
2. App erklaert knapp: "Diese Identitaet gehoert dir und bleibt auf deinem Geraet."
3. App fragt nur nach dem minimal noetigen Schutz- oder Recovery-Schritt fuer den Pilotkontext.

**Output:** Lokale Identitaet ist vorhanden.

**Normen:**

- Identitaet MUSS vor Space-Beitritt erzeugt werden.
- Identitaet DARF NICHT an eine zentrale Registrierung gekoppelt sein.
- Die UX MUSS deutlich machen, dass der Space-Beitritt nicht die Identitaet erzeugt, sondern die vorhandene Identitaet in einen Raum einlaedt.

### 4.4 Pax-Space beitreten

**Zweck:** Die Person landet in dem gemeinsamen digitalen Raum fuer den Festival-Kontext.

**Inputs:** lokale Identitaet, Pax-Space-Einladung, ggf. Space-Key oder Invite-Token.

**Ablauf:**

1. App erkennt den Pax-Space-Invite aus QR-Code oder Link.
2. Person sieht: "Du trittst dem Pax-Space bei."
3. Person bestaetigt freiwillig.
4. App speichert Space-Mitgliedschaft und noetige Space-Daten.

**Output:** Person ist Mitglied des Pax-Space.

**Normen:**

- Space-Beitritt MUSS freiwillig bestaetigt werden.
- Nicht-Beitritt DARF nicht als Fehler oder sozialer Makel dargestellt werden.
- Die Person SOLLTE auch verstehen, welche Inhalte im Space sichtbar werden koennen.

### 4.5 Minimalprofil anlegen

**Zweck:** Andere Menschen koennen die Person wiedererkennen und ansprechen.

**Minimalfelder:**

- Name oder Rufname
- optional Avatar/Bild
- kurzer Satz: "Was bewegt mich?"
- Angebote
- Beduerfnisse
- Vision oder Interesse
- optional Region/Ort

**Output:** Profil ist im Pax-Space sichtbar, soweit die Person zustimmt.

**Normen:**

- Profilfelder SOLLTEN optional bleiben, ausser ein Feld ist fuer den Flow zwingend.
- Sichtbarkeit MUSS erklaert und aenderbar sein.

### 4.6 Auf Karte oder Liste sichtbar werden

**Zweck:** Begegnung wird wahrscheinlicher, weil Menschen, Interessen, Angebote und Beduerfnisse auffindbar werden.

**Ablauf:**

1. Person entscheidet, ob und wie sie sichtbar sein will.
2. App kann eine ungefaehre Region, einen Festival-Ort oder keinen Ort verwenden.
3. Angebote, Beduerfnisse und Interessen werden filterbar.

**Output:** Person oder Profil ist im Pax-Kontext auffindbar.

**Norm:** Exakte Standortdaten DUERFEN NICHT erzwungen werden.

### 4.7 Menschen kennenlernen

**Zweck:** Der digitale Raum fuehrt in reale Begegnung.

**Ablauf:**

1. Person sieht passende Menschen, Angebote, Beduerfnisse, Orte oder Programmpunkte.
2. App, Crew oder Agent kann eine leichte Einladung vorschlagen.
3. Begegnung findet analog statt.

**Output:** Neue Beziehung oder Kontaktmoeglichkeit.

### 4.8 Menschen verifizieren

**Zweck:** Eine reale Begegnung wird als Identitaetsbeziehung bestaetigt.

**Ablauf:**

1. Zwei Menschen begegnen sich.
2. Eine Person zeigt QR-Code oder Challenge.
3. Die andere scannt und bestaetigt.
4. Optional erfolgt Gegenbestaetigung.

**Output:** Verifizierte Beziehung.

**Norm:** Verifikation bestaetigt Begegnung/Identitaet, nicht globale Vertrauenswuerdigkeit.

### 4.9 Angebote, Beduerfnisse und Visionen entdecken

**Zweck:** Aus Begegnung koennen konkrete naechste Schritte entstehen.

**Ablauf:**

1. Person durchsucht oder sieht Profile, Angebote und Beduerfnisse im Pax-Space.
2. App oder Agent schlaegt passende, freiwillige naechste Schritte vor.
3. Menschen koennen sich treffen, helfen, Ressourcen teilen oder Projekte anstossen.

**Output:** moegliche Kooperation, Einladung, Ressourcenteilen oder Projektidee.

### 4.10 Nach dem Festival verbunden bleiben

**Zweck:** Pax erzeugt nicht nur Festivalkontakte, sondern lokale Anschlussfaehigkeit.

**Ablauf:**

1. Person sieht nach dem Festival ihre Kontakte, Verifikationen und Pax-Space-Verbindungen.
2. App oder Agent schlaegt lokale oder thematische naechste Schritte vor.
3. Crew kann Follow-up-Nachrichten, regionale Kreise oder Projektideen dokumentieren.

**Output:** Beziehungen ueberdauern den Festivalkontext.

## 5. P0-Operationen im Pax-Slice

| Reihenfolge | Operation | Muss funktionieren, wenn... | Minimaler Output |
|---|---|---|---|
| 1 | App laden/oeffnen | Person scannt Stand-QR oder oeffnet Link | App/Web-App laeuft |
| 2 | Identitaet erzeugen | keine lokale ID vorhanden ist | DID/Schluessel lokal erzeugt |
| 3 | Pax-Space beitreten | lokale ID vorhanden und Invite gueltig ist | Space-Mitgliedschaft |
| 4 | Profil anlegen | Person im Space ansprechbar sein will | Minimalprofil |
| 5 | Sichtbarkeit setzen | Person gefunden werden will | Map-/Listen-/Profil-Sichtbarkeit |
| 6 | Menschen kennenlernen | passende Personen oder Interessen sichtbar sind | Begegnung oder Kontakt |
| 7 | Menschen verifizieren | reale Begegnung stattgefunden hat | Verification Claim |
| 8 | Angebote/Beduerfnisse teilen | Person beitragen oder fragen will | Offer/Need im Profil oder Space |
| 9 | Naechsten Schritt finden | genug Kontext fuer Einladung existiert | Quest, Einladung oder Follow-up |
| 10 | Verbunden bleiben | Festival vorbei ist | Kontakte, regionale Anschlussoption |

## 6. Operation-to-App-Mapping v0.1

| Operation | App-Flow | Datenobjekte | Agentenhilfe | Metrik |
|---|---|---|---|---|
| App laden/oeffnen | QR -> Web/App -> Startscreen | none / install state | erklaert Pilot und Einstieg | gestartete Sessions |
| Identitaet erzeugen | Onboarding -> Generate ID | DID, key material, device state | erklaert Selbstbesitz der ID | erzeugte IDs |
| Pax-Space beitreten | Invite screen -> accept | space invite, membership | erklaert Space und Sichtbarkeit | Space-Mitglieder |
| Profil anlegen | Profile wizard | profile item | hilft beim Formulieren | Profile mit Mindestfeldern |
| Sichtbarkeit setzen | Visibility screen | profile visibility, map marker | erklaert Optionen | sichtbare Profile/Marker |
| Menschen kennenlernen | Map/List/Profile browse | profile, relation hint | schlaegt passende Begegnungen vor | neue Kontakte |
| Verifizieren | QR challenge/scan | verification claim | erklaert Unterschied zu Vertrauen | Verifikationen |
| Angebote/Beduerfnisse teilen | Profile/Marketplace edit | offer, need, tags | erkennt passende Matches | Offers/Needs |
| Naechsten Schritt finden | Quest suggestion | quest, relation, event | macht Einladungsvorschlaege | angenommene Einladungen |
| Verbunden bleiben | Follow-up view | contacts, attestations, events | schlaegt regionale Anschlussoptionen vor | Follow-ups |

## 7. Stand-Crew-Unterstuetzung

Die Stand-Crew SOLLTE fuer jede Phase eine einfache Antwort haben:

- "Was ist das?" -> Ein Netzwerk fuer echte Begegnung, lokale Gemeinschaft und geteilte Ressourcen.
- "Warum brauche ich eine ID?" -> Damit deine Beziehungen und Daten dir gehoeren und nicht einem zentralen Konto.
- "Was ist der Pax-Space?" -> Der gemeinsame digitale Raum fuer Menschen, Begegnungen und Angebote auf diesem Festival.
- "Was ist sichtbar?" -> Nur das, was du eintraegst und sichtbar machst.
- "Muss ich mitmachen?" -> Nein. Es ist eine Einladung.

## 8. Fallbacks

| Problem | Fallback |
|---|---|
| Kein Netz | App lokal vorbereiten, spaeter syncen; analog Kontakt notieren |
| App laedt nicht | QR zu Infoseite, Crew-Geraet fuer Demo, Papierkarte |
| Kamera geht nicht | Code manuell eingeben |
| Person will keine App | analog vernetzen, spaeter Link senden |
| ID wurde schon erstellt | bestehende ID verwenden, nicht neu erzeugen |
| Recovery zu schwer | minimaler Pilot-Hinweis, spaeter vertiefen |
| Person will nicht sichtbar sein | Space beitreten ohne Map-/Profil-Oeffentlichkeit |

## 9. Erste Quests im Pax-Slice

Diese Quests sind freiwillige Einladungen:

1. Oeffne die App.
2. Erzeuge deine eigene ID.
3. Tritt dem Pax-Space bei.
4. Ergaenze dein Profil mit einem Satz, der dich bewegt.
5. Trage ein Angebot ein.
6. Trage ein Beduerfnis ein.
7. Finde eine Person mit aehnlichem Interesse.
8. Fuehre ein echtes Gespraech.
9. Verifiziert euch gegenseitig.
10. Lade jemanden zu einem Kreis, Essen oder Feuer ein.
11. Dokumentiere ein Learning vom Festival.
12. Finde nach Pax eine lokale Anschlussmoeglichkeit.

## 10. Definition of Done fuer Pax v0.1

Pax v0.1 ist rollout-ready, wenn:

- eine fremde Person per QR in die App kommt,
- ohne Vorwissen eine lokale Identitaet erzeugen kann,
- dem Pax-Space freiwillig beitreten kann,
- ein Minimalprofil anlegen kann,
- sichtbar oder bewusst unsichtbar bleiben kann,
- mindestens eine andere Person finden und verifizieren kann,
- Angebot, Beduerfnis oder Vision ausdruecken kann,
- nach dem Festival ihre Kontakte und naechsten Schritte wiederfindet,
- die Stand-Crew den gesamten Flow erklaeren und bei Fehlern auffangen kann.

## 11. Offene Fragen

- Ist der primaere Einstieg Web-App, native App, F-Droid oder eine Auswahlseite?
- Wie viel Recovery ist im Festival-Onboarding zumutbar?
- Muss ein Minimalprofil vor Space-Beitritt existieren oder reicht ein spaeterer Profil-Step?
- Welche Felder sind im Pax-Space oeffentlich, space-intern oder privat?
- Wie wird der Pax-Space vorbefuellt?
- Wie werden analoge Kontakte nachtraeglich in digitale Verbindungen ueberfuehrt?
