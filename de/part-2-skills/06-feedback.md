---
layout: chapter
title: "Feedback"
chapter: 6
part: 2
part_title: "Fähigkeiten"
part_url: "/de/part-2-skills/"
lang: de
dir: ltr
prev: "/de/part-2-skills/05-precision"
prev_title: "Präzision"
next: "/de/part-2-skills/07-context"
next_title: "Kontext"
---

Die KI hat Ihnen etwas gegeben. Es ist nicht ganz richtig. Was sagen Sie als Nächstes?

Hier scheitern die meisten Anfänger. Sie geben schlechtes Feedback und wundern sich dann, warum die KI ihnen immer wieder falsche Antworten gibt.

![Gutes vs. schlechtes Feedback](/code-with-ai/assets/images/diagrams/06-1-good-vs-bad.png)
{: .chapter-diagram}
*Abbildung 6.1: Gutes vs. schlechtes Feedback — Was funktioniert und was nicht*
{: .diagram-caption}

Schlechtes Feedback lässt die KI raten. "Es funktioniert nicht" sagt der KI nichts darüber, was falsch ist—funktioniert nicht wie? Was ist passiert? Was haben Sie erwartet? "Das ist falsch" wirft die Frage auf: Falsch wie? Was ist das korrekte Verhalten? "Reparier es" gibt keine Richtung—was reparieren? Die KI wird raten, und sie wird falsch raten. "Das ist nicht das, was ich wollte" führt zur Frage: Was WOLLTEN Sie dann? Die KI kann keine Gedanken lesen.

Gutes Feedback ist spezifisch und umsetzbar. "Bekomme Fehler: TypeError in Zeile 15" sagt der KI genau, wo sie schauen soll. "Ausgabe ist 5, sollte aber 10 sein" definiert die Lücke, die die KI schließen muss. "Ändere die Schleife, sodass sie bei 1 beginnt, nicht bei 0" gibt der KI die genaue Modifikation vor. "Füge Validierung hinzu: negative Zahlen ablehnen" spezifiziert die neue Anforderung klar.

Erkennen Sie das Muster? Gutes Feedback sagt der KI genau, was falsch ist, und schlägt oft vor, was geändert werden muss. Je mehr Informationen Sie bereitstellen, desto schneller kommen Sie zu funktionierendem Code.

<div class="key-insight">
<strong>Kernaussage:</strong> Spezifisches Feedback → Spezifische Korrekturen → Schneller fertig.
</div>

---

## Die Feedback-Formel

Hier ist eine Formel, die Sie jedes Mal verwenden können, wenn die KI Ihnen etwas gibt, das nicht ganz richtig ist.

![Die Formel](/code-with-ai/assets/images/diagrams/06-2-the-formula.png)
{: .chapter-diagram}
*Abbildung 6.2: Die Feedback-Formel — Bekommen X, Erwartet Y, Ändere Z*
{: .diagram-caption}

Die Formel ist einfach: **"Bekommen [X]. Erwartet [Y]. Ändere [Z]."** Drei Teile. Vollständige Information. Sofortige Korrektur.

Der erste Teil beschreibt, was tatsächlich passiert ist—die aktuelle Ausgabe, die Fehlermeldung, das aktuelle Verhalten, das Sie sehen. Seien Sie hier spezifisch. Kopieren Sie exakte Werte und Meldungen, anstatt sie zu paraphrasieren.

Der zweite Teil beschreibt, was stattdessen passieren sollte—die korrekte Ausgabe, das gewünschte Verhalten, das erwartete Ergebnis. Das gibt der KI ein klares Ziel. Ohne zu wissen, was Sie wollten, kann die KI nicht erkennen, was geändert werden muss.

Der dritte Teil schlägt vor, was geändert werden soll—die spezifische Korrektur, welcher Teil geändert werden soll, welche Operation stattdessen verwendet werden soll. Dieser Teil ist optional, aber hilfreich, wenn Sie eine Ahnung haben, was falsch ist. Selbst eine Vermutung hilft der KI, das Problem einzugrenzen.

Hier ist ein Beispiel in Aktion. Sie bitten die KI um eine Funktion, die das Produkt einer Liste berechnet, und sie gibt Ihnen etwas, das 15 für die Eingabe [1, 2, 3, 4, 5] zurückgibt. Sie wissen, das Produkt sollte 120 sein. Mit der Formel: "Die Funktion gibt 15 für Eingabe [1,2,3,4,5] zurück, sollte aber 120 zurückgeben—sie berechnet die Summe anstelle des Produkts. Ändere die Addition zu Multiplikation in der Schleife."

Die KI hat jetzt alles, was sie braucht. Eine Antwort, fertig.

<div class="key-insight">
<strong>Kernaussage:</strong> Vollständige Information = Korrektur auf Anhieb.
</div>

---

## Probieren Sie es selbst aus

Üben Sie gutes Feedback zu geben:

- Schlecht: „Es funktioniert nicht" → Gut: „Die Funktion gibt None zurück statt einer Zahl"
- „Bekommen 15, erwartet 120 — die Funktion addiert statt zu multiplizieren"
- „Fehler: IndexError in Zeile 8 — die Schleife geht einen Schritt zu weit"
- „Das Ausgabeformat ist ‚5.0', aber ich brauche ‚5.00' mit genau zwei Dezimalstellen"
- „Ergebnisse sind korrekt, aber zu langsam — 10 Sekunden für 1000 Elemente"
- „Die Funktion funktioniert, stürzt aber ab, wenn die Eingabeliste leer ist — füge eine Prüfung dafür hinzu"

---

## Kernaussage

Wenn die KI Ihnen etwas Falsches gibt, widerstehen Sie dem Drang zu sagen "reparier es" und verwenden Sie stattdessen die Formel: Bekommen [X], Erwartet [Y], Ändere [Z]. Je spezifischer Ihr Feedback, desto schneller kann die KI das Problem korrigieren. Jede Information, die Sie bereitstellen, eliminiert Raten und bringt Sie näher ans Ziel.

Im nächsten Kapitel werden wir erkunden, wie Sie der KI den Kontext geben, den sie braucht, um Ihr Problem vollständig zu verstehen.
