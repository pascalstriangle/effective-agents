# Business Model Canvas für KI-Lösungen

*Der Business Model Canvas (BMC) nach Alexander Osterwalder, übertragen auf Produkte und Dienste, die auf KI und maschinellem Lernen beruhen.*

> **Hinweis zum Zweck:** Der BMC ist eine visuelle Vorlage mit neun Bausteinen, mit der ein Geschäftsmodell auf einer Seite beschrieben und gemeinsam diskutiert wird. Diese Fassung ergänzt jeden Baustein um KI-spezifische Leitfragen und ein Beispiel. Fett gesetzte Fachbegriffe sind im **Glossar** (Abschnitt 4) erklärt. Originalvorlage: Business Model Canvas, Strategyzer / Business Model Foundry AG.

---

## Inhaltsverzeichnis

1. Die neun Bausteine (mit KI-Leitfragen)
2. Ausfüll-Vorlage
3. Checkliste vor der Umsetzung
4. Glossar

---

## 1. Die neun Bausteine

**Empfohlene Reihenfolge beim Ausfüllen:** zuerst Kundensegmente und Wertangebote (rechte, marktseitige Hälfte), dann die Infrastruktur (linke Hälfte), zuletzt Einnahmen und Kosten. Bei KI-Vorhaben lohnt es sich, früh die Bausteine Schlüsselressourcen (Daten) und Kostenstruktur (Rechenkosten) zu prüfen, weil sie oft über die Tragfähigkeit entscheiden.

### 1.1 Kundensegmente (Customer Segments)
Für wen wird Wert geschaffen? Wer sind die wichtigsten Nutzer?

KI-Leitfragen:
- Wer hat ein Problem, das sich durch Vorhersage, Automatisierung oder Mustererkennung lösen lässt?
- Sind die Nutzer technisch versiert (Entwickler über eine **API**) oder Laien (Endkunden in einer App)?
- Wie tolerant sind die Nutzer gegenüber Fehlern des Modells? Ein falscher Filmtipp ist harmlos, eine falsche Diagnose nicht.

*Beispiel:* Kleine Arztpraxen, die Sprechstunden-Diktate automatisch in strukturierte Notizen umwandeln wollen.

### 1.2 Wertangebote (Value Propositions)
Welches Problem wird gelöst, welcher Nutzen entsteht?

KI-Leitfragen:
- Worin liegt der Mehrwert der KI konkret: Zeitersparnis, tiefere Erkenntnisse, Personalisierung, Skalierung, tiefere Kosten?
- Wäre eine einfache, regelbasierte Lösung ohne KI gut genug? Wenn ja, ist KI womöglich überflüssig.
- Wie wird mit Unsicherheit umgegangen? Liefert das Produkt Wahrscheinlichkeiten und Begründungen statt Scheingenauigkeit?

*Beispiel:* „Aus einer Stunde Diktat in zwei Minuten eine fertige, korrigierbare Notiz, die der Arzt nur noch freigibt."

### 1.3 Kanäle (Channels)
Über welche Wege werden Kunden erreicht und beliefert?

KI-Leitfragen:
- Wird die KI als eigenständige App, als Zusatzfunktion in bestehender Software oder als **API** für Dritte ausgeliefert?
- Wie werden Vertrauen und Erwartungen gesteuert (Kennzeichnung als KI, Erklärung der Grenzen)?

*Beispiel:* Integration als Schaltfläche direkt in die bereits genutzte Praxissoftware, dazu eine Web-Oberfläche.

### 1.4 Kundenbeziehungen (Customer Relationships)
Welche Art von Beziehung erwartet jedes Segment?

KI-Leitfragen:
- Wie entsteht Vertrauen, wenn das System nicht immer richtig liegt? (Transparenz, Korrekturmöglichkeit, menschliche Rückfallebene.)
- Wird die Beziehung durch Lernen aus Nutzerdaten enger, und ist das datenschutzrechtlich sauber geregelt?
- Gibt es einen Support für Fälle, in denen das Modell versagt?

