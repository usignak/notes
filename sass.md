# Sass

Sass to rozszerzenie języka CSS, które dodaje funkcjonalności, takich jak zmienne, zagnieżdżanie, mixiny i funkcje. CSS jest językiem, który definiuje wygląd stron internetowych, a Sass ułatwia jego pisanie i organizację. Sass jest kompilowany do CSS, czyli w rezultacie otrzymujemy tradycyjny arkusz stylów CSS, który można używać w przeglądarkach.

## Notatki
- wtyczka Live Sass Compiler sama dodaje prefixy,
- dokumentacja: https://sass-lang.com/documentation/

## Zmienne
Umożliwiają przechowywanie wartości, takich jak kolory, rozmiary czcionek, czy odległości, a następnie ich powtarzanie w kodzie, co ułatwia modyfikację stylów.

```scss
// utworzenie zmiennej
$primaryBtn: colar;

// wykorzystanie utworzonej zmiennej
body {
  background: $primaryBtn;
}
```

## Zagnieżdżanie
Pozwala tworzyć hierarchiczne struktury stylów, co poprawia ich czytelność i organizację.

```scss
header {
  background: coral;

  button {
    background: yellow;

    &:hover {
      background: pink;
    }
  }
}
```

## Importowanie
Umożliwia włączanie fragmentów kodu z innych plików Sass do głównego arkusza stylów, co ułatwia organizację projektu.

```scss
// nowy folder
_header.scss

// importowanie
@import "./header";
```

## Mixins
Funkcje, które pozwalają na opakowanie fragmentów kodu i wielokrotne ich użycie w różnych miejscach arkusza stylów, co zwiększa wydajność i redukuje powtarzanie się kodu.

```scss
// utworzenie
@mixin flexCenter($direction) {
  display: flex;
  flex-direction: $direction;
  align-items: center;
  justify-content: center;
}

// zastosowanie
body {
  @include flexCenter(column);
}
```

## Extend
Umożliwia stosowanie stylów z rodzicielskich elementów do elementów potomnych, co pozwala na efektywne zarządzanie stylem.

```scss
// utworzenie
header {
  height: 100vh;
  background: yellow;
}

// zastosowanie
.contact {
  @extend header;
  background: coral;
}
```

## Funkcje matematyczne
Pozwalają na wykonywanie obliczeń na wartościach, np. dodawanie, odejmowanie, mnożenie i dzielenie.

```scss
contact {
  width: 100px - 20%;
}
```

## Pętle
Umożliwiają iteracyjne generowanie stylów, co jest przydatne przy tworzeniu powtarzalnych struktur.

```scss
$base-color: #036;

@for $i from 1 through 3 {
  ul:nth-child(3n + #{$i}) {
    background-color: lighten($base-color, $i * 5%);
  }
}
```
Efekt w CSS:
```css
ul:nth-child(3n+1) {
  background-color: rgb(0, 63.75, 127.5);
}

ul:nth-child(3n+2) {
  background-color: rgb(0, 76.5, 153);
}

ul:nth-child(3n+3) {
  background-color: rgb(0, 89.25, 178.5);
}
```

## Instrukcje warunkowe
```scss
@if ($screen-size == 'small') {
  .element {
    font-size: 14px;
  }
}
@else if ($screen-size == 'medium') {
  .element {
    font-size: 16px;
  }
}
@else {
  .element {
    font-size: 18px;
  }
}

// przykład
@mixin text-style($size) {  
  font-size: $size;  
  @if ($size < 20px) {    
    color: blue;  
  } @else if ($size > 30px) {    
    color: pink;  
  } @else {    
    color: orange;  
  }
}

header {  
  @include text-style(25px);
}
```

## Funkcje
Umożliwiają wykonywanie obliczeń, manipulację kolorami, a także korzystanie z wbudowanych funkcji, np. do przyciemniania i rozjaśniania kolorów.

```scss
@function multiply($a, $b) {
  @return $a * $b;
}

$width: 10px;
$height: multiply($width, 2);
```
