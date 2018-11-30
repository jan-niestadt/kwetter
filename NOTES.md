# Notes about learning Vue

## Difficult

### Props vs. data properties

Wat is het verschil tussen props en data properties?

Props 'stromen' alleen van parent component naar child components; als de parent de waarde verandert, verandert die automatisch ook in het child component, maar andersom niet. 

Wijzig dus geen props in het child component. Vue geeft een warning als je dat doet en het doet waarschijnlijk niet wat je wilt. Als je in het cihld component een veranderlijke waarde wilt bijhouden, doe dat dan in een data property.

(see https://vuejs.org/v2/guide/components-props.html)

### Data binding: v-bind and v-model

Wat is het verschil tussen v-bind en v-model?

v-bind is eenrichtingverkeer, v-model tweerichtingverkeer. Maar als je v-model op je eigen componenten wilt gebruiken, moet je wel zelf specificeren hoe het tweerichtingverkeer werkt (d.m.v. events).

### Two-way binding

Hoe deel je eenvoudig variabele data tussen componenten? (bijv. typ bericht in 1 component, ander component toont het)

Alles via events, die door de parent kunnen worden opgepakt.


## Vragen

- Waarom mag je console niet gebruiken? Meest praktische manier om hier tijdens debuggen geen last van te hebben?
- Wat is de correcte manier om de focus op een element te zetten? Werkt in post() method maar niet vanuit mounted() handler.
  Ook niet als je met nextTick of setTimeout werkt...
  Algemener: hoe refereer je naar een bepaald HTML-element binnen je template? Nu met .children[0] gedaan, maar is niet zo elegant
- 