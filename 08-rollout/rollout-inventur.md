# Rollout-Inventur — Real Life Network Protocol

**Status:** Entwurf v0.1  
**Datum:** 2026-05-07  
**Zweck:** Bestandsaufnahme der vorhandenen Bausteine und der Lücken, die geschlossen werden müssen, damit das Real Life Network Protocol praktisch ausgerollt werden kann.

---

## 1. Kurzfazit

Es gibt bereits eine starke Grundlage:

- Die soziale Vision ist in `netzwerk.md`, `handbuch.md`, `vernetzungskonzept.md` und `netzwerk-protokoll.md` beschrieben.
- Das Web of Trust hat eine formale Spec, Conformance-Struktur, Implementierungsstand, Identitäten, Verifikationen, Attestations, Spaces und Sync.
- Der Real Life Stack hat App-Shell, DataInterface, Connector-Schicht, Referenz-App, Profile, Gruppen, Feed, Kalender, einfache Karte, Kontakte, Verifikation und WoT-Connector.
- Für Pax und die Festival-Saison gibt es bereits eine konkrete Roadmap mit Muss/Soll/Kann-Scope.
- Mit Eli, WoT-Tools und dem Agent Runner gibt es erste Bausteine, um KI-Agenten in Spezifikations-, Implementierungs- und Unterstützungsprozesse einzubinden.

Die zentrale Lücke liegt nicht mehr im "Warum", sondern im Übersetzen:

> Soziale Operationen müssen als App-Flows, Datenmodelle, Quests, Playbooks, Crew-Briefings und Agenten-Handlungsrahmen modelliert werden.

Der nächste sinnvolle Schritt ist deshalb kein weiterer großer Visionstext, sondern eine Rollout-Slice-Definition: Welche minimalen sozialen Operationen müssen auf Pax/Festivals, in lokalen Kreisen und in der App v0.1 zuverlässig funktionieren?

## 2. Inventur nach Baustein-Klassen

### 2.1 Vision, Kultur und soziale Praxis

**Vorhanden**

- `netzwerk.md` beschreibt das Real Life Network als dezentrales Beziehungsnetz aus Menschen, Gemeinschaften, Kreisen, Ressourcen, Projekten und Orten.
- `handbuch.md` beschreibt konkrete Handlungen: Menschen einladen, Kreise starten, Festivals bespielen, Ressourcen verwalten, dokumentieren.
- `vernetzungskonzept.md` beschreibt, wie bestehende Initiativen sichtbar werden, Ownership teilen, eigene Spaces gründen und ihre Autonomie behalten.
- `netzwerk-protokoll.md` definiert Grundprinzipien, Entitäten und soziale Kernoperationen.
- Praktische Formate sind benannt: Kreis, Redekreis, gemeinsames Essen, Vollmondfeuer, Vernetzungszelt, Gartentag, Festival-Stand.

**Fehlt**

- Wiederholbare Playbooks für konkrete Formate: Kreis starten, Vernetzungszelt betreiben, neue Initiative andocken, Commons anlegen, Nachbereitung machen.
- Eine klare "erste Stunde / erster Tag / erste Woche"-Dramaturgie für neue Menschen und neue lokale Gruppen.
- Vorlagen für Einladungen, Check-ins, Nachfass-Nachrichten, Dokumentation und Reflexion.
- Eine explizite Praxis für Konflikte, Mediation, Grenzen, Überforderung und Austritt aus Räumen.
- Kinderschutz-/Jugendschutz-Leitplanken, sobald Jugendliche oder Kinder in App-Flows oder Quests vorkommen.

### 2.2 Formale Spezifikationen

**Vorhanden**

- `wot-spec` ist eine formale technische Spezifikation mit Identität, Trust, Sync, Extensions, Versioning, Conformance, Schemas und Testvektoren.
- `netzwerk-protokoll.md` ist ein erster formaler Entwurf für soziale Operationen, Prinzipien, Entitäten, Quests, Agenten und Conformance.
- `real-life-stack/docs` beschreibt Module, Konzepte, Item-Typen, Web-of-Trust-Integration und den Aktivierungskreislauf.

