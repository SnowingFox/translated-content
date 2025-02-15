---
title: transition-delay
slug: Web/CSS/transition-delay
tags:
  - CSS
  - Propriété
  - Reference
  - Transitions
translation_of: Web/CSS/transition-delay
---
{{CSSRef}}

La propriété **`transition-delay`** indique la durée à attendre avant de débuter la transition qui s'applique pour un changement de propriété.

{{EmbedInteractiveExample("pages/css/transition-delay.html")}}

Cette durée peut être nulle, positive ou négative :

- Une valeur de `0s` ou `0ms` indique que l'animation correspondante démarrera immédiatement lorsque la valeur sera modifiée.
- Une valeur positive permettra d'attendre avant de démarrer l'effet de transition.
- Une valeur négative lancera l'animation immédiatement mais à partir d'un état intermédiaire (comme si la  transition avait déjà commencé).

Il est possible d'indiquer plusieurs valeurs d'attente. Chaque valeur sera appliquée à la propriété correspondante donnée par la liste {{cssxref("transition-property")}} (qui agit comme un index des propriétés concernées par les transitions). S'il n'y a pas suffisamment de valeurs dans cette liste, les valeurs précédentes seront répétées jusqu'à ce qu'il y en ait suffisamment. S'il y a plus de valeurs d'attente que d'éléments dans {{cssxref("transition-property")}}, la liste est simplement tronquée. Dans les deux cas, la déclaration CSS est considérée comme valide.

## Syntaxe

```css
/* Valeurs temporelles */
/* Type <time> */
transition-delay: 3s;
transition-delay: 2s, 4ms;

/* Valeurs globales */
transition-delay: inherit;
transition-delay: initial;
transition-delay: unset;
```

### Valeurs

- `<time>`
  - : Une valeur {{cssxref("&lt;time&gt;")}} qui indique la durée à attendre avant de démarrer l'effet de transition déclenché par le changement de valeur d'une propriété.

### Syntaxe formelle

{{csssyntax}}

## Exemples

### Exemple illustrant différentes temporisations

#### HTML

```html
  <div class="box delay-1">0,5 secondes</div>

  <div class="box delay-2">2 secondes</div>

  <div class="box delay-3">4 secondes</div>

  <button id="change">Changer</button>
```

#### CSS

```css
.box {
  margin: 20px;
  padding: 10px;
  display: inline-block;
  width: 100px;
  height: 100px;
  background-color: red;
  font-size: 18px;
  transition-property: background-color font-size transform color;
  transition-timing-function: ease-in-out;
  transition-duration: 3s;
}

.transformed-state {
  transform: rotate(270deg);
  background-color: blue;
  color: yellow;
  font-size: 12px;
  transition-property: background-color font-size transform color;
  transition-timing-function: ease-in-out;
  transition-duration: 3s;
}

.delay-1 {
  transition-delay: 0.5s;
}

.delay-2 {
  transition-delay: 2s;
}

.delay-3 {
  transition-delay: 4s;
}
```

#### JavaScript

```js
function change() {
  const elements = document.querySelectorAll("div.box");
  for (let element of elements) {
    element.classList.toggle("transformed-state");
  }
}

const changeButton = document.querySelector("#change");
changeButton.addEventListener("click", change);
```

#### Résultat

{{EmbedLiveSample("exemple_illustrant_differentes_temporisations",275,200)}}

## Spécifications

| Spécification                                                                                                | État                                     | Commentaires         |
| ------------------------------------------------------------------------------------------------------------ | ---------------------------------------- | -------------------- |
| {{SpecName('CSS3 Transitions', '#transition-delay-property', 'transition-delay')}} | {{Spec2('CSS3 Transitions')}} | Définition initiale. |

{{cssinfo}}

## Compatibilité des navigateurs

{{Compat("css.properties.transition-delay")}}

## Voir aussi

- [Utiliser les transitions CSS](/fr/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
- L'API {{domxref("TransitionEvent")}}
