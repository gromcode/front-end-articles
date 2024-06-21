## HTML & CSS - quality rules

#### Global
  1. [Semantics](#semantics)
  1. [BEM (.html)](#bem-html)
  1. [BEM (.scss)](#bem-scss)
  1. [Prettier](#prettier)

#### Code styles
  1. [HTML formating](#types)

## Semantics

  <a name="semantics--description"></a><a name="2.1"></a>
  - [1.1](#semantics--description) **Description**: Always adhere to semantics in your project. Use HTML tags for their intended purpose ([more details](https://www.w3schools.com/html/html5_semantic_elements.asp)).

  <a name="semantics--example"></a><a name="2.2"></a>
  - [1.2](#semantics--example) **Examples**:
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

## BEM (.html)

  <a name="bem-html--description"></a><a name="2.1"></a>
  - [1.1](#bem-html--description) **Description**: Carefully name classes for elements following BEM rules ([more details](https://ru.bem.info/methodology/quick-start/)):
    - **Blocks:**
      - Blocks are independent parts of the interface
      - A block's name describes its content and functionality
      - Use words that match the essence of the block (example: `menu`, `header`, `footer`)
      ```html
      <!-- Examples of block names -->
      <body>
        <header class="header">...</header>
        <main class="main">
          <aside class="aside"></aside>
        </main>
        <footer class="footer">...</footer>
      </body>
      ```
    - **Elements:**
      - Elements are parts of blocks and cannot exist separately from them
      - An element's name consists of the block name and the element name, separated by double underscores `__` (example: `menu__item`, `header__title`)
      ```html
      <!-- Examples of element names -->
      <header class="header">
        <h1 class="header__title">Welcome</h1>
        <nav class="menu">
          <a class="menu__item" href="#">Home</a>
          <a class="menu__item" href="#">About</a>
        </nav>
      </header>
      ```
    - **Modifiers:**
      - Modifiers define the appearance, state, or behavior of blocks or elements
      - A modifier's name consists of the block or element name and the modifier name, separated by a single underscore `_` (example: `menu__item_active`, `header_dark`)
      ```html
      <!-- Examples of modifier names -->
      <header class="header header_dark">
        <h1 class="header__title">Welcome</h1>
        <nav class="menu">
          <a class="menu__item_active" href="#">Home</a>
          <a class="menu__item" href="#">About</a>
        </nav>
      </header>
      ```

  <a name="bem-html--example"></a><a name="2.2"></a>
  - [1.2](#bem-html--example) **Common BEM problems (+ expamples)**:
    - You cannot use a BEM modifier for an element's class name

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
    
    - An element cannot include another element

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

    - Avoid element names containing more than two words

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

  <a name="bem-scss--description"></a><a name="2.1"></a>
  - [1.1](#bem-scss--description) **Description**: Always ensure the correct application of BEM selector hierarchy in styles.
    
  <a name="bem-scss--example"></a><a name="2.2"></a>
  - [1.2](#bem-scss--example) **Common problems (+ examples)**:
    - Each new block should be placed outside its parent styles scope.

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
    
    - Avoid style duplication

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

    - `&` is used only with the full name of the element/modifier.

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
        <div class="review__worker-details">
          <b class="review__worker-name">Viella Malkovich</b>
          <p class="review__worker-profession">Creative Director Johnson</p>
        </div>
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
        &-avatar {...}
        &-details {...}
        &-name {...}
        &-profession {...}
      }
    }

    // Correct //
    .review {
      ...
      &__message {...}
      &__worker {...}
      &__worker-avatar {...}
      &__worker-details {...}
      &__worker-name {...}
      &__worker-profession {...}
    }
    ```

**[⬆ back to top](#html--css---quality-rules)**