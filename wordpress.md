# WordPress

## Gutenberg
### Wtyczki

- Stackable - dodatkowe bloki dla Gutenberga (dodaje np. blok z opiniami, mapę google),
- Contact Form 7 - dodaje formularz kontaktowy,
- Forminator - formularz kontaktowy,
- Easy WP SMTP - służy do wysyłania wiadomości,
- hCaptcha for WordPress - antybot,
- CookieYes - wtyczka do ciasteczek (z opcją wybory zgody lub braku),
- Conventer for Media - kompresja zdjęć do WebP,
- Rank Math - wtyczka do SEO,
- Spectra - wtyczka do motywu Astra,
- Block Visibility - pozwala na ustawienie widoku dla mobile,
- Otter - wtyczka do animacji.

### Dodawanie formularza kontaktowego

Wtyczka Contact Form 7 → edycja formularza (<label> Numer telefonu [tel*.tel-328]</label> → edycja adresu e-mail (numer telefonu: [tel-328] - w treści wiadomości) → shortcode.

Można dodać wtyczki SMTP i hCaptcha.

### Optymalizacja

- usunąć zbędne wtyczki i motywy,
- narzędzia do sprawdzania szybkości strony: GTmetrix, Page Speed Insights,
- na szybkość ładowania strony wpływają:
    - zbyt duże obrazy,
    - zbyt duży rozmiar skryptów JS,
    - brak kompresji zasobów,
    - niezoptymalizowania czcionka,
    - brak responsywności,
    - zły hosting lub serwer,
    - nadmierna ilość żądań,
    - zły caching,
    - opóźnione ładowanie obrazów lub reklam,
- zalecana wielkość obrazów to logo 50 - 100px wysokości, obraz 600 - 800 px szerokości,
- obrazy powinny być zapisane jako WebP lub AVIF.

### Problem z XAMPP (MySQL nie działa)

Folder xampp → mysql → aktualny folder “data” zmienić na “data_old” i zrobić nowy folder “data” → skopiować do niego pliki z folderu “backup” (poza ibdata1) i z “data_odd” (bez zastępowania dobrych plików).

### SEO

- ustawienia → czytanie → odznacz “proś wyszukiwarki o nieindeksowanie tej witryny”,
- ustawienia → bezpośrednie odnośniki → wg nazwy wpisu lub własny format,
- wybór motywu promującego SEO, np. Kadence WP, Ocean WP, Hello Elementor, Astra,
- tworzenie kategorii i tagów,
- wtyczka do SEO, np. Rank Math (pozwala np. generować mapę witryny XML, tworzyć nawigację okruszkową, ustawić nofollow dla linków, zrobić integrację z Google Search Console/Analitics, monitorować błędy 404),
- wygenerowanie mapy XML,
- kompresja zdjęć - format WebP i mniej niż 100 KB,
- wtyczki do optymalizacji technicznej, np. WP Rocket (płatna), inne z nazwą “Cache”,
- linkowanie wewnętrzne, czyli dodawanie linków w artykułach do innych artykułów na stronie,
- ustawienie “nofollow” dla linków zewnętrznych.

## Elementor
### Wtyczki

- Elementor,
- ElementorKit (do np. menu),
- Jeg Elementor Kit,
- MetForm.

### Motywy

- Hello Elementor.

### Tworzenie strony
- schowanie tytułu strony	ustawienia strony (górne menu) → układ strony: płótno elementora (elementor canvas),
- ustawienie koloru tła	ustawienia strony → styl,
- zmiana koloru dla jednego słowa	zaznacz słowo → przełącz widoczność paska narzędzi → kolor tekstu,
- nakładka na obraz	nowy kontener → styl → obraz → ustawienie styli i position: absolute,
- animowanie elementów	nowy HTML (jako nowy blok),
- błąd z ikonami SVG w liście ikon	opublikuj stronę → odśwież edytor,
- dodanie menu (za darmo)	krok 1: zrobić menu tak jak się robi w Gutenbergu (niestandardowy link to np. #about),
- krok 2: dodanie menu za pomocą wtyczki np. ElementorKit,
- ukrycie elementu dla mobile	ustawienia zaawansowane → responsywne → ukryj dla mobile.
