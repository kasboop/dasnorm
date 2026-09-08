# Das Norm — Website-Template

Rein statisches Template (HTML, CSS, kein Build-Schritt, kein JavaScript nötig).
Einfach den ganzen Ordner per FTP/rsync auf den eigenen Server kopieren.

## Struktur

```
index.html               Startseite mit Bildraster (alle Projekte)
motion.html               Rubrikseite Motion
graphic.html               Rubrikseite Graphic
lab.html                   Rubrikseite Lab (noch Platzhalter)
teach.html                 Rubrikseite Teach (noch Platzhalter)
bio.html                    Bio-/Über-uns-Text
projekte/
  motion-1.html            Projektseite zu motion1.png: Beschrieb (1/3 Liste, 2/3 Text), Video, 3 Bilder
  beispielprojekt-a.html  Projektseite, lang (2 Bilder, 2 Videos)
  beispielprojekt-b.html  Projektseite, kurz (1 Bild, 1 Video)
css/style.css             Alle Design-Tokens und Layouts an einem Ort
images/                   Eigene Bilder hier ablegen
videos/                   Eigene Videos hier ablegen (.mp4)
```

## Die 5 Rubriken

Motion, Graphic, Lab, Teach, Bio — verlinkt als eigenständige Seiten in der
Navigation (`<div class="nav__rubriken">`), identisch auf jeder Seite. Bio ist als
Text-/Über-uns-Seite angelegt, die anderen vier als Bildraster.

Neue Rubrik umbenennen: den Linktext und `href` in `.nav__rubriken` auf **jeder**
HTML-Seite anpassen (kein zentrales Include, da rein statisch).

## Neues Projekt hinzufügen

1. `projekte/beispielprojekt-b.html` kopieren, umbenennen, Titel/Text/Rubrik/Jahr anpassen.
2. Eigene Bilder/Videos einbinden: `.projekt-block__bild-wrap`/`.projekt-block__video-wrap`
   entsprechend anpassen.
3. Auf der passenden Rubrikseite (z. B. `graphic.html`) eine neue `.kachel` mit Link auf
   die neue Seite ergänzen.
4. Vor/Zurück-Links im `.projekt-fuss` der betroffenen Seiten nachführen.

## Bilder

`motion.html` und `graphic.html` verwenden bereits eigenes Bildmaterial
(`../images/motion1.png` … `print4.png`). `lab.html` und `teach.html` haben noch
hochformatige Platzhalter von [placehold.co](https://placehold.co) — `src` dort
einfach durch `../images/dateiname.jpg` ersetzen, sobald Material vorliegt.

Achtung Pfad: Aktuell zeigen die Bild-Pfade auf `../images/...`, also eine Ebene
**oberhalb** des Website-Ordners. Falls die Bilder stattdessen im mitgelieferten
`images/`-Ordner **innerhalb** der Website liegen sollen, die Pfade auf
`images/dateiname.png` (ohne `../`) ändern.

Alle Bilder haben einen grünen 20px-Rahmen (`--border-gruen` in `css/style.css`,
aktuell `#22a559`) sowie beim Hover einen mittig zentrierten Projekttitel
(`.kachel__titel`). Das `.kachel__rubrik`-Label existiert im Markup weiterhin, ist
aber per CSS ausgeblendet.

## Videos in den Projektseiten

Als Platzhalter ist überall dasselbe Vimeo-Video eingebettet
(`.projekt-block__video-wrap` mit `<iframe src="https://player.vimeo.com/video/1068776751">`).
Für eigenes Material entweder die Vimeo-ID im `iframe`-src durch die eigene ersetzen,
oder den `iframe` ganz durch ein lokales `<video controls><source src="../videos/dateiname.mp4"></video>`
ersetzen.

## Schrift

Aktuell per Google Fonts eingebunden (`Rubik`). Für einen Server ohne externe
Anfragen: Schriftdateien selbst hosten und die `<link>`-Tags in jeder HTML-Datei durch
ein lokales `@font-face` in `style.css` ersetzen.
