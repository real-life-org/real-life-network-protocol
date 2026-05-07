# Data Model

Mapping zwischen sozialen Operationen, App-Flows, Items, Relationen, Claims und Metriken.

Aktueller Startpunkt:

- [operations-mapping.md](operations-mapping.md)

Aktuelle Modellierungsentscheidung:

- WoT-Verifikationen und Attestations bleiben VC-JWS nach `wot-spec`.
- Profile und Quests werden als generische Real-Life-Stack-Items modelliert.
- Offers und Needs sind für Pax v0.1 einfache Tags im Profil. In WoT sind sie bereits Profilfelder; in RLS sind sie Ziel-/Interface-Felder, aber noch nicht vollständig in der Referenzimplementierung umgesetzt.

Nächster Schritt:

- RLS-kompatible Item-Schemata für `profile`, `quest`, `visibility` und `follow-up` ableiten und die WoT-Profilfelder `offers[]`/`needs[]` sauber in die RLS-Profile-View mappen.
