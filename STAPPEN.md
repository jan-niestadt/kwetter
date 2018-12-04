# Stappen

## Voorbeeldprojectje Kwetter

1. Invoerveld-component dat van kleur verandert als je teveel (maxLength property) of geen tekens invoert.
2. Tweede component dat weergeeft hoeveel tekens / woorden je hebt ingevoerd, en hoeveel tekens je nog hebt; communicatie via parent-component
   (computed property)
3. MessageList component
4. Post message to list
5. Add username (required input), post time
5. Enter to post message; set focus to input
6. [TODO] Heel simpel PHP backendje, communicatie met axios?
8. (misschien) hoe zou je deze applicatie met vuex implementeren?

## Belangrijk om uit te leggen

### Wat is Vue?
Wat is het precies? 
- framework voor dynamische (evt. single-page) webapplicaties

### Waarom zo'n framework nodig?
Waarom zouden we niet gewoon alles in plain JavaScript of met jQuery doen?
- complexe dynamische pagina's netjes structureren
- ...

### Waarom allerlei extra tools nodig? (npm, etc.)
Tools doen een hoop voor je:
- downloaden, installeren libs
- opzetten nieuw project
- compileren van TypeScript naar JS (babel)
- Evt. ook sass, pack, minify, etc.
- development server runnen
- goeie debugger in de browser

### Vergelijking Angular/React/WebComponents
Waarom hebben we voor Vue gekozen en niet voor de bekendere Angular/React? Of voor bijv. webcomponents met Polymer
- ook goeie keuzes, maar Vue lijkt modernst, cleanst, productiefst, snelst te leren en best gedocumenteerd.
- Webcomponents, Polymer is een interessante ontwikkeling maar nog erg volatile en nog niet het makkelijkst in gebruik. Vue is met zeer vergelijkbare doelen gebouwd en kan ws. uiteindelijk under the hood web components gaan gebruiken, zodat je er toch van profiteert.
- populariteit Vue is snel groeiende
- ...

### Hoe brengt Vue structuur aan?
Wat is het idee achter Vue precies?
- self-contained componenten (HTML, Javascript, CSS) die elkaar niet in de weg zitten
- ...

### Directory/file-structuur
Hoe steekt een compleet maar simpel Vue-project in elkaar?

Filetypes:
- .vue

Dirs/files:
- public/
- src/assets/
- src/components/
- src/App.vue
- src/main.js