**Fehlt**

- Ein maschinenlesbares oder zumindest tabellarisches Mapping: soziale Operation -> App-Flow -> Datenmodell -> Quest -> Agentenunterstützung -> Metrik.
- Versionierung und Conformance für das Netzwerk-Protokoll selbst.
- Ein gemeinsames Glossar zwischen Netzwerk-Protokoll, Real Life Stack und Web of Trust.
- Schemas für soziale Entitäten wie Quest, Ressource, Commons, Initiative, Dokumentation, Beziehung, Einladung.
- Akzeptanzkriterien, wann ein Tool oder Agent "protokollkonform" im sozialen Sinn ist.

### 2.3 Web of Trust

**Vorhanden**

- DID-basierte Identität, Signaturen, QR-Challenge-Verifikation, Attestations und signierte Profile sind spezifiziert.
- Group Spaces, Personal Doc, Relay, Vault, Profiles, E2EE-Sync und lokale Persistenz sind als Architektur vorhanden.
- Die Implementierung hat Demo-App, native/mobile Pfade, Biometric Unlock, F-Droid/OTA, E2E-Tests und WoT-Connector-Anbindung.
- `wot-spec` hat Conformance-Profile für Identity, Trust und Sync.
- Der Agent Runner kann Spec-Tasks in PR-fähige Arbeitspakete übersetzen.

**Fehlt**

- Stabiler, produktnaher Pax-Flow mit Onboarding unter 2 Minuten.
- Klare Integration der sozialen Operationen in die WoT-App oder RLS-Referenz-App.
- Referenzimplementierung ist im Umbau: der vorhandene Stand ist wertvoll, aber nicht mehr alleinige normative Quelle.
- Nutzerfreundliche Sichtbarkeit und Kontrolle für Attestations, Profile, Space-Beitritte und öffentliche Daten.
- Noch nicht vollständig geklärt: selektives Teilen, robuste Einladungs-/Space-Flows, Jugend-/Kinderschutz, langlebige Recovery- und Safety-UX.

### 2.4 Real Life Stack und App-Module

**Vorhanden**

- App-Shell mit Workspaces/Spaces, Modul-Tabs und Bottom Navigation.
- DataInterface mit generischen Items, Relationen, Gruppen, Auth, Contacts, Signed Claims und Profil-Fähigkeiten.
- Item-Typen im Code: `task`, `event`, `post`, `place`, `feature`, `profile`, Reactions und Kommentare.
- Profilfelder im Code: Name, Bio, Avatar, Skills, Offers, Needs.
- Referenz-App mit Feed, Kanban, Kalender, einfacher Kartenansicht, Profil-Dialog, Kontakt-Dialogen, Verifikation, Gruppenverwaltung und WoT-Connector.
- Modul-Dokumente für Kalender, Karte, Marketplace, Quests und Gamification.

**Fehlt**

- Die Karte ist aktuell eher Platzhalter/Listenansicht als echte interaktive Netzwerk-Karte.
- Marketplace/Ressourcen sind nur sehr grob beschrieben.
- Quests sind dokumentarisch vorhanden, aber noch nicht im neuen sozialen Sinn spezifiziert oder implementiert.
- Es fehlt ein expliziter `resource`-/`commons`-/`need`-/`offer`-/`quest`-/`initiative`-Typ im produktiven RLS-Datenmodell.
- Event-Teilnahme, Vor-Ort-QR, Anwesenheitsbestätigung und Event-Nachbereitung sind noch nicht als vollständiger Flow umgesetzt.
- Profile brauchen für Pax den konkreten Minimalumfang: Name, Avatar, Angebote, Bedürfnisse, Vision, optional Ort/Region und Sichtbarkeit.
- Map-Einträge brauchen Ownership, mehrere Owner, Space-Zugehörigkeit, Sichtbarkeit und Pflege-Status.

### 2.5 Daten- und Graphmodell

**Vorhanden**

- Das generische `Item`-Modell mit `type`, `data` und `relations` ist flexibel genug, um soziale Entitäten abzubilden.
- Relationen können Items, Profile, Spaces und Cross-Space-Bezüge verbinden.
- Signed Claims können Verifikationen und Attestations repräsentieren.
- Groups/Spaces sind als kollaborative Räume vorhanden.

