---
layout: chapter
title: "Präzision"
chapter: 5
part: 2
part_title: "Fähigkeiten"
part_url: "/de/part-2-skills/"
lang: de
dir: ltr
prev: "/de/part-2-skills/04-decomposition"
prev_title: "Zerlegung"
next: "/de/part-2-skills/06-feedback"
next_title: "Feedback"
---

Nicht alle Prompts sind gleich. Es gibt ein Spektrum von vage bis präzise, und wo Sie auf diesem Spektrum landen, bestimmt Ihre Erfolgsquote.

![Das Spektrum](/code-with-ai/assets/images/diagrams/05-1-the-spectrum.png)
{: .chapter-diagram}
*Abbildung 5.1: Das Spektrum — Von vage bis präzise*
{: .diagram-caption}

Betrachten Sie diesen Verlaufsbalken. Links, in Rot: VAGE. Rechts, in Blau: PRÄZISE. Ihr Ziel ist es, so weit wie möglich nach rechts zu gelangen, bevor Sie absenden.

Ein vager Prompt wie "Hilf mir bei Berechnungen" hat vielleicht eine Erfolgsquote von 20%. Die KI hat keine Ahnung, welche Berechnungen Sie meinen. Welche Eingaben? Welche Ausgaben? Welcher Bereich? Sie wird raten, und sie wird wahrscheinlich falsch raten. Sie werden die nächste Stunde damit verbringen, das zu bekommen, was Sie eigentlich wollten.

Ein mittelmäßiger Prompt wie "Schreibe eine Spannungsberechnungsfunktion" verbessert sich auf etwa 50%. Besser—die KI kennt jetzt den Bereich. Aber welche Art von Spannung? Welche Eingaben nimmt die Funktion? Was soll sie zurückgeben? Noch zu viel Raten erforderlich.

Ein präziser Prompt verändert alles. "Schreibe eine Python-Funktion namens berechne_zugspannung, die Kraft in Newton und Fläche in Quadratmillimetern entgegennimmt, Spannung in MPa zurückgibt und einen Fehler auslöst, wenn einer der Eingabewerte negativ ist." Das erreicht eine Erfolgsquote von über 90%. Die KI weiß genau, was sie bauen soll: den Funktionsnamen, die Eingaben, die Ausgabe, die Einheiten, die Fehlerbehandlung—alles ist spezifiziert.

Ja, das Schreiben präziser Prompts kostet im Voraus mehr Zeit. Aber es spart enorm viel Zeit in der Schleife. Würden Sie lieber 2 Minuten für einen guten Prompt aufwenden und funktionierenden Code bekommen, oder 30 Sekunden für einen vagen Prompt und dann 20 Minuten damit verbringen, das zu reparieren, was die KI Ihnen gibt?

<div class="key-insight">
<strong>Kernaussage:</strong> Spezifischere Prompts = Weniger Iterationen = Bessere Ergebnisse.
</div>

---

## Fünf Komponenten eines guten Prompts

Hier ist ein Rahmenwerk für das Erstellen präziser Prompts. Fünf Komponenten, jede fügt Klarheit hinzu.

![Fünf Komponenten](/code-with-ai/assets/images/diagrams/05-2-five-components.png)
{: .chapter-diagram}
*Abbildung 5.2: Fünf Komponenten — Das Rahmenwerk für präzise Prompts*
{: .diagram-caption}

Die erste Komponente ist, was Sie wollen—die Aktion. Das ist das Verb Ihres Prompts: "Erstelle eine Funktion" oder "Behebe diesen Fehler" oder "Erkläre diesen Code." Beginnen Sie mit einer klaren Aktion, damit die KI weiß, welche Art von Antwort Sie brauchen.

Die zweite Komponente ist, wo es passiert—der Ort oder Kontext. Sie könnten sagen "in der utils.py-Datei" oder "in der berechne-Funktion" oder "für diese Datenstruktur." Das sagt der KI, worauf sie ihre Aufmerksamkeit richten soll, und hält die Antwort zielgerichtet.

Die dritte Komponente ist, wie Sie es gemacht haben wollen—die Methode oder der Ansatz. Die Angabe "mit einer for-Schleife" oder "mit Fehlerbehandlung" oder "unter Verwendung der pandas-Bibliothek" schränkt ein, wie die KI das Problem löst. Ohne dies wählt die KI ihren eigenen Ansatz, der möglicherweise nicht zu Ihrer Codebasis passt.

Die vierte Komponente ist, warum Sie es brauchen—der Zweck. Die Erklärung "um die Leistung zu verbessern" oder "für die Benutzervalidierung" oder "um dem bestehenden Codestil zu entsprechen" gibt der KI eine Absicht, an der sie sich orientieren kann. Wenn die KI Ihr Ziel versteht, trifft sie bessere Entscheidungen.

Die fünfte Komponente ist ein Beispiel dessen, was Sie erwarten. Das Zeigen von "Eingabe: [1,2,3], Ausgabe: 6" oder das Sagen "wie diese bestehende Funktion, aber für Temperatur" beseitigt Mehrdeutigkeit bezüglich des gewünschten Ergebnisses. Beispiele sind oft der effektivste Weg, um zu verdeutlichen, was Sie wollen.

Sie brauchen nicht immer alle fünf Komponenten, aber je mehr Sie einbeziehen, desto besser werden Ihre Ergebnisse. Wenn ein Prompt nicht funktioniert, gehen Sie diese Komponenten durch und fügen Sie die hinzu, die Ihnen fehlen.

<div class="key-insight">
<strong>Kernaussage:</strong> Die fünf Komponenten geben Ihnen einen systematischen Weg, jeden Prompt präziser zu machen.
</div>

---

## Probieren Sie es selbst aus

Vergleichen Sie vage vs. präzise Prompts:

- Vage: „Hilf mir bei Mathe" → Präzise: „Schreibe eine Funktion, die Zinseszins berechnet"
- „Erstelle eine Python-Funktion namens zinseszins, die Kapital, Zinssatz (als Dezimalzahl) und Jahre nimmt, den Endbetrag auf 2 Dezimalstellen gerundet zurückgibt"
- „Füge ein Beispiel hinzu: Kapital=1000, Zinssatz=0.05, Jahre=10 sollte 1628.89 ergeben"
- „Füge Fehlerbehandlung für negative Werte hinzu"
- „Füge einen Docstring hinzu, der erklärt, was die Funktion macht"
- „Schreibe einen Testfall, der überprüft, ob die Berechnung korrekt ist"

---

## Kernaussage

Jede Minute, die Sie damit verbringen, Ihren Prompt präziser zu machen, spart fünf Minuten Iteration später. Verwenden Sie die fünf Komponenten—Was, Wo, Wie, Warum und Beispiel—als Checkliste. Wenn die KI Ihnen etwas Falsches gibt, fragen Sie sich: "Wobei war ich nicht spezifisch genug?" Die Antwort liegt fast immer im Prompt.

Im nächsten Kapitel lernen wir, wie man effektives Feedback gibt, wenn der erste Versuch der KI nicht ganz richtig ist.
