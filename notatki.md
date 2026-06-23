# Notatki

## Linki
- [Typescale](https://typescale.com/)
- [TintPNG](https://tinypng.com/)
- [CSS Grid Generator](https://cssgrid-generator.netlify.app/)
- [cubic-bezier](https://cubic-bezier.com/)
- [Clippy](https://bennettfeely.com/clippy/)
- [CSS Gradient](https://cssgradient.io/)

## Rozmiar fontu
```css
:root {
  font-size: 100%;
}
```
#### Wzór na przeliczanie px na rem 
`rem = px / 16`
#### Najczęściej używane wartości (px -> rem)

| px  | rem |
| ------------- | ------------- |
| 12 | 0.75rem |
| 14 | 0.875rem |
| 16 | 1rem |
| 18 | 1.125rem |
| 20 | 1.25rem |
| 24 | 1.5rem |
| 32 | 2rem |
| 48 | 3rem |

## Przedziały dla breakpoints
- Laptop Range: 1800px - 1200px,
- Tablet Range: 1200px - 600px,
- Phone Range: < 600px.

## Stylowanie list
- `list-style-position: inside` - wyrówna listę do środka, usunie lewy padding,
- `list-style-image: url(obrazek.svg)` - doda obrazek zamiast kropki, ale ciężko go odpowiednio wyrównać do tekstu,
- `list-style: circle inside url(obrazek.svg)` - typ, pozycja, obrazek.

## Stylowanie tła
- `background-sizing: 100%` - tło pokryje całość elementu,
- `background-image: linear-gradient(90deg, #846FFA, #F23B60)` - 90 deg oznacza, że gradient będzie “szedł” od górnego lewego rogu do dolnego prawego rogu,
- `background-image: linear-gradient(to right, #846FFA, #846FFA)` - wykorzystanie gradientu dla jednego koloru,
- `background: url(obrazek.svg) left center no-repeat` - obrazek, pozycja, powtarzanie.

## Sekcja head
```html
<head>
  <meta charset="UTF-8">
  <meta name="format-detection" content="telephone=no" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Portfolio - Usigna." />
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <link rel="shortcut icon" type="image/png" href="favicon.png" />
  <title>Usigna</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="css/style.min.css" />
</head>
```

## Ukrycie focusa
CSS
```css
*:focus {
  outline: none;
}

body.user-is-tabbing *:focus {
  outline: 2px solid blue;
}
```
JavaScript
```javascript
function showFocus() {
  function handleFirstTab(e) {
    if (e.key === 'Tab') {
      document.body.classList.add('user-is-tabbing');
      window.removeEventListener('keydown', handleFirstTab);
    }
  };
  
  window.addEventListener('keydown', handleFirstTab);
}
```

## Skip link
HTML
```html
<a href="#main" class="skip-link">Przejdź do treści</a>

<main id="main"></main>
```
Sass
```scss
.skip-link {
  clip: rect(1px, 1px, 1px, 1px);
  -webkit-clip-path: inset(50%);
  clip-path: inset(50%);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  position: absolute;
  width: 1px;
  white-space: nowrap;
  text-align: center;
  text-decoration: none;
  padding: 24px 48px;
  position: absolute;
  top: 0;
  left: 1.5rem;
  z-index: 999;
  outline: none;

  &:focus,
  &:active {
    clip: auto;
    -webkit-clip-path: none;
    clip-path: none;
    height: auto;
    margin: auto;
    overflow: visible;
    width: auto;
    white-space: normal;
  }
}
```

## Scrollbar
```css
/* scrollbar */
::-webkit-scrollbar {
  width: 12px;
}

::-webkit-scrollbar-track {
  background: white;
}

::-webkit-scrollbar-thumb {
  background-color: black;
  border-radius: 5px;  
}
```

## Hamburger menu
HTML
```html
<header>
  <div class="logo">Logo</div>
  <nav class="nav">
    <button class="hamburger" aria-expanded="false" aria-label="Otwórz/zamknij menu">
      <span class="hamburger__box">
        <span class="hamburger__inner"></span>
      </span>
    </button>
    <div class="navigation">
      <ul class="menu">
        <li class="menu__item">
          <a href="" class="menu__link">Link</a>
        </li>
        <li class="menu__item">
          <a href="" class="menu__link">Link</a>
        </li>
        <li class="menu__item">
          <a href="" class="menu__link">Link</a>
        </li>
      </ul>
    </div>
  </nav>
</header>
```
Sass
```scss
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  margin: 0;
  position: relative;
  z-index: 3;
}

/* nav */
.hamburger {
  width: 32px;
  height: 32px;
  background-color: transparent;
  padding: 0;
  border: none;
  position: relative;
  z-index: 3;
  cursor: pointer;
  transition: transform .3s .1s ease-in-out, visibility 0s .4s;
  // display: block;

  @media screen and (min-width: 1000px) {
    display: none;
  }
}

.hamburger__box {
  width: 100%;
  height: 100%;
  display: inline-block;
  position: relative;
}

.hamburger__inner {
  width: 100%;
  height: 4px;
  background-color: black;
  position: absolute;
  top: calc(50% - 2px);
  right: 0;
  transition: background-color .1s .2s ease-in-out;

  &::before,
  &::after {
    content: "";
    width: 100%;
    height: 4px;
    background-color: black;
    position: absolute;
    right: 0;
    transition: transform .2s .2s ease-in-out;
    z-index: 6;
  }

  &::before {
    top: -10px;
  }

  &::after {
    top: 10px;
  }
}

.hamburger--active {
  .hamburger__inner {
    background-color: transparent;

    &::before {
      transform: translateY(10px) rotate(45deg);
    }

    &::after {
      transform: translateY(-10px) rotate(-45deg);
    }
  }
}

.navigation {
  height: auto;
  position: fixed;
  inset: 0;
  background-color: yellow;
  padding: 128px 0;
  transform: translateY(-100%);
  visibility: hidden;
  z-index: 2;
  transition: transform .3s .1s ease-in-out, visibility 0s .4s;

  @media screen and (min-width: 1000px) {
    position: static;
    background-color: transparent;
    padding: 0;
    transform: translateY(0%);
    visibility: visible;
    z-index: 0;
  }
}

.navigation--active {
  transform: translateY(0px);
  visibility: visible;
  transition: transform .3s .1s ease-in-out, visibility 0s 0s;
}

.menu {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 24px;

  @media screen and (min-width: 1000px) {
    flex-direction: row;
  }
}

.menu__link {
  text-decoration: none;
}
```
JavaScript
```javascript
function showHamburgerMenu() {
  const hamburger = document.querySelector('.hamburger');
  const nav = document.querySelector('.navigation');
  const links = document.querySelectorAll('.menu__link');

  const handleClick = () => {
    hamburger.classList.toggle('hamburger--active');
    hamburger.setAttribute('aria-expanded', hamburger.classList.contains('hamburger--active'));
    nav.classList.toggle('navigation--active');
  };

  links.forEach(link => {
    link.addEventListener('click', () => {
      hamburger.classList.remove('hamburger--active');
      nav.classList.remove('navigation--active');
    });
  });

  hamburger.addEventListener('click', handleClick);
};

showHamburgerMenu();
```