**Fehlt**

- Ein explizites Protokoll-Event-Log: Welche soziale Operation wurde wann, von wem, mit welchem Ergebnis dokumentiert?
- Eine klare Relationstaxonomie für Netzwerkaufbau: kennt, verifiziert, eingeladen, teilgenommen, beigetragen, hütet, besitzt, braucht, bietet, gehört zu, findet statt an.
- Ein Modell für Commons mit Hüter, Ort, Nutzungsregeln, Pflege-Rhythmus und Verfügbarkeit.
- Ein Modell für Quests als Einladungen statt Leistungsaufgaben.
- Ein Modell für Metriken ohne Ranking-Logik: Netzwerkgröße, Begegnungen, Events, Ressourcen, Projekte, Dokumentation, Fortschritt lokaler Kreise.

### 2.6 Praktische Rollout-Kontexte

**Vorhanden**

- Festival-Roadmap 2026 mit DWeb Camp, Local First Conf und Pax Friedensfestival.
- Pax-Scope ist bereits konkret: QR-Einstieg, Profil in unter 2 Minuten, Pax-Space, Map, Verifikation, nach dem Festival verbunden bleiben.
- Vernetzungszelt ist als Format beschrieben: temporärer Begegnungsraum auf Festivals und Veranstaltungen.
- Stand-Crew-Bedarf, Material, ehrliche Pilot-Kommunikation und Offline-Toleranz sind benannt.

**Fehlt**

- Pax-Space-Spezifikation: Welche Module, Startinhalte, Rollen, Einladungslinks, QR-Codes, Sichtbarkeiten?
- Stand-Crew-Briefing mit konkreten Gesprächsabläufen, Datenschutzantworten und "was tun wenn"-Situationen.
- Analoge Fallbacks bei schlechter Technik: Papierkarte, Kontaktkarten, QR-Backup, Offline-Dokumentation.
- Nachbereitungsprotokoll: Wie werden Festivalkontakte zu lokalen Kreisen, nächsten Einladungen und Projekten?
- Testprotokoll mit 5-10 echten Nicht-Tech-Nutzer:innen.

### 2.7 Kommunikation und öffentliche Artefakte

**Vorhanden**

- `real-life-network` ist als öffentliche Website/Story vorhanden.
- Die Docs erklären Unterschied zwischen Organisation, Netzwerk, Tools und Zweck.
- Es gibt bereits narrative Sprache: weniger Konsum, mehr echtes Leben; Technologie als Spiegel der Realität; Einladung statt Überzeugung.

**Fehlt**

- Ein One-Pager für Pax/Festivals: Was ist das? Wie mache ich mit? Was passiert mit meinen Daten?
- Eine knappe Startseite oder Landing-Ziel für den QR-Code am Stand.
- Kurzes Erklärvideo oder Tablet-Demo.
- Öffentliche Dokumentation, die aus der Spec abgeleitet ist, aber nicht spezifikationsartig klingt.
- Material für bestehende Initiativen: "So dockt ihr an, ohne eure Autonomie aufzugeben."

### 2.8 KI-Agenten

**Vorhanden**

- Eli hat Erinnerungen, Telegram-Fähigkeit, WoT-Task-Tools und Netzwerk-Kontext.
- Codex/Agent Runner können Spezifikationen in PRs, Tasks, Checks und Review-Schleifen übersetzen.
- `netzwerk-protokoll.md` definiert KI-Agenten als mögliche eingebettete Teilnehmer mit eigener Identität.

**Fehlt**

- Ein Agenten-Handlungsrahmen: Was darf ein Agent vorschlagen, wann fragt er nach Zustimmung, wann hält er sich zurück?
- Eine lokale Graph-Sicht: Welche Personen, Orte, Ressourcen und Events darf ein Agent sehen?
- Ein Quest-/Next-Step-Engine-Konzept: Welche Einladung ist in welchem Netzwerkzustand sinnvoll?
- Agenten-Conformance: keine Kontrolle, kein Ranking von Menschen, keine Missionierung, keine Drucklogik.
- Agenten-Identität im Netzwerk: DID, Profil, Attestations, Rechte, Sichtbarkeit, Verantwortlichkeit.

