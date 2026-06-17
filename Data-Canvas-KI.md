# Data Canvas für KI-Lösungen

*Eine auf KI zugeschnittene Vorlage, um die Datengrundlage eines Vorhabens strukturiert zu planen.*

> **Hinweis zum Zweck und zu Varianten:** Unter dem Namen „Data Canvas" gibt es mehrere etablierte, aber unterschiedliche Vorlagen, unter anderem den Data Canvas für datenbasierte Geschäftsmodelle (z. B. von Datentreiber, verbreitet über Miro) und den Data Ethics Canvas des Open Data Institute (ODI) mit Fokus auf Datenethik. (Der „BigQuery Data Canvas" von Google ist dagegen ein Analysewerkzeug und nicht gemeint.) Dieses Dokument ist eine eigene Synthese, die gezielt die Datenfragen rund um eine KI-Lösung bündelt. Sie ergänzt damit den Business Model Canvas (Geschäftssicht), den Ethical Canvas (ethische Sicht) und CRISP-DM (Vorgehen). Fett gesetzte Fachbegriffe sind im **Glossar** (Abschnitt 4) erklärt.

---

## Inhaltsverzeichnis

1. Die zehn Bausteine (mit KI-Leitfragen)
2. Ausfüll-Vorlage
3. Checkliste zur Datenreife
4. Glossar

---

## 1. Die zehn Bausteine

### 1.1 Ziel und Anwendungsfall
Wofür werden die Daten gebraucht?

KI-Leitfragen:
- Welche fachliche Frage oder Entscheidung soll das Modell unterstützen?
- Welche Art von Ausgabe wird erwartet (Vorhersage, Einstufung, Erzeugung)?

*Beispiel:* Vorhersagen, welche Kunden voraussichtlich kündigen, um ihnen rechtzeitig ein Angebot zu machen.

### 1.2 Benötigte Daten
Welche Daten braucht das Modell, im Training und im Betrieb?

KI-Leitfragen:
- Welche **Features** (Eingangsgrössen) und welche **Labels** (Zielwerte) werden benötigt?
- Unterscheiden sich Trainingsdaten und die Daten, die später bei jeder **Inferenz** anfallen?
- Wie viele Daten sind nötig, und liegen sie in ausreichender Menge vor?

*Beispiel:* Vertragsdauer, Nutzungsverlauf und Beschwerden als Features; „hat gekündigt ja/nein" als Label.

### 1.3 Datenquellen
Woher kommen die Daten?

KI-Leitfragen:
- Welche internen Quellen (eigene Systeme) und externen Quellen (Zukauf, offene Daten, **API**) gibt es?
- Wie steht es um Lizenzen, Nutzungsrechte und Verfügbarkeit auf Dauer?
- Wie aktuell und wie zuverlässig ist jede Quelle?

*Beispiel:* Internes Abrechnungssystem plus zugekaufte Branchenkennzahlen, beide mit geklärten Nutzungsrechten.

### 1.4 Datenqualität und Repräsentativität
Wie gut bilden die Daten die Wirklichkeit ab?

KI-Leitfragen:
- Wie vollständig, korrekt und einheitlich sind die Daten?
- Bilden sie alle relevanten Gruppen und Situationen ab, oder fehlen ganze Teile (**Bias**)?
- Spiegeln historische Daten frühere Fehlentscheidungen wider, die nicht fortgeschrieben werden sollen?

*Beispiel:* Daten stammen nur aus einer Region; für andere Regionen wäre das Modell wahrscheinlich ungenau.

### 1.5 Rechte, Datenschutz und Compliance
Was ist rechtlich und regulatorisch zu beachten?

KI-Leitfragen:
- Enthalten die Daten Personenbezug (**PII**), und auf welcher Rechtsgrundlage werden sie verarbeitet?
- Sind Einwilligung (**Consent**), Zweckbindung und Speicherfristen (**Retention**) geklärt?
- Welche Rechte haben Betroffene (Auskunft, Löschung), und wie werden sie erfüllt?

*Beispiel:* Personenbezogene Felder werden pseudonymisiert, die Aufbewahrung ist auf das Nötige befristet.

### 1.6 Daten-Governance und Verantwortung
Wer verantwortet und steuert die Daten?

KI-Leitfragen:
- Wer ist Eigentümer (**Data Owner**) je Datensatz, wer pflegt ihn (**Data Steward**)?
- Ist die Herkunft über alle Schritte nachvollziehbar (**Data Lineage**)?
- Welche Zugriffsrechte und Freigaben gelten?

*Beispiel:* Die Fachabteilung ist Eigentümerin der Vertragsdaten, jede Verarbeitung ist protokolliert.

### 1.7 Speicherung und Infrastruktur
Wie und wo liegen die Daten, und wie fliessen sie?

KI-Leitfragen:
- Welche Speicher und welche **Pipelines** transportieren und verarbeiten die Daten?
- Wie werden Sicherheit, Verschlüsselung und Standort geregelt?
- Wie greift die Datenhaltung in den laufenden Betrieb (**MLOps**)?

*Beispiel:* Eine automatisierte Pipeline lädt täglich neue Daten, bereinigt sie und stellt sie dem Modell bereit.

### 1.8 Datennutzer und Konsumenten
Wer nutzt die Daten und die Ergebnisse?

KI-Leitfragen:
- Welche Teams, Systeme oder Kunden verwenden die Ausgaben des Modells?
- Welche Form und Genauigkeit brauchen sie, und wie werden Grenzen kommuniziert?

*Beispiel:* Das Kundenbindungsteam erhält täglich eine Liste gefährdeter Kunden samt Wahrscheinlichkeit.

### 1.9 Wertangebot und Datenprodukte
Welcher Wert entsteht aus den Daten?

