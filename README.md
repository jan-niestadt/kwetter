# kwetter

Een testproject voor de INT Vue.js workshop van 11 december 2018.

Handige [voorbereiding voor de workshop](VOORBEREIDEN.md).


## TODO

## Suggesties voor verbeteringen
- voeg een vinkje toe dat switcht tussen light / dark theme
  (dus lichte achtergrond met donkere tekst vs. andersom;
   hint: toggle een css class op de body die andere css-regels activeert)
- maak een zoekformulier die zoekt in berichttekst
- maak een dropdown met alle auteurs erin; als je er een selecteert zie je alleen berichten van die auteur
- zorg dat automatisch elke 10s evt. nieuwe berichten opgehaald worden van de server

### Geavanceerd
- zorg dat #hashtags / @ mentions gekleurd worden in geposte berichten
- zorg dat de tijdvermeldingen "1 minuut geleden", etc. real-time meeveranderen
- gebruik vue-router om zoek/filter-opdrachten elk hun eigen URL te geven.
  dus bijv. /persoon/Frieda toont alleen berichten van Frieda

- koppel aan simpel PHP script om kwetters te persisten


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