## 3. Soziale Operationen: Rollout-Reife

| Operation | Schon vorhanden | Fehlt für Rollout |
|---|---|---|
| Menschen kennenlernen | Vision, Handbuch, Kreis- und Festivalpraxis | Onboarding-Dramaturgie, Kontakt-/Nachfass-Flow, App-Einstieg |
| Menschen einladen | Prinzip Einladung statt Überzeugung | Einladungsvorlagen, Ablehnen-ohne-Druck-UX, Quest-Sprache |
| Menschen verifizieren | WoT-Spec, QR-Verifikation, App-Komponenten | Festival-tauglicher Flow, Fehlerfälle, Erklärung für Laien |
| Beiträge attestieren | WoT-Attestations, Claims, Profil-Sichtbarkeit | UX für konkrete Beiträge, Akzeptieren/Sichtbarkeit, soziale Leitplanken |
| Veranstaltungen ausrichten | Kalender-Docs, Event-Typ, Handbuch | Vollständiger Event-Flow, Teilnahme, Nachbereitung, Ritualvorlagen |
| Kreis starten | Handbuch | Starter-Kit, erste 4 Treffen, App- und Agentenunterstützung |
| Ressourcen teilen/nachfragen | Handbuch, Profil Offers/Needs, Marketplace-Idee | Resource-/Need-/Offer-Typen, Suche, Pflege, Verfügbarkeit |
| Commons schaffen | Netzwerktext, Handbuch | Commons-Modell, Hüter/Pflege/Nutzungsregeln, gemeinsame Anschaffung |
| Projekte starten | Kanban/Tasks, Gruppen/Spaces | Projekt-Typ, Projekt-Start-Quest, Beziehung zu Orten/Ressourcen/Events |
| Orte gründen/pflegen | Place-Typ, Map-Idee | Echte Map, Ort als sozialer Raum, Pflege-/Owner-Modell |
| Dokumentieren | Feed/Post, Media-Idee, Handbuch | Dokumentations-Flow, Zustimmung, Story-Templates, Agenten-Zusammenfassung |
| Menschen/Initiativen verbinden | Vernetzungskonzept, Items/Spaces | Initiative-Typ, Cross-Space-Ownership, Bridge-Flow, Andock-Playbook |

## 4. Kritische Lücken nach Priorität

### P0 — Muss für einen ersten echten Rollout

1. **Pax-MVP-Slice definieren**  
   Exakt festlegen, welche sozialen Operationen in Pax funktionieren müssen: joinen, Profil anlegen, auf Map sichtbar werden, Menschen verifizieren, Angebote/Bedürfnisse/Visionen sehen, verbunden bleiben.

2. **Operation-to-App-Mapping schreiben**  
   Für jede P0-Operation: App-Screen, Datenobjekt, Relation, Sichtbarkeit, Agentenhilfe, Erfolgssignal.

3. **Pax-Space spezifizieren**  
   Module, Startdaten, QR-Links, Rollen, Sichtbarkeiten, Offline-Fallback, Stand-Crew-Rechte.

4. **Profil-Minimum stabilisieren**  
   Name, Avatar, kurze Bio/Vision, Angebote, Bedürfnisse, optional Region/Ort; mit klarer Sichtbarkeitslogik.

5. **Map-/Resource-Minimum definieren**  
   Menschen, Initiativen, Orte, Angebote und Bedürfnisse müssen in Pax einfach sichtbar werden.

6. **Verifikationsflow festival-tauglich machen**  
   QR scannen, bestätigen, Gegenbestätigung, Fehlerfälle, Offline-/schlechtes-Netz-Verhalten.

7. **Quest-Katalog v0.1 schreiben**  
   Nicht XP-first, sondern Einladung-first: jemanden kennenlernen, sich verifizieren, Angebot eintragen, Bedürfnis äußern, zu Kreis einladen, Foto/Bericht teilen, Initiative markieren.