KI-Leitfragen:
- Welches konkrete Datenprodukt entsteht (Bericht, Vorhersage, eingebettete Funktion)?
- Wie zahlt es auf das Geschäftsmodell ein (Verweis auf den Business Model Canvas)?

*Beispiel:* Eine Kündigungs-Vorhersage, die messbar die Abwanderung senkt.

### 1.10 Risiken und Drift
Was kann mit den Daten schiefgehen, jetzt und später?

KI-Leitfragen:
- Wie wird **Data Drift** erkannt (verändern sich die echten Daten gegenüber dem Training)?
- Welche Risiken bestehen durch Lecks, fehlende Qualität oder fehlerhafte Quellen?
- Wie oft werden Daten und Modell überprüft und aktualisiert?

*Beispiel:* Eine Überwachung schlägt Alarm, wenn sich die Verteilung der Eingabedaten deutlich verschiebt.

---

## 2. Ausfüll-Vorlage

| Baustein | Eintrag für dein Vorhaben |
|----------|---------------------------|
| Ziel und Anwendungsfall | |
| Benötigte Daten | |
| Datenquellen | |
| Datenqualität und Repräsentativität | |
| Rechte, Datenschutz und Compliance | |
| Daten-Governance und Verantwortung | |
| Speicherung und Infrastruktur | |
| Datennutzer und Konsumenten | |
| Wertangebot und Datenprodukte | |
| Risiken und Drift | |

---

## 3. Checkliste zur Datenreife

- [ ] Der Anwendungsfall und die benötigten Features und Labels sind klar.
- [ ] Alle Datenquellen sind erfasst, mit geklärten Rechten und Lizenzen.
- [ ] Qualität und Repräsentativität sind geprüft; Lücken und Verzerrungen sind benannt.
- [ ] Personenbezug, Rechtsgrundlage, Einwilligung und Speicherfristen sind geklärt.
- [ ] Eigentümer und Pflegeverantwortliche je Datensatz sind benannt.
- [ ] Die Datenherkunft ist über alle Schritte nachvollziehbar (Lineage).
- [ ] Speicherung, Sicherheit und Pipelines sind beschrieben.
- [ ] Es ist festgelegt, wie Data Drift erkannt und wie oft aktualisiert wird.
- [ ] Die Datensicht ist mit Ethical Canvas und Ethik-Framework abgestimmt.

---

## 4. Glossar

*Jeder Begriff mit kurzer Definition und konkretem Beispiel.*

**API (Programmierschnittstelle):** Definierte Schnittstelle, über die Daten zwischen Systemen ausgetauscht werden. *Beispiel:* Aktuelle Wechselkurse werden über eine API einer Drittquelle bezogen.

**Bias (Verzerrung):** Systematische Schieflage in den Daten, die zu unfairen oder falschen Ergebnissen führt. *Beispiel:* Eine Gruppe ist in den Daten kaum vertreten, deshalb sind die Vorhersagen für sie schlechter.

**Consent (Einwilligung):** Zustimmung der betroffenen Person zur Verarbeitung ihrer Daten für einen bestimmten Zweck. *Beispiel:* Kunden stimmen zu, dass ihr Nutzungsverlauf zur Verbesserung des Dienstes ausgewertet wird.

**Data Drift (Datendrift):** Veränderung der echten Eingabedaten gegenüber den Trainingsdaten im Lauf der Zeit. *Beispiel:* Nach einer Preisreform ändert sich das Kundenverhalten, und alte Muster passen nicht mehr.

**Data Lineage (Datenherkunft):** Lückenlose Nachverfolgbarkeit, woher Daten stammen und wie sie verarbeitet wurden. *Beispiel:* Man kann zu jedem Wert zurückverfolgen, aus welcher Quelle und über welche Schritte er entstand.

**Data Owner / Data Steward (Dateneigentümer / Datenpfleger):** Verantwortliche für Entscheidungen über einen Datensatz bzw. für dessen laufende Pflege und Qualität. *Beispiel:* Die Vertriebsleitung ist Eigentümerin der Verkaufsdaten, eine benannte Person pflegt sie.

**Feature (Merkmal / Eingangsgrösse):** Eine Eingangsvariable, aus der das Modell lernt oder eine Vorhersage ableitet. *Beispiel:* „Anzahl Beschwerden im letzten Jahr" ist ein Feature.

**Inferenz (Inference):** Die Nutzung eines fertigen Modells, um zu einer Eingabe eine Ausgabe zu erzeugen. *Beispiel:* Für einen einzelnen Kunden die Kündigungswahrscheinlichkeit berechnen.

**Label (Zielwert):** Die bekannte, korrekte Antwort, die das Modell im Training lernen soll. *Beispiel:* „hat gekündigt: ja" als Label zu einem historischen Kundendatensatz.

**MLOps (Machine Learning Operations):** Praktiken und Werkzeuge für den zuverlässigen Betrieb, die Überwachung und die Aktualisierung von Modellen und Datenflüssen. *Beispiel:* Eine Pipeline trainiert das Modell automatisch neu, sobald die Qualität fällt.

**Pipeline (Datenpipeline):** Automatisierte Abfolge von Schritten, die Daten beschafft, verarbeitet und bereitstellt. *Beispiel:* Jede Nacht werden Rohdaten geladen, bereinigt und für das Modell aufbereitet.

**PII (Personally Identifiable Information / personenbezogene Daten):** Daten, die eine Person identifizierbar machen. *Beispiel:* Name, Adresse und Kundennummer zusammengenommen.

**Retention (Aufbewahrungsfrist):** Festgelegter Zeitraum, für den Daten gespeichert und danach gelöscht werden. *Beispiel:* Beschwerdedaten werden nach drei Jahren automatisch entfernt.
