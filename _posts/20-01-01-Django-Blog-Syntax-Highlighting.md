---
title: Code Blocks und Syntax Highlighting
fname: django_blog_syntax_highlight
category: tutorial
---

Um Codeschnippsel darzustellen werden im Internet normalerweise `<pre></pre>` bzw. `<code></code> Blöcke verwendet, da darin Zeilenumrüche und Einrückungen erhalten bleiben. Um diese Blöcke hervorzuheben, können sie eingerahmt oder mit einer anderen Hintergrundfarbe versehen werden. Besonders zur Geltung und besser lesbar wird der Code, wenn dessen Syntax noch durch die verwendung verschiedener Farben unterstrichen wird. Dieser Artikel enthält verschiedene Möglichkeiten, die Syntax von Code verschiedener Sprachen automatisch hervorzuheben.

## Client

Eine häufig verwendete Möglichkeit ist es, das Analysieren des Codes dem Browser des Besuchers zu überlassen. Beim Besuch der Seite wird der Post (mit samt dem Code-Block) als html-Seite heruntergeladen. Zusätzlich erhält der Browser des Besuchers ein JavaScript, das der Browser ausführt, um den Code in bestimmten Bereichen bunt zu färben. 

Diese Methode verschiebt etwas Arbeit vom Server auf den Client und macht die Erstellung der Code-Blöcke sehr einfach.



### prism.js

### syntaxhighlighter

http://alexgorbatchev.com/SyntaxHighlighter/

### prettify

https://github.com/google/code-prettify

themes: https://rawgit.com/google/code-prettify/master/styles/index.html

jquery extension die prettify benutzt:

http://balupton.github.io/jquery-syntaxhighlighter/demo/

### rainbow

https://craig.is/making/rainbows

### highlight.js

https://highlightjs.org/usage/

Highlighted automatisch `<pre><code></code></pre>` Bereiche und kann mit `class="nohighlight"` deaktiviert werden. Es passt damit direkt zur html Ausgabe vom `markdown` Paket, dass zum generieren der Posts aus `.md`-Dateien im Kapitel (TODO: link) verwendet wurde.

Es ist zur einfachen Verwendung mit üblichen Sprachen über ein CDN ohne Installation bereit zur Benutzung:

```html
<link rel="stylesheet"
      href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/styles/default.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.12.0/highlight.min.js"></script>
```



## Server

Damit auch Nutzer ohne JavaScript in den Genuss von gefärbten Source Code kommen, bietet sich die Alternative, den Code schon auf dem Server hervorzuheben und in den html-Code der Seite einzubetten. 

### CodeHilite

Source: http://pythonhosted.org/Markdown/extensions/code_hilite.html

Speziell in diesem Fall bei einem Django- und Markdown-basierten Blog, klingt doch eine Erweiterung fürs markdown Modul in python (das ohnehin schon verwendet wird) nach einer super Möglichkeit.

Die Erweiterung selbst ist bereits im Markdown-Modul enthalten, um es richtig nutzen zu können, ist allerdings das paket `pygmentize` notwendig. Dieses Paket kann außerdem verwendet werden, um CSS-Dateien nach verschiedenen Themes zu generieren. Dazu ist nur ein einziger Befehl nötig:

`pygmentize -S default -f html -a .codehilite > syntax.css`

Auch wenn der Code nicht serverseitig aufbereitet werden soll, ist diese Extension, sofern Markdown als Quelle verwendet wird, auch in Kombination mit JavaSctipt Highlightern sinnvoll. Mit der `use_pygments = False` Option ist keine pygements Installation auf dem Server erforderlich und die im Markdown (Fences) definierte Sprache wird als Klasse ans `<code>`-Tag weitergegeben.

Bei der Verwendung der Markdown-Klasse muss in den Extensions-Array lediglich `markdown.extensions.codehilite` aufgenommen werden, dann führt die Ausgabe mit der `convert`-Methode automatisch zum bunten Code beim Besucher. Ganz ohne JS:

```python
extensions = ['markdown.extensions.meta',
	'markdown.extensions.extra',      
	'markdown.extensions.codehilite', ]            
md = markdown.Markdown(extensions=extensions)   
html = md.convert(markdown_string)   
```

Der html-Code kann dann nach Django-Manier direkt in ein Template eingepflanzt werden, in dem die css-Datei eingebunden ist.