8. **Vernetzungszelt-Playbook schreiben**  
   Aufbau, Rollen, Gesprächsabläufe, Tagesrhythmus, Datenschutzantworten, Nachbereitung.

9. **Pilot-Kommunikation und Consent-Texte vorbereiten**  
   Ehrlich: Pilotversion, lokale Datenhoheit, Sichtbarkeit, freiwillige Teilnahme, keine Pflicht.

10. **Feedback- und Nachbereitungsloop einrichten**  
   Was wurde gelernt? Welche Kontakte brauchen Follow-up? Welche lokalen Kreise könnten entstehen?

### P1 — Wichtig direkt nach dem ersten Rollout

- Event-Teilnahme mit QR und Anwesenheitsbestätigung.
- Commons-Modell mit Hüter, Pflege, Ort, Nutzungsregeln und Verfügbarkeit.
- Projekt- und Initiative-Typen mit Cross-Space-Ownership.
- Dokumentations-Templates für Fotos, Texte, Learnings und Fortschritt.
- Agenten-gestützte Next-Step-Vorschläge.
- Metriken als Netzwerk-Signale ohne Ranking von Menschen.
- Inter-Space-Sichtbarkeit und Pflege von Items in mehreren Spaces.

### P2 — Spätere Ausbaustufen

- Jugend-/Kinderschutz-Modus mit Erziehungsberechtigten-Logik.
- Mediation-/Konflikt-Unterstützung als optionales Netzwerkangebot.
- Fortgeschrittene Governance-Module.
- Föderation mit externen Netzwerken und Tools.
- Selektives Teilen auf Item-Ebene mit ausgereifter UX.
- Öffentliche Lernmaterialien, Videos, Handbücher und Facilitation-Ausbildung.

## 5. Vorgeschlagene nächste Artefakte

Diese Inventur legt nahe, als nächstes nicht alles gleichzeitig zu schreiben, sondern fünf Arbeitsdokumente anzulegen:

1. `pax-rollout-slice.md` — verbindlicher Minimal-Scope für den ersten öffentlichen Einsatz.
2. `operations-mapping.md` — soziale Operationen auf App-Flows, Datenmodelle, Quests, Agenten und Metriken mappen.
3. `quest-katalog.md` — erste 30 bis 50 Quests als freiwillige Einladungen.
4. `vernetzungszelt-playbook.md` — praktisches Handbuch für Festival- und Event-Einsätze.
5. `agenten-handlungsrahmen.md` — Regeln, Fähigkeiten und Grenzen für KI-Agenten im Netzwerk.

## 6. Definition: Rollout-ready v0.1

Das Protokoll ist nicht dann rollout-ready, wenn es vollständig ist. Es ist rollout-ready, wenn ein erster realer Einsatz ohne ständige Improvisation getragen werden kann.

Für v0.1 heißt das:

- Ein neuer Mensch kann verstehen, worum es geht, freiwillig einsteigen und sein Profil anlegen.
- Eine Begegnung kann zu einer Verifikation werden.
- Eine Person kann sichtbar machen, was sie anbietet, braucht oder bewegen will.
- Ein lokaler Ort, eine Initiative, ein Event oder eine Ressource kann dokumentiert werden.
- Eine Stand-Crew kann das Netzwerk erklären und Menschen durch die ersten Schritte begleiten.
- Eine lokale Gruppe kann nach dem Event weiterarbeiten.
- Ein KI-Agent kann hilfreiche nächste Schritte vorschlagen, ohne Menschen zu bewerten oder zu steuern.
- Die Datenmodelle sind einfach genug für Pax und präzise genug, um danach erweitert zu werden.

## 7. Wichtigste Entscheidung

Die nächste Entscheidung ist:

> Schneiden wir das Netzwerk-Protokoll zuerst entlang des Pax-Rollouts oder entlang der vollständigen sozialen Operationen?

Empfehlung: zuerst Pax-Rollout-Slice. Pax zwingt zur Konkretion, ohne das Gesamtprotokoll zu verlieren. Danach können die Operationen systematisch erweitert und verallgemeinert werden.
