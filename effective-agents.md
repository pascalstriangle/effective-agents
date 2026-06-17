# Building Effective Agents

> Basierend auf: [Anthropic – Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents)

## Kernphilosophie

Die erfolgreichsten LLM-Agent-Implementierungen setzen auf **einfache, kombinierbare Muster** statt auf komplexe Frameworks. Der wichtigste Grundsatz: **Mit Einfachheit starten** und Komplexität nur dann hinzufügen, wenn sie nachweislich bessere Ergebnisse liefert.

---

## Grundlegende Definitionen

| Begriff | Beschreibung |
|---------|-------------|
| **Workflows** | Systeme, in denen LLMs und Tools über vordefinierte Code-Pfade gesteuert werden |
| **Agents** | Systeme, in denen LLMs ihre eigenen Prozesse dynamisch steuern und dabei die Kontrolle behalten |

---

## Der Augmented LLM – Grundbaustein

Die Basis jedes Agenten ist ein LLM, erweitert um:

- **Retrieval** – Zugriff auf externe Wissensquellen
- **Tools** – Fähigkeit, Aktionen auszuführen
- **Memory** – Kontext über Interaktionen hinweg behalten

Entscheidend: Diese Fähigkeiten auf den jeweiligen Use Case zuschneiden und klar dokumentieren (z.B. via Model Context Protocol).

---

## Workflow-Muster

### 1. Prompt Chaining (Verkettung)

```
[Input] → LLM Call 1 → Gate → LLM Call 2 → [Output]
```

- Aufgabe wird in **sequenzielle Schritte** zerlegt
- Jeder LLM-Aufruf verarbeitet die Ausgabe des vorherigen
- **Programmatische Gates** zur Qualitätssicherung zwischen den Schritten
- **Wann nutzen:** Aufgaben, die sich in feste Teilschritte zerlegen lassen und wo der Latenz-Tradeoff akzeptabel ist

**Beispiele:** Dokument generieren → dann übersetzen; Code schreiben → dann reviewen

---

### 2. Routing (Weiterleitung)

```
[Input] → Classifier → Route A → Spezialisierter Prompt A
                      → Route B → Spezialisierter Prompt B
                      → Route C → Spezialisierter Prompt C
```

- Eingaben werden **klassifiziert** und an spezialisierte Aufgaben weitergeleitet
- Ermöglicht separate, optimierte Prompts pro Kategorie
- **Wann nutzen:** Verschiedene Eingabetypen erfordern unterschiedliche Behandlung

**Beispiele:** Kundenservice-Anfragen routen; einfache vs. komplexe Anfragen an unterschiedliche Modelle weiterleiten

---

### 3. Parallelization (Parallelisierung)

```
            ┌→ LLM Call A ─┐
[Input] ────┼→ LLM Call B ─┼──→ Aggregator → [Output]
            └→ LLM Call C ─┘
```

Zwei Varianten:

| Variante | Beschreibung | Beispiel |
|----------|-------------|----------|
| **Sectioning** | Unabhängige Teilaufgaben laufen parallel | Guardrails + Hauptantwort gleichzeitig |
| **Voting** | Dieselbe Aufgabe wird mehrfach ausgeführt | Code-Review aus mehreren Perspektiven |

**Wann nutzen:** Unabhängige Teilaufgaben oder wenn Diversität der Ausgaben wertvoll ist

---

### 4. Orchestrator-Workers

```
                        ┌→ Worker LLM A
[Input] → Orchestrator ─┼→ Worker LLM B  → Orchestrator → [Output]
                        └→ Worker LLM C
```

- Ein **zentrales LLM** zerlegt Aufgaben dynamisch und delegiert an Worker-LLMs
- Aufgabenstruktur wird **zur Laufzeit** bestimmt, nicht vorher festgelegt
- **Wann nutzen:** Komplexe Aufgaben, bei denen Teilschritte nicht vorhersagbar sind

**Beispiel:** Multi-File-Code-Änderungen, bei denen der Orchestrator entscheidet, welche Dateien betroffen sind

---

### 5. Evaluator-Optimizer

```
[Input] → Generator LLM ⇄ Evaluator LLM → [Output]
              ↑_______________|
              (iteratives Feedback)
```

