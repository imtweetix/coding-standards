# BEM CSS Coding Standard with SCSS

## 1. SCSS

SCSS (Sassy CSS) is an extension of CSS. It adds powerful features like variables, mixins, nesting, and more, which make managing CSS easier and more efficient.

## 2. BEM with SCSS

SCSS's nesting feature works particularly well with BEM methodology. Here's how you can structure the same navigation menu example using SCSS:

```scss
.nav {
  // Styles for "nav" block

  &__item {
    // Styles for "nav__item" element

    &--active {
      // Styles for "nav__item--active" modifier
    }
  }
}
```

This SCSS code will compile to the following CSS:

```css
.nav {
  /* Styles for "nav" block */
}

.nav__item {
  /* Styles for "nav__item" element */
}

.nav__item--active {
  /* Styles for "nav__item--active" modifier */
}
```

The `&` in SCSS refers to the parent selector. So `&__item` will become `.nav__item` when compiled to CSS, and `&--active` will become `.nav__item--active`. This allows you to nest your BEM selectors and keep your SCSS neat and readable.

## 3. Use of Variables and Mixins

Variables and mixins in SCSS can make your CSS more efficient and easier to maintain. For instance, if you're using a specific color scheme in your project, you can define these colors as variables and reuse them throughout your SCSS:

```scss
$primary-color: #ffc0cb;
$secondary-color: #800080;

.nav {
  background-color: $primary-color;

  &__item {
    color: $secondary-color;

    &--active {
      color: $primary-color;
      background-color: $secondary-color;
    }
  }
}
```

Mixins are a way to define reusable styles that can be included in multiple rules. For instance, a common use case is to define a mixin for a set of styles that handle browser prefixing for flexbox:

```scss
@mixin flexbox {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
}

.nav {
  @include flexbox;

  &__item {
    // Styles for "nav__item" element
  }
}
```

## 4. Conclusion

Pairing BEM with SCSS can significantly improve the structure and readability of your CSS. BEM provides a useful naming convention that makes it clear what each class is for, and SCSS adds useful features that make your CSS easier to write and manage. Together, they can help create a more maintainable, understandable, and organized CSS codebase.
