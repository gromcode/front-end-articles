## HTML & CSS - quality rules

#### Global
  1. [Semantics](#semantics)
  1. [Naming](#naming)
  1. [BEM (.html)](#bem-html)
  1. [BEM (.scss)](#bem-scss)
  1. [Breakpoints](#breakpoints)
  1. [Preprocessor usage](#preprocessor-usage)
  1. [Styles order](#styles-order)

#### Code styles
  1. [HTML formating](#types)

## Semantics

  <a name="semantics--1.1"></a><a name="1.1"></a>
  - [1.1](#semantics--1.1) Always adhere to semantics in your project. Use HTML tags for their intended purpose ([more details](https://www.w3schools.com/html/html5_semantic_elements.asp)).

    Examples:

      - v.1:
  
    ```html
    <!-- Incorrect -->
    <div class="header">
      <h1>Header</h1>
    </div>
    <div class="main">
      <div class="section">
        <div>Main content</div>
        <a href="#">Link</a>
      </div>
    </div>
    <div class="footer">
      <p>Footer</p>
    </div>

    <!-- Correct -->
    <header>
      <h1>Header</h1>
    </header>
    <main>
      <section>
        <p>Main content</p>
        <a href="#">Link</a>
      </section>
    </main>
    <footer>
      <p>Footer</p>
    </footer>
    ```
      - v.2:
    
    ```html
    <!-- Incorrect -->
    <div class="header">
      <div>Title</div>
    </div>
    <div class="main">
      <div class="article">
        <div>Subtitle</div>
        <p>Main content</p>
        <ul>
          <div><a href="#">Link 1</a></div>
          <div><a href="#">Link 2</a></div>
        </ul>
      </div>
    </div>
    <div class="footer">
      <p>Footer</p>
    </div>

    <!-- Correct -->
    <header>
      <h1>Title</h1>
    </header>
    <main>
      <article>
        <h2>Subtitle</h2>
        <p>Main content</p>
        <ul>
          <li><a href="#">Link 1</a></li>
          <li><a href="#">Link 2</a></li>
        </ul>
      </article>
    </main>
    <footer>
      <p>Footer</p>
    </footer>
    ```

**[⬆ back to top](#html--css---quality-rules)**

## Naming

  <a name="bem-html--2.1"></a><a name="2.1"></a>
  - [2.1](#bem-html--2.1) Choose class names for elements carefully, the name should clearly reflect the content or functionality of the element.

  <a name="bem-html--2.2"></a><a name="2.2"></a>
  - [2.2](#bem-html--2.2) This also applies to file names.

**[⬆ back to top](#html--css---quality-rules)**



## BEM (.html)

  <a name="bem-html--3.1"></a><a name="3.1"></a>
  - [3.1](#bem-html--3.1) Carefully name classes for elements following BEM rules ([more details](https://ru.bem.info/methodology/quick-start/)).

  <a name="bem-html--3.2"></a><a name="3.2"></a>
  - [3.2](#bem-html--3.2) You cannot use a BEM modifier for an element's class name:

    ```html
    <!-- Incorrect -->
    <section class="about">
      <article class="about__article">
        <h2 class="about__article_title">What is it about?</h2>
        <p class="about__article_text">Building a website...</p>
      </article>
      <article class="about__article">
        <h2 class="about__article_title">Who is it for?</h2>
        <p class="about__article_text">Startups, small...</p>
      </article>
      ...
    </section>
    
    <!-- Сorrect -->
    <section class="about">
      <article class="about__article article">
        <h2 class="article__title">What is it about?</h2>
        <p class="article__text">Building a website...</p>
      </article>
      <article class="about__article article">
        <h2 class="article__title">Who is it for?</h2>
        <p class="article__text">Startups, small...</p>
      </article>
      ...
    </section>
    ```
    
  <a name="bem-html--3.3"></a><a name="3.3"></a>
  - [3.3](#bem-html--3.3) An element cannot include another element:

    ```html
    <!-- Incorrect -->
    <ul class="additional-nav__list">
      <li class="additional-nav__list__item"><a href="#">Acquire</li>
      <li class="additional-nav__list__item"><a href="#">Marketing</a></li>
      <li class="additional-nav__list__item"><a href="#">WebTemplates</a></li>
      <li class="additional-nav__list__item"><a href="#">CustManagement</a></li>
      <li class="additional-nav__list__item"><a href="#">Virtual Ina></li>
    </ul>

    <!-- Сorrect -->
    <ul class="additional-nav__list">
      <li class="additional-nav__list-item"><a href="#">Acquire</li>
      <li class="additional-nav__list-item"><a href="#">Marketing</a></li>
      <li class="additional-nav__list-item"><a href="#">WebTemplates</a></li>
      <li class="additional-nav__list-item"><a href="#">CustManagement</a></li>
      <li class="additional-nav__list-item"><a href="#">Virtual Ina></li>
    </ul>
    ```

  <a name="bem-html--3.4"></a><a name="3.4"></a>
  - [3.4](#bem-html--3.4) Avoid element names containing more than two words:

    ```html
    <!-- Incorrect -->
    <div class="review">
      <p class="review__message">“Great widgets...</p>
      <div class="review__worker">
        <img
          src="https://..."
          alt="User Avatar"
          class="review__worker-avatar"
        />
        <div class="feedback__worker review__about-worker">
          <b class="review__about-worker-name">Viella Malkovich</b>
          <p class="review__about-worker-profession">Creative Director Johnson</p>
        </div>
      </div>
    </div>

    <!-- Сorrect v.1 -->
    <div class="review">
      <p class="review__message">“Great widgets...</p>
      <div class="review__worker">
        <img
          src="https://..."
          alt="User Avatar"
          class="review__worker-avatar"
        />
        <div class="review__worker-details">
          <b class="review__worker-name">Viella Malkovich</b>
          <p class="review__worker-profession">Creative Director Johnson</p>
        </div>
      </div>
    </div>

    <!-- Сorrect v.2 -->
    <div class="review">
      <p class="review__message">“Great widgets...</p>
      <div class="review__worker review-worker">
        <img
          src="https://..."
          alt="User Avatar"
          class="review-worker__avatar"
        />
        <div class="review-worker__details">
          <b class="review-worker__name">Viella Malkovich</b>
          <p class="review-worker__profession">Creative Director Johnson</p>
        </div>
      </div>
    </div>
    ```

**[⬆ back to top](#html--css---quality-rules)**

## BEM (.scss)

  <a name="bem-scss--4.1"></a><a name="4.1"></a>
  - [4.1](#bem-scss--4.1) Always follow the correct nesting of BEM selectors in .scss styles:

    ```html
    <section class="price-card">
      <h1 class="price-card__title price-card__title_primary">Business</h1>
      <p class="price-card__subtitle">Website</p>
      <h2 class="price-card__price price-card__price_new">299€</h2>
      <p class="price-card__description">Advanced website made...</p>
      <div class="sale-decoration">
        <p class="sale-decoration__subtitle">Fantastic</p>
        <h6 class="sale-decoration__title">Sale</h6>
      </div>
    </section>
    ```
    ```scss
    .price-card {
      &__title {
        &_primary {...}
      }
      &__subtitle {...}
      &__price {
        &_new {...}
      }
      &__description {...}
    }

    .sale-decoration {
      &__subtitle {...}
      &__title {...}
    }
    ```
    
  <a name="bem-scss--4.2"></a><a name="4.2"></a>
  - [4.2](#bem-scss--4.2) Each new block should be placed outside its parent styles scope:

    ```scss
    // Incorrect //
    .header {
      color: $main-text-color;
      ...
      .menu {
        display: flex;
        ...
        .navigation {
          display: flex;
          ...
        }
      }
      .headline {
        width: 826px;
        ...
      }
    }
    
    // Correct //
    .header {
      color: $main-text-color;
      ...
    }
    
    .menu {
      display: flex;
      ...
    }      
   
    .navigation {
      display: flex;
      ...
    }
    
    .headline {
      width: 826px;
      ...
    }
    ```
  <a name="bem-scss--4.3"></a><a name="4.3"></a>
  - [4.3](#bem-scss--4.3) Avoid styles duplication:

    ```scss
    // Incorrect //
    .checkmark {
      &_green {
        display: block;
        margin: auto;
        margin-left: 22px;
        margin-right: 22px;
        width: 15px;
        height: 13px;
        background-image: url("https://...-symbol_green.png");
      }
      &_blue {
        display: block;
        margin: auto;
        margin-left: 22px;
        margin-right: 22px;
        width: 15px;
        height: 13px;
        background-image: url("https://...-symbol_blue.png");
      }
      &_orange {
        display: block;
        margin: auto;
        margin-left: 22px;
        margin-right: 22px;
        width: 15px;
        height: 13px;
        background-image: url("https://...-symbol_green.png");
      }
    }

    // Incorrect //
    .checkmark {
      display: block;
      margin: auto;
      margin-left: 22px;
      margin-right: 22px;
      width: 15px;
      height: 13px;
      background-image: url("https://...-symbol_green.png");

      &_blue {
        background-image: url("https://...-symbol_blue.png");
      }

      &_orange {
        background-image: url("https://...-symbol_green.png");
      }
    }
    ```
  <a name="bem-scss--4.4"></a><a name="4.4"></a>
  - [4.4](#bem-scss--4.4) Use `&` with the full element/modifier name:

    ```html
    <!-- html example -->
    <div class="review">
      <p class="review__message">“Great widgets...</p>
      <div class="review__worker">
        <img
          src="https://..."
          alt="User Avatar"
          class="review__worker-avatar"
        />
      </div>
    </div>
    ```

    ```scss
    // Incorrect //
    .review {
      ...
      &__message {...}
      &__worker {
        ...
        &-avatar {...} // ===> X
      }
    }

    // Correct //
    .review {
      ...
      &__message {...}
      &__worker {...}
      &__worker-avatar {...}
    }
    ```
  <a name="bem-scss--4.5"></a><a name="4.5"></a>
  - [4.5](#bem-scss--4.5) Don't use [BEM modifiers](https://ru.bem.info/methodology/quick-start/#%D0%BC%D0%BE%D0%B4%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%82%D0%BE%D1%80) for styling layouts for different screen sizes, use breakpoints (+ mixins) for that:

    ```scss
    // Incorrect //
    .footer {
      display: flex;
      
      &_mobile {
        flex-direction: column;
      }
    }

    // Correct //
    .footer {
      display: flex;

      @include for-large-up {
        flex-direction: column;
      }
    }
    ```
  <a name="bem-scss--4.6"></a><a name="4.6"></a>
  - [4.6](#bem-scss--4.6) Don't use too many [BEM modifiers](https://ru.bem.info/methodology/quick-start/#%D0%BC%D0%BE%D0%B4%D0%B8%D1%84%D0%B8%D0%BA%D0%B0%D1%82%D0%BE%D1%80), only use them when necessary:

    ```scss
    // In progress...
    ```

**[⬆ back to top](#html--css---quality-rules)**

## Breakpoints

  <a name="breakpoints--5.1"></a><a name="5.1"></a>
  - [5.1](#breakpoints--5.1) Use mixins for breakpoints and place them in a separate file - 'breakpoints.scss'.

  <a name="breakpoints--5.2"></a><a name="5.2"></a>
  - [5.2](#breakpoints--5.2) Don't create unnecessary breakpoints for styling, only use the 2-3 primary ones (for mobile/tablet/desktop versions):

    ```scss
    $lg: 1400px;
    $md: 400px;

    @mixin mobile {
      @media screen and (max-width: $md) {
        @content;
      }
    }

    @mixin tablet {
      @media screen and (max-width: $lg) {
        @content;
      }
    }

    @mixin desktop {
      @media screen and (min-width: $lg + 1) {
        @content;
      }
    }
    ```

  <a name="breakpoints--5.3"></a><a name="5.3"></a>
  - [5.3](#breakpoints--5.3) Don't forget to follow the ['mobile-first'](https://www.uxpin.com/studio/blog/a-hands-on-guide-to-mobile-first-design/) approach:

    ```scss
    // In progress
    ```

**[⬆ back to top](#html--css---quality-rules)**

## Preprocessor usage

  <a name="bem-html--6.1"></a><a name="6.1"></a>
  - [6.1](#bem-html--6.1) Use variables for colors, units, etc., and place these variables in a separate file - 'variables.scss'.

    ```scss
    $primary-color: #fcf0e366;
    $secondary-color: #f2f2f2;

    $primary-unit: 4px;
    $secondary-unit: 6px;

    $primary-font-size: 16px;
    $secondary-font-size: 12px;
    ```

  <a name="bem-html--6.2"></a><a name="6.2"></a>
  - [6.2](#bem-html--6.2) Properly import various .scss files into a main 'index.scss' file (following the order of the HTML structure).

**[⬆ back to top](#html--css---quality-rules)**

## Styles order

  <a name="bem-html--7.1"></a><a name="7.1"></a>
  - [7.1](#bem-html--7.1) The order of selectors should follow the order of the HTML structure:

    ```html
    <div class="price-card">
      <h1 class="price-card__title">Business</h1>
      <p class="price-card__subtitle">Website</p>
      <h2 class="price-card__price">299€</h2>
      <p class="price-card__description">Advanced website made...</p>
    </div>
    ```
    ```scss
    // Incorrect //
    .price-card {
      &__description {}
      &__price {}
      &__title {}
      &__subtitle {}
    }

    // Correct //
    .price-card {
      &__title {}
      &__subtitle {}
      &__price {}
      &__description {}
    }
    ```

  <a name="bem-html--7.2"></a><a name="7.2"></a>
  - [7.2](#bem-html--7.2) Sort properties in selectors. It significantly improves code readability

    ```scss
    .sale-decoration {
      position: absolute;  // 
      top: 25px;           // ----> position properties
      rigth: 25px;         // 
      display: flex;               //
      justify-content: center;     //  ----> flex properties
      gap: 10px;                   //
      background-color: #f252265;      //
      border: 3px solid #fff;          // ----> decorating properties
      border-radius: 10px;             //
      padding: 10px 20px;                   //
      margin: 0;                            // ----> padding/margin
    }
    ```

**[⬆ back to top](#html--css---quality-rules)**