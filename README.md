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


