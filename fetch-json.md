# Jak działa `fetch()` i wczytywanie danych z pliku JSON?
Źródło: ChatGPT

W tym poradniku wyjaśnimy krok po kroku, jak działa poniższy kod:

```javascript
fetch("./data.json")
  .then(response => response.json())
  .then(data => {
    const summaryList = document.getElementById("summary-list");

    data.forEach(item => {
      const row = document.createElement("div");

      row.classList.add("summary-item");
      row.classList.add(item.category.toLowerCase());

      row.innerHTML = `
        <div class="left">
            <img src="${item.icon}" alt="${item.category}">
            <span>${item.category}</span>
        </div>

        <div class="right">
            <strong>${item.score}</strong> / 100
        </div>
      `;

      summaryList.appendChild(row);
    });
  })
  .catch(error => console.error(error));
```

---

## Krok 1. Pobranie pliku JSON

```javascript
fetch("./data.json")
```

Funkcja `fetch()` służy do pobierania danych z pliku lub z Internetu.

W tym przypadku oznacza:

> Pobierz plik `data.json`, który znajduje się w tym samym folderze co plik HTML.

Na tym etapie JavaScript **jeszcze nie zna zawartości pliku**. Wysłał jedynie prośbę o jego pobranie.

---

## Krok 2. Zamiana odpowiedzi na obiekt JavaScript

```javascript
.then(response => response.json())
```

Po pobraniu pliku otrzymujemy obiekt `response`.

Nie zawiera on jeszcze gotowych danych, dlatego wywołujemy:

```javascript
response.json()
```

Metoda ta zamienia tekst zapisany w formacie JSON na zwykły obiekt lub tablicę JavaScript.

### Przykład

#### data.json

```json
[
  {
    "category": "Reaction",
    "score": 80
  }
]
```

Po wykonaniu:

```javascript
response.json()
```

otrzymujemy:

```javascript
[
  {
    category: "Reaction",
    score: 80
  }
]
```

Teraz możemy korzystać z danych, np.

```javascript
data[0].category
```

wynik:

```
Reaction
```

---

## Krok 3. Otrzymanie danych

```javascript
.then(data => {
```

Zmiennej `data` zostaje przypisana cała zawartość pliku.

Wygląda ona tak:

```javascript
[
  {
    category: "Reaction",
    score: 80,
    icon: "./assets/images/icon-reaction.svg"
  },
  {
    category: "Memory",
    score: 92,
    icon: "./assets/images/icon-memory.svg"
  },
  {
    category: "Verbal",
    score: 61,
    icon: "./assets/images/icon-verbal.svg"
  },
  {
    category: "Visual",
    score: 72,
    icon: "./assets/images/icon-visual.svg"
  }
]
```

Można to przedstawić jako:

```text
data
 │
 ├── element 0
 │      category: Reaction
 │      score: 80
 │
 ├── element 1
 │      category: Memory
 │      score: 92
 │
 ├── element 2
 │      category: Verbal
 │      score: 61
 │
 └── element 3
        category: Visual
        score: 72
```

---

## Krok 4. Znalezienie miejsca w HTML

```javascript
const summaryList = document.getElementById("summary-list");
```

JavaScript wyszukuje element:

```html
<div id="summary-list"></div>
```

i zapisuje go do zmiennej `summaryList`.

Można to rozumieć jako:

> Zapamiętaj miejsce, do którego będę dodawał kolejne elementy.

---

## Krok 5. Przejście po wszystkich elementach tablicy

```javascript
data.forEach(item => {
```

Metoda `forEach()` wykonuje kod dla **każdego elementu tablicy**.

Jest podobna do pętli:

```javascript
for (let i = 0; i < data.length; i++) {

}
```

Podczas pierwszego przebiegu:

```javascript
item = {
    category: "Reaction",
    score: 80,
    icon: "./assets/images/icon-reaction.svg"
}
```

Podczas drugiego:

```javascript
item = {
    category: "Memory",
    score: 92,
    icon: "./assets/images/icon-memory.svg"
}
```

I tak aż do końca tablicy.

---

## Krok 6. Tworzenie nowego elementu HTML

```javascript
const row = document.createElement("div");
```

Powstaje nowy element:

```html
<div></div>
```

Na razie istnieje tylko w pamięci programu i **nie jest jeszcze widoczny na stronie**.

