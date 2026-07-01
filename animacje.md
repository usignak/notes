# Animacje

## Przydatny kod
```css
transform: translate3d(0, -6rem, 0); /* przesunie element z góry w dół */
transform: translate3d(0, 6rem, 0); /* przesunie element z dołu w górę */
transform: translate3d(-6rem, 0, 0); /* przesunie element od lewej do prawej */
transform: translate3d(6rem, 0, 0); /* przesunie element od prawej do lewej */

animation: 2s linear nazwa_animacji; /* sprawi, że np. koło będzie się kręciło bez przerw */
```

## Tworzenie animacji
Istnieją dwa sposoby tworzenia animacji w CSS:

- przejścia (transitions) - proste animacje, które są zależne od interakcji z użytkownikiem, np. najechaniem przez niego myszką na element,
- animacje (animations) - złożone animacje, które działają bez interakcji użytkownika.

### Transitions
Przejścia wykonuje się na elemencie, którym manipuluje się za pomocą transition i np. transform: translateY(-10px).

```css
.btn {
  transition: transition-property transition-duration transition-timing-function transition-delay;
}
```

- `transition-property` (właściwość przejścia) - określa, do której właściwości powinien zostać zastosowany, np. transform,
- `transition-duration` - czas trwania przejścia, czyli ile powinien trwać efekt, np. 0.3s,
- `transition-timing-function` (funkcja czasu przejścia) - definiuje krzywą przyspieszenia przejścia, może przyjmować wartości: ease (wartość domyślna), ease-in, ease-out, ease-in-out, linear,
- `transition-delay` - opóźnienie rozpoczęcia się przejścia.

### Animations
Animacje wykonuje się na elemencie, którym manipuluje się za pomocą `@keyframes`.

```css
@keyframes nazwa_animacji {
  from {
    /* kod, który ma się wykonać na początku animacji */
  } to {
    /* kod, który ma się wykonać na końcu animacji */
  }
}

.item {
  animation: animation-name animation-duration animation-timing-function animation-delay animation-iteration-count animation-direction animation-fill-mode;
}
```

- `animation-name` - nazwa animacji,
- `animation-duration` - czas trwania animacji,
- `animation-timing-function` - określa krzywą przyśpieszenia animacji, może przyjmować wartości: ease (wartość domyślna), ease-in, ease-out, ease-in-out, linear,
- `animation-delay` - opóźnienie animacji,
- `animation-iteration-count` - określa ile razy ma zostać uruchomiona animacja, może przyjmować wartości: 1 (domyślna), liczby inne niż 1, infinite (nieskończoność),
- `animation-direction` - określa czy animacja będzie działać normalnie, czy odwrotnie, może przyjmować wartości: normal, reverse,
- `animation-fill-mode` - tryb wypełnienia animacji określa, w jaki sposób animacja zastosuje style z naszej klatki kluczowej przed i po jej wykonaniu, może przyjmować wartości:
    - none,
    - forwards - animowany element zatrzyma się na ostatniej klatce, bez względu na jego style,
    - backwards - animowany element zatrzyma się na pierwszej klatce, bez względu na jego style,
    - both - animowany element zatrzyma się pomiędzy klatkami bez względu na jego style.
