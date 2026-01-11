---
layout: chapter
title: "Zerlegung"
chapter: 4
part: 2
part_title: "Fähigkeiten"
part_url: "/de/part-2-skills/"
lang: de
dir: ltr
prev: "/de/part-1-foundations/03-operations"
prev_title: "Sechs Operationen"
next: "/de/part-2-skills/05-precision"
next_title: "Präzision"
---

Dies ist die wichtigste Fähigkeit beim Programmieren mit KI: große Dinge in kleine Dinge zerlegen.

![Zerlegung](/code-with-ai/assets/images/diagrams/04-1-decomposition.png)
{: .chapter-diagram}
*Abbildung 4.1: Zerlegung — Große Aufgaben in KI-gerechte Teile aufbrechen*
{: .diagram-caption}

Betrachten Sie diesen Baum. Ganz oben haben Sie eine große Aufgabe: "Erstelle eine Schraubenrechner-App." Wenn Sie das der KI so übergeben, werden Sie etwas bekommen. Aber es wird wahrscheinlich nicht das sein, was Sie wollen. Die Aufgabe ist zu groß, zu vage, zu offen für Interpretationen.

Schauen Sie nun, was passiert, wenn wir sie zerlegen. Diese große Aufgabe gliedert sich in mittlere Aufgaben: Eingabebereich, Berechnungsmodul, Ergebnisanzeige und Dateiverarbeitung. Jede davon gliedert sich in kleine Aufgaben. Der Eingabebereich wird zu "Kraftwert erfassen", "Flächenwert erfassen" und "Eingaben validieren". Das Berechnungsmodul wird zu "Spannung berechnen", "Gegen Grenzwerte prüfen" und "Bestanden/Nicht bestanden ermitteln".

Diese kleinen Aufgaben sind perfekt für die KI. Sie sind spezifisch. Sie sind abgegrenzt. Sie haben klare Ein- und Ausgaben. Jede kann in einem einzigen Satz beschrieben werden, und die KI kann jede einzelne mit nahezu perfekter Genauigkeit ausführen.

Denken Sie daran wie an technische Zeichnungen. Sie geben niemandem eine Skizze auf einer Serviette und sagen "Baue dieses Gebäude." Sie liefern detaillierte Zeichnungen jeder Komponente. Die KI braucht dieselbe Detailgenauigkeit. Je mehr Sie ein Problem aufschlüsseln, bevor Sie die KI bitten, es zu lösen, desto besser werden Ihre Ergebnisse sein.

<div class="key-insight">
<strong>Kernaussage:</strong> Große Aufgaben verwirren die KI. Kleine Aufgaben liefern perfekte Ergebnisse.
</div>

---

## Die Ein-Satz-Regel

Hier ist ein einfacher Test, um zu wissen, ob Ihre Aufgabe die richtige Größe hat.

![Die Regel](/code-with-ai/assets/images/diagrams/04-2-the-rule.png)
{: .chapter-diagram}
*Abbildung 4.2: Die Ein-Satz-Regel — Der Test für richtig bemessene Aufgaben*
{: .diagram-caption}

Fragen Sie sich: "Kann ich diese Aufgabe in EINEM Satz erklären?" Wenn Sie es nicht können, ist die Aufgabe zu groß—zerlegen Sie sie weiter. Wenn Sie es können, ist die Aufgabe genau richtig—geben Sie sie der KI.

Betrachten Sie diese beiden Ansätze für dasselbe Ziel. Der erste sagt "Erstelle mir eine App, die alle unsere Schraubenberechnungen mit einer Benutzeroberfläche, Datenbank und Berichten verarbeitet." Das ist kein einzelner Satz, der eine einzelne Aufgabe beschreibt—das ist ein Absatz, der ein Projekt beschreibt. Die KI wird entweder ablehnen oder etwas Unbrauchbares produzieren.

Der zweite Ansatz sagt "Erstelle eine Funktion, die die Zugspannung aus Kraft und Fläche berechnet." Ein Satz. Eine Aufgabe. Ein klares Ergebnis. Das ist die Art von Prompt, die Ergebnisse liefert.

<div class="key-insight">
<strong>Kernaussage:</strong> Wenn Sie merken, dass Sie einen Absatz schreiben, um zu beschreiben, was Sie wollen, halten Sie inne. Das ist ein Zeichen, dass Sie zuerst zerlegen müssen.
</div>

---

## Probieren Sie es selbst aus

Üben Sie das Aufteilen von Aufgaben:

- „Erstelle eine Funktion, die eine E-Mail-Adresse validiert" (eine Aufgabe)
- „Ich möchte einen Budget-Tracker bauen" → Aufteilen: „Was sind die Hauptteile eines Budget-Trackers?"
- „Erstelle eine Funktion, die prüft, ob ein String das @-Symbol enthält"
- „Erstelle eine Funktion, die prüft, ob Text vor und nach dem @ steht"
- „Kombiniere diese Prüfungen zu einem einfachen E-Mail-Validator"
- „Welche anderen Prüfungen sollte ein vollständiger E-Mail-Validator haben?"

---

## Kernaussage

Zerlegung ist die Schlüsselfähigkeit für das KI-Programmieren. Bevor Sie irgendeinen Prompt schreiben, fragen Sie sich: "Ist diese Aufgabe klein genug?" Wenn Sie sie nicht in einem Satz beschreiben können, zerlegen Sie sie. Bauen Sie Ihre Programme aus kleinen Bausteinen mit einem einzigen Zweck, und die KI wird Ihnen helfen, sie zu etwas Kraftvollem zusammenzusetzen.

Im nächsten Kapitel werden wir uns darauf konzentrieren, jeden dieser kleinen Prompts so präzise wie möglich zu gestalten.
