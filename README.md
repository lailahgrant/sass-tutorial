# Sass - CSS with Superpowers
> by codeSTACKr

## What is Sass?
- [x] Sass is a CSS extension language.

### What you need to write CSS (Setup)
- [x]  VS Code
  - [ ]  Live Sass Compiler
  - [ ]  Live Server
  - [ ]  Install these compilers as extensions

### There are **two** syntaxes supported by Sass

#### 1. SCSS Syntax
- The simplest and most popular.
  
```css
@mixin button-base(){
    @include typography(button);

    display: inline-flex;
    position: relative;
    height: $button-height;
    border: none;
    vertical-align: middle;

&:hover {cursor: pointer;}
}
```

#### 2. Indented Syntax
- It was the original sass syntax.
- Uses the .sass file extension.
- It uses **indentation** instead of **{}** and **;**

```css
@mixin button-base()
    @include typography(button)

    display: inline-flex
    position: relative
    height: $button-height
    border: none
    vertical-align: middle

&:hover
    cursor: pointer
```

> Create a `scss` folder and add a `style.scss` file
> Watch SCSS - this creates a `css` folder in the `dist` folder with `.style.css`
> 
> Don't write in the `.css` file.

#### CSS Variables
- CSS Variables compile into CSS variables.
- Use `--` for CSS variables
- Use `var()`
- CSS Variables have **`90%`** compatibility across browsers.

```css
/* put this in the style.scss */
:root {
    --primary-color: #272727;
    --accent-color: #ff652f;
    --text-color: #fff;
}


body {
    background: var(--primary-color);
}
```

#### Sass Variables
- Sass Variables compile into the actual values.
- Use `$` for Sass variables
- DON'T use `var()`
- Sass Variables have **`100%`** compatibility across browsers.

```scss
$primary-color: #272727;
$accent-color: #ff652f;
$text-color: #fff;

body {
    background: $primary-color;
}
```


### Maps
> In JavaScript, compare `Maps` to `Arrays`
- Maps are lists of `key-value` pairs.

```scss
$font-weights: (
    "regular" : 400,
    "medium": 500,
    "bold" : 700
);
```

- Call the maps as follows:-
```scss
font-weight: map-get($map: , $key: );
```

- This is how the `style.scss` file looks like:-

```scss
//map
$font-weights: (
    "regular" : 400,
    "medium" : 500,
    "bold" : 700
);

body{
    color: $text-color;
    //call the map
    font-weight: map-get($font-weights: , bold);
}
```

- Have shortcuts in Sass
```scss
.main {
    width: 80%;
    margin: 0 auto;

    .main-paragraph {
        font-weight: map-get($font-weights, bold);
    }
}
```

OR

- `&` = the parent (.main)
- Use Interpolation :- Wrap `&` in `#{}`


```scss
.main {
    width: 80%;
    margin: 0 auto;

// & = the parent (.main)
// Use Interpolation :- Wrap & in #{}
    #{&}-paragraph {
        font-weight: map-get($font-weights, bold);
    }
}
```

### Separating files
- In Sass, we can create `partial Sass` files that contain small snippets of CSS that can be included in other Sass files.
- Cam _modularize_ the CSS and make it easy to maintain projects.

**Partial**
- A partial is simply a Sass file named with a leading underscore (_).
- The `_` lets Sass know that the file is only a `partial` and that it shouldn't generate a CSS file.
- The compiler will ignore files that begin with `_`s.
- [x] Create a `_resets.scss` file in `scss` folder.

`_resets.scss`

```scss
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}
```

- [x] Include the `_resets.scss` in the `style.scss`

`style.scss`

```scss
@import './resets';
```

### Sass Functions
- Declare a function using `@function`

```scss

//create a function
@function weight($weight-name) {
    @return map-get($font-weights , $weight-name );
}

//call the function
.main {
    width: 80%;
    margin: 0 auto;

// & = the parent (.main)
// Use Interpolation :- Wrap & in #{}
    #{&}-paragraph {
    //call function
        font-weight: weight(bold);
    }
}

```

### Mixins
- They're like functions
- `@mixin`
- Create the mixin
- Include the mixin
- Can also pass `arguments` in `mixins`.

```scss
@mixin flexCenter{
    display: flex;
    justify-content: center;
    align-items: center;
}

.main {
    @include flexCenter;
    width: 80%;
    margin: 0 auto;
}
```

- Can also pass `arguments` in `mixins`.

```scss
@mixin flexCenter($direction) {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: $direction;
}

.main {
    @include flexCenter(column);
    width: 80%;
    margin: 0 auto;
}
```

> - Functions and Mixins are similar.
>
| Functions                                                    | Mixins                      |
| ------------------------------------------------------------ | --------------------------- |
| Functions should be used to compute values and return values | Mixins should define styles |
|                                                              |                             |

###### Use case of Mixins
- [x] Choosing between Dark and light mode.
- [x] Media queries.

`Choosing between Dark and light mode`

```scss
@mixin theme($light-theme: true) {
    @if $light-theme {
        background: lighten($primary-color, 100%);
        color: darken($text-color, 100%);
    }
}

// light theme
.light {
    @include theme($light-theme: true);
}
```

`Media queries`

```scss
@mixin mobile {
    
}
```