*Beispiel:* Selbstbedienung im Alltag, aber ein erreichbarer menschlicher Support, sobald die KI eine Notiz als „unsicher" markiert.

### 1.5 Einnahmequellen (Revenue Streams)
Wofür sind die Kunden zu zahlen bereit, und wie?

KI-Leitfragen:
- Welches Preismodell passt: Abonnement, Bezahlung pro Nutzung (z. B. pro Anfrage oder pro **Token**), pro Sitzplatz, oder ergebnisabhängig?
- Deckt der Preis die laufenden **Inferenz**-Kosten pro Nutzung? Bei KI fallen anders als bei klassischer Software je Anfrage echte Kosten an.
- Gibt es eine kostenlose Stufe, und ist sie finanzierbar?

*Beispiel:* Monatliches Abo pro Behandler plus ein Aufpreis bei sehr hohem Diktatvolumen.

### 1.6 Schlüsselressourcen (Key Resources)
Welche Mittel sind unverzichtbar?

KI-Leitfragen:
- **Daten:** Welche Trainings- und Betriebsdaten werden gebraucht, woher kommen sie, und ist der Zugang dauerhaft gesichert? (Siehe Data Canvas.)
- **Modelle:** Eigenes Modell, Feinabstimmung (**Fine-Tuning**) eines **Foundation Model** oder Zukauf über eine API?
- **Rechenleistung (Compute):** Welche Hardware oder Cloud wird für Training und Betrieb benötigt?
- **Menschen:** ML-Fachleute, Fachexperten für die Datenkennzeichnung (**Labeling**), Personen für die Qualitätssicherung.

*Beispiel:* Ein vortrainiertes Sprachmodell, eine medizinische Fachterminologie-Datenbank und anonymisierte Beispiel-Diktate für die Feinabstimmung.

### 1.7 Schlüsselaktivitäten (Key Activities)
Welche Tätigkeiten muss das Unternehmen beherrschen?

KI-Leitfragen:
- Datenbeschaffung, Datenbereinigung und **Labeling** als laufende, nicht einmalige Aufgabe.
- Training, Bewertung und regelmässige Aktualisierung der Modelle.
- **MLOps:** stabiler Betrieb, Überwachung von Qualität und **Data Drift**, Wiederanlernen bei nachlassender Leistung.
- Sicherheits- und Qualitätsprüfung (Tests, Red-Teaming, Bias-Kontrolle).

*Beispiel:* Laufendes Sammeln korrigierter Notizen (mit Einwilligung), um das Modell vierteljährlich nachzuschärfen.

### 1.8 Schlüsselpartnerschaften (Key Partnerships)
Wer liefert zu, wer trägt mit?

KI-Leitfragen:
- Cloud- und Compute-Anbieter für Training und **Inferenz**.
- Anbieter von **Foundation Models** oder APIs, mit Blick auf Abhängigkeit, Preisänderungen und Datenschutz.
- Datenpartner und Lizenzgeber; Annotationsdienstleister für das Labeling.
- Fach- oder Branchenpartner, die Glaubwürdigkeit und Zugang zum Markt bringen.

*Beispiel:* Ein Cloud-Anbieter mit Serverstandort in der Schweiz und ein Berufsverband, der das Produkt empfiehlt.

### 1.9 Kostenstruktur (Cost Structure)
Welche Kosten dominieren das Modell?

KI-Leitfragen:
- Einmalige bzw. wiederkehrende **Trainingskosten** gegenüber laufenden **Inferenzkosten** pro Anfrage.
- Kosten für Daten (Erwerb, Lizenzen, Labeling) und für Personal (ML, Fachexperten).
- Skaliert der Gewinn mit der Nutzung, oder steigen die Rechenkosten genauso schnell wie der Umsatz? (Stichwort Gesamtkosten, **TCO**.)

*Beispiel:* Hohe Anfangskosten für Feinabstimmung und Zulassung, danach planbare Kosten je verarbeitetem Diktat.

---

## 2. Ausfüll-Vorlage