- Ein LLM **generiert** Antworten, ein anderes gibt **iteratives Feedback**
- Ähnlich einem menschlichen Redaktionsprozess
- **Wann nutzen:** Klare Bewertungskriterien existieren und Verfeinerung messbare Verbesserungen bringt

**Beispiele:** Texte überarbeiten mit Styleguide-Feedback; Code optimieren mit Test-Ergebnissen als Feedback

---

## Autonome Agent

```
[Aufgabe] → LLM → Aktion → Umgebung → Feedback ─┐
                    ↑_____________________________│
                    (Loop bis Ziel erreicht)
```

- LLMs arbeiten **eigenständig in Schleifen**
- Nutzen Tools basierend auf Umgebungs-Feedback
- Erfordern: klare Toolsets, passende Guardrails, Sandbox-Testing
- **Wann nutzen:** Offene Probleme, bei denen Schritte nicht hartcodiert werden können

**Wichtig:** Menschliche Aufsicht einplanen – Agents können bei falschen Annahmen in Schleifen geraten.

---

## Wann KEINE Agents verwenden

Einfache Single-Call-Optimierungen mit Retrieval und In-Context-Beispielen reichen für viele Anwendungen. Agentische Systeme tauschen **höhere Latenz und Kosten** gegen bessere Aufgabenleistung – dieser Tradeoff muss die zusätzliche Komplexität rechtfertigen.

**Faustregel:**
1. Starte mit einem einfachen Prompt
2. Optimiere durch umfassende Evaluation
3. Füge erst dann mehrstufige Agenten-Systeme hinzu, wenn einfachere Ansätze nicht ausreichen

---

## Tool-Design – Best Practices

Die Gestaltung von Tools verdient **genauso viel Aufmerksamkeit wie die Prompts selbst**. (Bei SWE-bench wurde mehr Zeit in Tool-Optimierung als in Prompt-Optimierung investiert.)

| Prinzip | Beschreibung |
|---------|-------------|
| **Denkraum geben** | Genug Tokens bereitstellen, damit das Modell "denken" kann, bevor es schreibt |
| **Natürliche Formate** | Formate nahe an natürlich vorkommendem Internet-Text halten |
| **Overhead minimieren** | Kein präzises Zählen oder komplexes Escaping erfordern |
| **Dokumentation** | Beispiele, Randfälle und klare Grenzen in Tool-Definitionen aufnehmen |
| **Testen** | Extensiv mit Workbench-Beispielen testen |
| **Poka-Yoke** | Tools so designen, dass Fehler schwer zu machen sind |

**Konkretes Beispiel:** Absolute Dateipfade statt relativer Pfade erfordern → eliminiert navigationsbedingte Fehler.

---

## Die drei Kernprinzipien

### 1. Einfachheit
Agenten-Designs geradlinig und wartbar halten. Viele Muster lassen sich in wenigen Zeilen Code umsetzen.

### 2. Transparenz
Planungsschritte und Reasoning des Agenten **explizit sichtbar** machen. Keine Black Box.

### 3. Agent-Computer Interface (ACI) Design
Genauso viel Aufwand in Tool-Dokumentation und -Testing investieren wie in Human-Computer Interface Design.

---

## Praxisbeispiele

### Kundensupport
- Natürliches Einsatzgebiet für offene Agents (Konversation + Aktionen)
- Erfolg messen über **Resolution-basierte Metriken**
- Mehrere Unternehmen nutzen nutzungsbasierte Preismodelle – als Zeichen ihres Vertrauens in Agent-Effektivität

### Coding Agents
- Besonders effektiv dank **verifizierbarer Lösungen** durch automatisierte Tests
- Agents iterieren mit Test-Ergebnissen als Feedback
- Können echte GitHub-Issues in Benchmarks lösen
- **Menschliches Review bleibt essenziell** für Alignment mit System-Anforderungen

---

## Zusammenfassung

> Erfolg kommt nicht vom Bauen des **komplexesten** Systems, sondern vom Bauen des **richtigen** Systems für die jeweiligen Anforderungen.

```
Einfacher Prompt → Optimieren → Evaluieren → Erst dann: Agents hinzufügen
```

---

*Quelle: [Anthropic Engineering – Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents)*
