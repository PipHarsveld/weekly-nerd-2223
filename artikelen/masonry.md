# Masonry explained: Een duik in CSS- en JavaScript-Lay-outtechnieken
Tijdens mijn meesterproef heb ik mij verdiept in masonry en heb ik zowel CSS masonry gebruikt als JavaScript masonry. In dit artikel leg ik uit wat masonry is, hoe het werkt en hoe je het kunt implementeren in je eigen projecten.

## Wat is masonry?
Masonry is een bepaalde lay-out vorm om een grid te tonen, waarbij de hoogte of breedte van de elementen over één as variabel zijn. De bekendste vorm van Masonry is wanneer de elementen een vaste breedte hebben, maar de elementen een verschillende hoogte. Bij een normaal grid komen er dan witruimtes onder de elementen die een kleinere hoogte hebben, aangezien alle elementen in een rij op dezelfde hoogte beginnen. Bij Masonry begint een element in de kolom meteen op het punt waar het vorige element eindigt, waardoor er geen witruimtes ontstaan en het grid er strakker uitziet.

De term Masonry is afgeleid van metselwerk, waarbij de stenen in een muur ook over één as variabel zijn. Hierbij zijn dan de rijen gelijk en verschillen de kolommen, terwijl in web vaak de kolommen gelijk zijn en de breedte van de rijen verschilt.

Masonry is een techniek die al langer bestaat, maar de laatste jaren steeds populairder is geworden. Dit komt doordat er steeds meer websites zijn die gebruik maken van een grid, waarbij de elementen een variabele hoogte hebben. Denk hierbij aan websites zoals [Pinterest](https://www.pinterest.com/), waarbij de elementen een variabele hoogte hebben en er geen witruimtes ontstaan tussen de elementen.


## Masonry met CSS Grid Layout
Sinds de komst van CSS Grid Layout is het mogelijk om Masonry te maken met alleen CSS. Dit is mogelijk door de `grid-auto-flow` property te gebruiken. Deze property bepaalt hoe de elementen in een grid worden geplaatst. De standaard waarde is `row`, wat betekent dat de elementen in een grid van links naar rechts en van boven naar beneden worden geplaatst. Wanneer je de waarde `column` gebruikt, worden de elementen van boven naar beneden en van links naar rechts geplaatst. Hierdoor ontstaat er een Masonry grid, waarbij de elementen in de kolommen van boven naar beneden worden geplaatst en de breedte van de rijen variabel is.

Mocht je aan de slag willen met een masonry grid in CSS, dan is het belangrijk om te weten dat dit nog niet volledig overal ondersteund is. Op dit moment is het nog alleen bruikbaar in Firefox, nadat je een developer flag hebt aangezet. Om dit te doen zoek je naar `about:config` in je zoekbalk en zoek je naar `layout.css.grid-template-masonry-value.enabled`. Deze zet je op `true` en dan kun je aan de slag! Met de paar onderstaande regels code kun je al een basis grid maken met CSS masonry.

```css
.container {
  display: grid;
  gap: 10px;
  grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
  grid-template-rows: masonry;
}
```
<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="wvQWaLE" data-user="pipharsveld" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/pipharsveld/pen/wvQWaLE">
  Css masonry</a> by Pip (<a href="https://codepen.io/pipharsveld">@pipharsveld</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## Masonry met JavaScript
Aangezien CSS grid nog niet overal ondersteund wordt, kan het handig zijn om na te denken over bijvoorbeeld een javascript library als fallback. Hopelijk wordt CSS in de toekomst meer ondersteund en is dit niet meer nodig, maar tot die tijd is het fijn als alle gebruikers dezelfde ervaring kunnen krijgen. Er zijn verschillende javascript libraries die je kunt gebruiken om een masonry grid te maken. Voor mijn project in de meesterproef heb ik gebruik gemaakt van [Masonry.js](https://masonry.desandro.com/) van David Desandro. Ik moest eerst goed kijken hoe ik kon werken met deze library want ik vond de documentatie niet heel duidelijk, maar met een tutorial is het uiteindelijk gelukt om een masonry grid te maken. Hieronder een voorbeeld van hoe je Masonry.js kunt gebruiken.

```js


```


## Conslusie


## Bronnen
* [Native CSS masonry layout in CSS grid](https://www.smashingmagazine.com/native-css-masonry-layout-css-grid/)
* [Piecing together approaches for a CSS masonry layout](https://css-tricks.com/piecing-together-approaches-for-a-css-masonry-layout/)
* [Masonry Layout mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Masonry_layout)


