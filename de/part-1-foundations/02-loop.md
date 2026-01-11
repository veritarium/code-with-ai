---
layout: chapter
title: "Die Schleife"
chapter: 2
part: 1
part_title: "Grundlagen"
part_url: "/de/part-1-foundations/"
lang: de
dir: ltr
prev: "/de/part-1-foundations/01-core"
prev_title: "Die Kernpartnerschaft"
next: "/de/part-1-foundations/03-operations"
next_title: "Sechs Operationen"
---

So funktioniert jede Programmiersitzung mit KI tatsächlich. Prägen Sie sich diese Schleife ein.

![Die Schleife](/code-with-ai/assets/images/diagrams/02-1-the-loop.png)
{: .chapter-diagram}
*Abbildung 2.1: Die Schleife — Beschreiben, Erhalten, Ausführen, Bewerten, Wiederholen*
{: .diagram-caption}

Die Schleife hat fünf Schritte, die Sie ständig wiederholen werden. Zuerst **BESCHREIBEN** Sie der KI, was Sie wollen. Etwas wie „Erstelle eine Funktion, die die Schraubenspannung aus Kraft und Fläche berechnet." Dann gibt Ihnen die KI Code — der **ERHALTEN**-Schritt. Der Code könnte perfekt sein. Wahrscheinlich wird er es nicht sein.

Als nächstes kommt der entscheidende Schritt, den die meisten Anfänger überspringen: **AUSFÜHREN**. Sie führen den Code tatsächlich aus. Nicht nur ansehen. Nicht nur annehmen, dass er funktioniert. Führen Sie ihn mit echten Eingaben aus und sehen Sie, was passiert.

Dann **BEWERTEN** Sie. Funktioniert er? Macht er das, was Sie wollten? Hier ist Ihr ingenieurmäßiges Urteilsvermögen am wichtigsten. Die KI weiß nicht, ob das Ergebnis für Ihre Anwendung sinnvoll ist — Sie wissen es. Eine Spannungsberechnung, die negative Megapascal zurückgibt, könnte syntaktisch korrekt, aber physikalisch bedeutungslos sein.

Schließlich treffen Sie eine Entscheidung: **Fertig oder Verfeinern?** Wenn es funktioniert, sind Sie fertig. Weitermachen. Wenn nicht, gehen Sie zurück zu BESCHREIBEN mit mehr Informationen. „Die Funktion funktioniert, aber gibt negative Werte zurück, wenn die Kraft negativ ist. Füge eine Validierung hinzu, um negative Eingaben abzulehnen." Diese Schleife könnte einmal durchlaufen werden. Sie könnte zehnmal durchlaufen werden. Das ist normal. Jeder professionelle Entwickler arbeitet so — der einzige Unterschied ist, dass sie mehr Schleifen durchlaufen haben.

<div class="key-insight">
<strong>Wichtige Erkenntnis:</strong> Jedes Problem ist durch Iteration lösbar. Sie müssen es nicht beim ersten Mal richtig machen. Sie müssen weitermachen, bis es richtig ist.
</div>

---

## Die Entwurfs-Denkweise

Hier liegt der größte Fehler der meisten Anfänger: Sie erwarten Perfektion beim ersten Versuch.

![Der Entwurf](/code-with-ai/assets/images/diagrams/02-2-the-draft.png)
{: .chapter-diagram}
*Abbildung 2.2: Der Entwurf — Fortschritt durch Iteration*
{: .diagram-caption}

Schauen Sie sich diesen Verlauf an. Version 1 ist vielleicht 10% von dem, was Sie wollen. Sie ist roh. Sie läuft vielleicht nicht einmal. Das ist in Ordnung. Das ist der *Entwurf*. Version 2 bringt Sie auf 40% — jetzt funktioniert die Grundstruktur, aber vielleicht ist das Ausgabeformat falsch. Version 3 erreicht 75% — sie führt die richtige Berechnung durch, behandelt aber keine Randfälle. Version 4 erreicht 100%. Sie funktioniert. Fertig zum Einsatz.

Wenn Sie einen Ingenieurbericht schreiben, erwarten Sie dann, dass der erste Entwurf perfekt ist? Natürlich nicht. Sie schreiben, überprüfen, überarbeiten, wiederholen. Code funktioniert genauso. Die erste Ausgabe der KI ist ein Ausgangspunkt, keine endgültige Antwort. Ihre Aufgabe ist es, sie zu testen, zu identifizieren, was falsch ist, und die Verfeinerung zu leiten.

Dieser Perspektivwechsel ist entscheidend. Hören Sie auf zu fragen „Warum hat mir die KI keinen perfekten Code gegeben?" und beginnen Sie zu fragen „Was muss ich der KI sagen, um das zu verbessern?"

<div class="key-insight">
<strong>Wichtige Erkenntnis:</strong> Behandeln Sie KI-Ausgaben wie einen ersten Entwurf, nicht wie eine endgültige Antwort.
</div>

---

## Probieren Sie es selbst aus

Üben Sie die Schleife mit diesen Prompts:

- „Erstelle eine Funktion, die die Fläche eines Kreises berechnet"
- „Die Funktion gibt 0 für alle Eingaben zurück — was ist falsch?"
- „Füge jetzt eine Validierung hinzu, um negative Radiuswerte abzulehnen"
- „Ändere die Ausgabe, um die Einheiten (Quadratmeter) einzuschließen"
- „Der Code stürzt ab, wenn ich Text statt einer Zahl eingebe — repariere das"
- „Füge eine zweite Funktion hinzu, die den Umfang berechnet"

---

## Wichtigste Erkenntnis

Die Schleife ist Ihr grundlegender Arbeitsablauf. Jedes Mal, wenn Sie mit KI arbeiten, werden Sie beschreiben, was Sie wollen, Code erhalten, ihn ausführen, bewerten, ob er funktioniert, und entweder fertig werden oder verfeinern. Erwarten Sie mehrere Iterationen. Planen Sie dafür. Das Ziel ist nicht perfekter Code beim ersten Versuch — es ist funktionierender Code nach genügend Schleifen.

Im nächsten Kapitel werden wir alle verschiedenen Arten von Operationen kategorisieren, die Sie in dieser Schleife durchführen können.

