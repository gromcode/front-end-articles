## Layout project - quality rules


#### General
  1. [Project repository](#project-repository)
  1. [Project description (README.md)](#project-description)
  1. [Prettier](#prettier)

#### HTML
  1. [HTML formating](#types)

#### CSS
  1. [-](#types)


## Project repository

  <a name="project-repository--description"></a><a name="1.1"></a>
  - [1.1](#project-repository--description) **Description**: The name of the repository where the project is located should match the project, all folders should be properly structured, and unnecessary files need to be removed from the repository.

  <a name="project-repository--example"></a><a name="1.2"></a>
  - [1.2](#project-repository--example) **Examples**:
      - Incorect/correct repo name:
  
    ```
    person/second-project123  => ---
    person/html-css-task-26  => ---

    person/Price-cards-layout => +++
    person/price-cards => +++
    ```
      - Correct structure example:
  
    ```
    styles/
      |-- index.scss
      |-- variables.scss
      |-- breakpoints.scss
      |-- ...
    .prettierrc
    .index.html
    .styles.css
    .styles.map.css
    ```
      - Unnecessary files examples:
  
    ```
    .vscode
    .DS_Store
    /dist
    ```

**[⬆ back to top](#layout-project---quality-rules)**

## Project description

  <a name="project-description--description"></a><a name="2.1"></a>
  - [1.1](#project-description--description) **Description**: The project description (README.md) must be properly formatted and include:
    - Project name, 
    - Working deploy link ([GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site))
    - Screen resolutions supported by the layout
    - List of tools used 
    - Author

  <a name="project-description--example"></a><a name="2.2"></a>
  - [1.2](#project-description--example) **Example of `README.md` structure**:
  
    ```
    # Layout Sample Project
    
    ### [Site link](https://gromcode.github.io/layout-sample-project/)
    
    Layout supports mobile (up-to-400) and desktop (up-to-1360) versions
    
    ### The tech stack is:
    
    - [HTML5](https://en.wikipedia.org/wiki/HTML5)
    - [CSS3](https://en.wikipedia.org/wiki/Cascading_Style_Sheets)
    - [Flexbox](https://en.wikipedia.org/wiki/CSS_Flexible_Box_Layout)
    - [Sass (Scss)](https://sass-lang.com/)
    - [BEM methodology](https://en.bem.info/methodology/)
    
    ### Author

    - Some Name
    ```

**[⬆ back to top](#layout-project---quality-rules)**


## Prettier

  <a name="prettier--description"></a><a name="2.1"></a>
  - [1.1](#prettier--description) **Description**: Always add the `.prettierrc.json` file to the root of the project for correct code formatting (+ don't forget about the [extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) for VS Code).

  <a name="prettier--example"></a><a name="2.2"></a>
  - [1.2](#prettier--example) **Example**:
  
    ```json
    {
      "trailingComma": "all",
      "printWidth": 100,
      "semi": true,
      "singleQuote": true,
      "bracketSpacing": true,
      "arrowParens": "avoid"
    }
    ```

**[⬆ back to top](#layout-project---quality-rules)**