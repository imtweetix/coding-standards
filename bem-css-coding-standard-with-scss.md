# BEM CSS Coding Standard with SCSS

## Overview of BEM

BEM stands for:

- **Block**: A logically and functionally independent page component, the equivalent of a component in React or Angular. Examples can be a header, container, menu, or footer.
- **Element**: A part of a block that has no standalone meaning and is semantically tied to its block. For example, a menu item is an element that exists within the block menu.
- **Modifier**: A flag on a block or element used to change appearance or behavior. For example, a different color scheme for a button: `button--yellow`.

The BEM structure provides a clear, strict framework that scales well in larger projects. It's easier to understand and maintain. It also provides a solution to common problems like global namespace, code reuse, and maintainability.

## 1. Naming convention

The BEM naming conventions follow this pattern:

- **Block**: `.block`
- **Element**: `.block__element`
- **Modifier**: `.block--modifier` or `.block__element--modifier`

Note the double underscores for elements and the double hyphens for modifiers. This helps visually distinguish between the different parts of your class names.

## 2. Examples

Consider this simple HTML structure for a navigation menu:

```html
<nav class="nav">
  <a href="#" class="nav__item">Home</a>
  <a href="#" class="nav__item">About</a>
  <a href="#" class="nav__item nav__item--active">Services</a>
  <a href="#" class="nav__item">Contact</a>
</nav>
```

In this example:

- `nav` is a block. It's a standalone component that encapsulates other elements.
- `nav__item` is an element. It stands for a specific part of the `nav` block. The element name (`item`) is separated from the block name (`nav`) by two underscores.
- `nav__item--active` is a modifier. It represents a different state of the `nav__item` element. The modifier name (`active`) is separated from the block or element name by two hyphens.

In terms of CSS, it would look something like this:

```css
.nav {
  /* styling for nav block */
}

.nav__item {
  /* styling for nav__item element */
}

.nav__item--active {
  /* styling for active state of nav__item */
}
```

By following this convention, it's easy to determine the nature and purpose of a component just by looking at its name. Furthermore, because class names are scoped to specific blocks, there is less potential for name clashes and you can more easily identify CSS specificity issues.

## 3. Advantages

- It helps create clear, strict relationships between HTML and CSS.
- It allows for code reuse while avoiding redundancy.
- It gives you a clear understanding of your component's structure just by looking at your code, making it easier to understand for other team members.

## 4. SCSS

SCSS (Sassy CSS) is an extension of CSS. It adds powerful features like variables, mixins, nesting, and more, which make managing CSS easier and more efficient.

## 5. BEM with SCSS

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

## 6. Use of Variables and Mixins

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

Absolutely. Here are a few more examples of using BEM methodology in combination with SCSS:

## 7. Button Block

First, let's consider a reusable "button" block with several modifications like size and state.

```scss
// Define variables
$primary-color: #30bced;
$secondary-color: #fff;
$danger-color: #f44;

.button {
  background: $primary-color;
  color: $secondary-color;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  font-size: 16px;

  // Modifier for a large button
  &--large {
    font-size: 20px;
    padding: 15px 30px;
  }

  // Modifier for a small button
  &--small {
    font-size: 12px;
    padding: 5px 10px;
  }

  // Modifier for a disabled button
  &--disabled {
    background: #ccc;
    color: #888;
  }

  // Modifier for a danger button
  &--danger {
    background: $danger-color;
  }
}
```

## 8. Header Block

Next, let's create a "header" block with elements such as "logo" and "navigation". This block also includes modifiers for elements.

```scss
$header-height: 60px;

.header {
  height: $header-height;
  background-color: #f9f9f9;

  // Element: logo
  &__logo {
    height: $header-height;
    width: $header-height;
  }

  // Element: navigation
  &__nav {
    background-color: #eee;

    // Modifier for a vertical navigation
    &--vertical {
      width: 200px;
    }

    // Modifier for a horizontal navigation
    &--horizontal {
      height: $header-height;
    }
  }

  // Element: navigation item
  &__nav-item {
    padding: 10px;

    // Modifier for an active navigation item
    &--active {
      background-color: #ddd;
    }
  }
}
```

## 9. Card Block

Finally, consider a "card" block with different parts like "image", "title", and "content".

```scss
$card-padding: 15px;

.card {
  border: 1px solid #eee;
  border-radius: 4px;
  padding: $card-padding;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);

  // Element: image
  &__image {
    width: 100%;
  }

  // Element: title
  &__title {
    font-size: 20px;
    margin-top: $card-padding;
  }

  // Element: content
  &__content {
    font-size: 16px;
    color: #333;
  }
}
```

## Conclusion

Pairing BEM with SCSS can significantly improve the structure and readability of your CSS. BEM provides a useful naming convention that makes it clear what each class is for, and SCSS adds useful features that make your CSS easier to write and manage. Together, they can help create a more maintainable, understandable, and organized CSS codebase.