---

## Krok 7. Dodawanie klas CSS

```javascript
row.classList.add("summary-item");
```

Dodaje klasę CSS:

```html
<div class="summary-item"></div>
```

Następnie wykonywana jest kolejna instrukcja:

```javascript
row.classList.add(item.category.toLowerCase());
```

Załóżmy, że aktualny element wygląda tak:

```javascript
item.category
```

wynik:

```
Reaction
```

Metoda:

```javascript
toLowerCase()
```

zamienia wszystkie litery na małe:

```
reaction
```

Ostatecznie otrzymujemy:

```html
<div class="summary-item reaction"></div>
```

Przy następnym elemencie powstanie:

```html
<div class="summary-item memory"></div>
```

Dzięki temu można w CSS nadać każdej kategorii inne kolory.

---

## Krok 8. Wypełnienie elementu HTML

```javascript
row.innerHTML = `
...
`;
```

Właściwość `innerHTML` pozwala wstawić kod HTML do elementu.

Po podstawieniu wartości otrzymujemy np.

```html
<div class="left">
    <img src="./assets/images/icon-reaction.svg" alt="Reaction">
    <span>Reaction</span>
</div>

<div class="right">
    <strong>80</strong> / 100
</div>
```

---

## Krok 9. Co oznacza `${...}`?

Jest to składnia **Template Literals**.

Pozwala wstawiać wartości zmiennych do tekstu.

Przykład:

```javascript
`Wynik: ${item.score}`
```

Jeżeli:

```javascript
item.score = 80
```

to wynik będzie:

```
Wynik: 80
```

Podobnie:

```javascript
${item.icon}
```

zamieni się na:

```
./assets/images/icon-reaction.svg
```

natomiast:

```javascript
${item.category}
```

na:

```
Reaction
```

---

## Krok 10. Dodanie elementu do strony

```javascript
summaryList.appendChild(row);
```

Dodaje utworzony wcześniej element do:

```html
<div id="summary-list"></div>
```

Po pierwszym przebiegu:

```html
<div id="summary-list">

    <div class="summary-item reaction">
        ...
    </div>

</div>
```

Po drugim:

```html
<div id="summary-list">

    <div class="summary-item reaction">...</div>

    <div class="summary-item memory">...</div>

</div>
```

Po wszystkich przebiegach:

```html
<div id="summary-list">

    <div class="summary-item reaction">...</div>
    <div class="summary-item memory">...</div>
    <div class="summary-item verbal">...</div>
    <div class="summary-item visual">...</div>

</div>
```

---

## Krok 11. Obsługa błędów

```javascript
.catch(error => console.error(error));
```

Jeżeli wystąpi błąd, np.:

- plik `data.json` nie istnieje,
- ścieżka jest niepoprawna,
- plik JSON ma błędną składnię,

to komunikat o błędzie zostanie wyświetlony w konsoli przeglądarki.

---

## Schemat działania

```text
Pobierz data.json
        │
        ▼
Zamień JSON na tablicę
        │
        ▼
Przejdź po każdym obiekcie
        │
        ▼
Utwórz nowy <div>
        │
        ▼
Dodaj klasy CSS
        │
        ▼
Wstaw ikonę, nazwę i wynik
        │
        ▼
Dodaj element do strony
        │
        ▼
Powtórz dla kolejnego obiektu
```

---

## Podsumowanie

W tym przykładzie wykorzystaliśmy kilka podstawowych metod JavaScript:

| Metoda | Do czego służy? |
|---------|-----------------|
| `fetch()` | Pobiera plik lub dane z Internetu. |
| `response.json()` | Zamienia JSON na obiekt JavaScript. |
| `forEach()` | Wykonuje kod dla każdego elementu tablicy. |
| `document.createElement()` | Tworzy nowy element HTML. |
| `classList.add()` | Dodaje klasę CSS do elementu. |
| `innerHTML` | Wstawia kod HTML do elementu. |
| `appendChild()` | Dodaje element do strony. |
| `toLowerCase()` | Zamienia tekst na małe litery. |
| `.catch()` | Obsługuje błędy. |

Po zrozumieniu tego przykładu będziesz potrafił dynamicznie tworzyć listy produktów, użytkowników, komentarzy oraz pobierać dane z API.
