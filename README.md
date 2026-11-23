# Git Shell Hausaufgabe
Dieses Repository enthält ein kleines Bash-Skript für einfache IT-Support-Aufgaben.

Geübte Git-Themen:
- git add
- git commit
- git push
- git branch
- git checkout
- git merge

## Theoriefragen

### 11. Theorie: Merge-Konflikt verstehen

**Was ist ein Merge-Konflikt?**
Ein Merge-Konflikt tritt auf, wenn Git zwei Branches zusammenführen soll, aber nicht automatisch entscheiden kann, welche Änderung gültig ist. Das passiert immer dann, wenn widersprüchliche Änderungen an derselben Stelle vorliegen. Git stoppt den Vorgang dann und bittet den Entwickler um Hilfe.

**Warum entsteht ein Merge-Konflikt meistens dann, wenn zwei Branches dieselbe Stelle in derselben Datei verändert haben?**
Git arbeitet zeilenbasiert und vergleicht den Zustand der Dateien. Wenn in Branch A und Branch B genau dieselbe Zeile unterschiedlich bearbeitet wurde, weiß Git nicht, welche Version die richtige ist. Deshalb lässt Git den Menschen entscheiden, welcher Code behalten werden soll.

**Warum haben Sie in dieser Aufgabe keinen Merge-Konflikt bekommen?**
Wir haben alle Aufgaben streng nacheinander erledigt. Jeder neue Branch wurde erst erstellt, nachdem der vorherige Branch bereits fertig in den master-Branch gemergt wurde. Dadurch basierte jeder Schritt auf dem aktuellsten Stand und es gab keine parallelen, widersprüchlichen Änderungen.

**Was zeigt Git in einer Datei an, wenn ein Merge-Konflikt entsteht?**
Git fügt spezielle Konfliktmarker direkt in die betroffene Datei ein. Mit `<<<<<<< HEAD` wird der eigene aktuelle Stand markiert, getrennt durch `=======`, und mit `>>>>>>> branch-name` endet der Bereich mit den Änderungen aus dem anderen Branch. So sieht man beide Versionen direkt untereinander.

**Welche Schritte muss man grundsätzlich durchführen, um einen Merge-Konflikt sauber zu lösen?**
Zuerst öffnet man die betroffene Datei und schaut sich die markierten Stellen an. Danach löscht man die Konfliktmarker (`<<<<<<<`, `=======`, `>>>>>>>`) und behält nur den gewünschten Code. Anschließend speichert man die Datei, markiert sie mit `git add` als gelöst und schließt den Vorgang mit `git commit` ab.

**Warum sollte man nach dem Lösen eines Merge-Konflikts das Programm oder Skript noch einmal testen?**
Beim manuellen Zusammenfügen von Code-Teilen passieren leicht Flüchtigkeitsfehler, wie zum Beispiel vergessene Klammern oder gelöschte Variablen. Durch einen erneuten Test stellt man sicher, dass das Skript fehlerfrei läuft und alle Funktionen wie gewünscht zusammenarbeiten.

### 12. Theorie: Merge und Rebase vergleichen

**Was macht git merge?**
`git merge` nimmt alle Änderungen aus einem Branch und führt sie mit dem aktuellen Branch zusammen. Dabei bleibt die komplette Historie beider Branches erhalten und es entsteht in der Regel ein neuer Merge-Commit, der beide Entwicklungsstränge verbindet.

**Was macht git rebase?**
`git rebase` nimmt die Commits eines Branches und setzt sie neu an die Spitze eines anderen Branches. Man kann sich das so vorstellen, als würde man seine Arbeit auf einer neueren Basis komplett neu aufbauen, zum Beispiel wenn man Änderungen aus dem Hauptbranch in seinen eigenen Feature-Branch übernimmt.

**Was ist der wichtigste Unterschied zwischen merge und rebase?**
Bei `merge` bleibt die echte zeitliche Geschichte mit allen Verzweigungen erhalten. Bei `rebase` hingegen wird die Historie umgeschrieben, sodass am Ende eine einzige gerade Linie ohne Verzweigungen entsteht.

**Warum bleibt bei merge oft besser sichtbar, wann ein Branch zusammengeführt wurde?**
Durch den speziellen Merge-Commit sieht man im Verlauf genau, wo ein Feature-Branch abgezweigt ist und an welchem Punkt er wieder in den Hauptbranch integriert wurde. Das macht die Zusammenarbeit in Teams sehr nachvollziehbar.

**Warum kann rebase die Git-Historie sauberer aussehen lassen?**
Da `rebase` keine zusätzlichen Merge-Commits erzeugt und alle Commits einfach hintereinanderreiht, gibt es keine unübersichtlichen Verzweigungen im Verlauf. Das Log liest sich dadurch wie eine lineare Geschichte von Anfang bis Ende.

**Warum sollte man mit rebase vorsichtig sein, wenn ein Branch bereits mit anderen geteilt wurde?**
Weil `rebase` die Commit-Historie umschreibt und neue Commit-IDs vergibt. Wenn andere Teammitglieder bereits auf dem alten Stand weitergearbeitet haben, führt das bei ihnen zu großen Problemen und Konflikten beim Synchronisieren.

**Wann würden Sie eher merge verwenden?**
Ich würde `merge` verwenden, wenn ich auf öffentlichen oder gemeinsam genutzten Branches arbeite oder wenn ich genau nachvollziehen möchte, wann ein bestimmtes Feature in das Hauptprojekt eingeflossen ist.

**Wann könnte rebase sinnvoll sein?**
`rebase` ist besonders sinnvoll, um meinen eigenen lokalen Feature-Branch auf den neuesten Stand des Hauptbranches zu bringen, bevor ich meine Arbeit mit anderen teile.
