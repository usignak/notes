# HTML

## Definicja

**HTML (HyperText Markup Language)** to podstawowy język do tworzenia stron internetowych. Nie jest językiem programowania, a językiem znaczników, który służy do opisania struktury strony.

## Struktura pliku index.html

```html
<!DOCTYPE html>
<html lang="pl">
  <head>
    <title>Tytuł strony</title>
  </head>
  <body>
    ...
  </body>
</html>
```
Gdzie:
- `<!DOCTYPE html>` - informuje przeglądarkę, że używamy kodu HTML 5,
- `<head>` - służy do przekazania stronie informacji takich jak tytuł strony, opis, słowa kluczowe,
- `<body>` - zawiera całą treść, która będzie wyświetlana w przeglądarce.

## Elementy i tagi w HTML
Elementy w HTML to paragrafy, nagłówki, obrazy oraz inne bazowe bloki z HTML.

```html
<button class="box">Send message</button>
```
Gdzie:
- `<button class="box">Send message</button>` - element,
- `Send message` - treść elementu,
- `<button>` - tag otwierający,
- `</button>` - tag zamykający,
- `class="box"` - atrybut class o wartości box.

## Linki

```html
<a href="https://example.com">Kliknij tutaj</a>
```

## Obrazy

```html
<img src="sciezka.jpg" alt="Opis alternatywny" width="300" />
```

## Listy
- Uporządkowana: `<ol><li>Element</li></ol>`,
- Nieuporządkowana: `<ul><li>Element</li></ul>`,
- Zagnieżdżanie list: można umieszczać listy w środku innych list.

## Komentarze

```html
<!-- komentarz -->
```

## Elementy liniowe i blokowe w HTML

**Elementy blokowe** zajmują całą możliwą dla siebie przestrzeń, natomiast **elementy linowe** tylko tyle ile jej potrzebują.
- popularne elementy blokowe: blockquote, div, figure, form, h1 - h6, hr, li, ol, ul, p, table,
- popularne elementy liniowe: a, button, em, img, input, label, small, span, strong.

## Tabele

```html
<table border="1">

  <thead>
    <tr>
      <th scope="col">Nagłówek 1</th>
      <th scope="col">Nagłówek 2</th>
      <th scope="col">Nagłówek 3</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Wiersz 1, kolumna 1</td>
	  <td>Wiersz 1, kolumna 2</td>
	  <td>Wiersz 1, kolumna 3</td>
    </tr>
	<tr>
      <td>Wiersz 2, kolumna 1</td>
      <td>Wiersz 2, kolumna 2</td>
	  <td>Wiersz 2, kolumna 3</td>
    </tr>
    <tr>
      <td>Wiersz 3, kolumna 1</td>
	  <td>Wiersz 3, kolumna 2</td>
	  <td>Wiersz 3, kolumna 3</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Podsumowanie kolumny 1</td>
      <td colspan="2">Podsumowanie łącznie kolumn 2 i 3</td>
    </tr>
  </tfoot>

</table>
```
Gdzie:
- `<table>` - tabela,
- `<tr>` - wiersz,
- `<td>` - komórka,
- `<th>` - komórka nagłówka,
- `scope="col"` lub `scope="row"` - wskazuje, czy nagłówek (th) dotyczy kolumny czy wiersza,
- `colspan="2"` lub `rowspan="2"` - łączenie kolumn lub wierszy.

### Responsywna tabela

```html
<div style="overflow-x:auto;">
  <table>
    <!-- zawartość tabeli -->
  </table>
</div>
```

## Formularze

```html
<form action="" method="">
  <div>
    <label for="login-email">Email address</label>
    <input type="email" name="login-email" id="login-email" value="hello@email.com">
  </div>
  <div>
    <label for="comments">Comments</label>
    <textarea name="comments" id="comments" cols="30" rows="10"></textarea>
  </div>
</form>
```
Gdzie:
- `action` - ścieżka do pliku, który otrzyma informacje z wypełnionego formularza, np. `action="contact.php"`,
- `method` - metoda przesłania formularza, np. GET (dane pokazują się w URL, więc widać też np. hasło), POST (bezpieczniejszy sposób i zalecany),
- `name` - jest używany do wysyłania informacji z formularza (w przypadku checkbox i radio wszystkie pola muszą mieć to samo name),
- `value` - przypisana wartość dla inputa (w przypadku checkboxa i radio służy do pobrania konkretnych danych).

### Typy pól formularza

- `text`: pole tekstowe do wprowadzania krótkich tekstów,
- `password`: pole do wprowadzania haseł, gdzie wpisany tekst jest ukryty,
- `email`: pole do wprowadzania adresu e-mail,
- `number`: pole liczbowe,
- `tel`: pole do wprowadzania numeru telefonu,
- `date`: pole do wyboru daty,
- `file`: pole do przesyłania plików,
- `checkbox`: pole wyboru, które można zaznaczyć lub odznaczyć,
- `radio`: przycisk radiowy, który można wybrać jako jeden z wielu,
- `button`: przycisk, który można kliknąć,
- `submit`: przycisk do wysłania formularza,
- `reset`: przycisk do zresetowania formularza,
- `url`: pole do wprowadzania adresu URL,
- `search`: pole do wyszukiwania,
- `hidden`: ukryte pole, nie wyświetlane, ale jego wartość jest przesyłana,
- `image`: przycisk z grafiką.

## Video

```html
<video controls width="400">
  <source src="film.mp4" type="video/mp4" />
</video>
```

## Audio

```html
<audio controls>
  <source src="dzwiek.mp3" type="audio/mpeg" />
</audio>
```

## Lista definicji

```html
<dl>  
  <dt>Coffee</dt>  
  <dd>- black hot drink</dd>
</dl>
```

## Progress

Wyświetla wskaźnik pokazujący postęp realizacji zadania, zazwyczaj wyświetlany jako pasek postępu.

```html
<label for="progress-bar">Uploading Document</label>
<progress id="progress-bar" value="70" max="100">70%</progress>
```

## Semantyczne znaczniki HTML5
- `<header>` - nagłówek strony/sekcji,
- `<nav>` - menu nawigacyjne,
- `<main>` - główna zawartość,
- `<section>` - sekcja,
- `<article>` - artykuł,
- `<aside>` - zawartość poboczna,
- `<footer>` - stopka.

## Metatagi

```html
<meta name="description" content="Opis strony" />>
<meta name="keywords" content="html, kurs, nauka" />
<meta name="author" content="Twoje Imie" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```