| Baustein | Eintrag für dein Vorhaben |
|----------|---------------------------|
| Kundensegmente | |
| Wertangebote | |
| Kanäle | |
| Kundenbeziehungen | |
| Einnahmequellen | |
| Schlüsselressourcen | |
| Schlüsselaktivitäten | |
| Schlüsselpartnerschaften | |
| Kostenstruktur | |

---

## 3. Checkliste vor der Umsetzung

- [ ] Das Kernproblem ist klar benannt und KI ist dafür wirklich nötig (eine einfache Lösung reicht nicht).
- [ ] Die Datengrundlage ist verfügbar, rechtlich geklärt und dauerhaft gesichert.
- [ ] Das Preismodell deckt die laufenden Inferenzkosten je Nutzung.
- [ ] Abhängigkeiten von externen Modell- und Cloud-Anbietern sind bewertet (Preis, Datenschutz, Ausweichoption).
- [ ] Für Modellfehler gibt es eine menschliche Rückfallebene und einen Supportweg.
- [ ] Der laufende Aufwand für MLOps, Überwachung und Nachtraining ist eingeplant.
- [ ] Datenschutz und regulatorische Anforderungen sind berücksichtigt (Verweis auf das Ethik- und Compliance-Framework sowie den Ethical Canvas).
- [ ] Es ist abgeschätzt, ob das Modell mit wachsender Nutzung profitabel bleibt.

---

## 4. Glossar

*Jeder Begriff mit kurzer Definition und konkretem Beispiel.*

**API (Application Programming Interface / Programmierschnittstelle):** Definierte Schnittstelle, über die andere Programme eine Funktion nutzen. *Beispiel:* Eine fremde App schickt Text an die KI-API und erhält die fertige Notiz zurück.

**Compute (Rechenleistung):** Die für Training und Betrieb nötige Rechenkapazität, meist spezialisierte Prozessoren. *Beispiel:* Das Training läuft mehrere Tage auf gemieteten Grafikprozessoren in der Cloud.

**Data Drift (Datendrift):** Allmähliche Veränderung der echten Daten gegenüber den Trainingsdaten, wodurch die Modellqualität sinkt. *Beispiel:* Neue Fachbegriffe tauchen in Diktaten auf, die das Modell noch nicht kennt.

**Fine-Tuning (Feinabstimmung):** Gezieltes Nachtrainieren eines vortrainierten Modells für eine bestimmte Aufgabe. *Beispiel:* Ein allgemeines Sprachmodell wird mit medizinischen Diktaten nachtrainiert.

**Foundation Model (Basismodell):** Sehr grosses, allgemein vortrainiertes Modell, das als Grundlage für viele Anwendungen dient. *Beispiel:* Ein grosses Sprachmodell, auf dem mehrere Spezialprodukte aufsetzen.

**Inferenz (Inference):** Die Nutzung eines fertigen Modells, um zu einer Eingabe eine Ausgabe zu erzeugen. *Beispiel:* Jede einzelne Umwandlung eines Diktats in eine Notiz ist eine Inferenz und verursacht Rechenkosten.

**Labeling (Datenkennzeichnung / Annotation):** Das manuelle Versehen von Daten mit den korrekten Antworten für das Training. *Beispiel:* Fachpersonen markieren in Beispiel-Diktaten Diagnose, Medikament und Dosierung.

**MLOps (Machine Learning Operations):** Praktiken und Werkzeuge, um Modelle zuverlässig zu betreiben, zu überwachen und zu aktualisieren. *Beispiel:* Ein System meldet automatisch, wenn die Trefferquote des Modells unter eine Schwelle fällt.

**TCO (Total Cost of Ownership / Gesamtkosten):** Summe aller Kosten über den gesamten Lebenszyklus, nicht nur der Anschaffung. *Beispiel:* Neben dem Training zählen auch Betrieb, Nachtraining und Support zur TCO.

**Token:** Kleine Texteinheit (Wortteil), in der Sprachmodelle rechnen und oft abgerechnet werden. *Beispiel:* Ein langes Diktat besteht aus vielen Tausend Token; danach richtet sich der Preis pro Anfrage.
