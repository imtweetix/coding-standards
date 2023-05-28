# BEM CSS Coding Standard

## 1. Overview of BEM

BEM stands for:

- **Block**: A logically and functionally independent page component, the equivalent of a component in React or Angular. Examples can be a header, container, menu, or footer.

- **Element**: A part of a block that has no standalone meaning and is semantically tied to its block. For example, a menu item is an element that exists within the block menu.

- **Modifier**: A flag on a block or element used to change appearance or behavior. For example, a different color scheme for a button: `button--yellow`.

The BEM structure provides a clear, strict framework that scales well in larger projects. It's easier to understand and maintain. It also provides a solution to common problems like global namespace, code reuse, and maintainability.

## 2. Naming convention

The BEM naming conventions follow this pattern:

- **Block**: `.block`
- **Element**: `.block__element`
- **Modifier**: `.block--modifier` or `.block__element--modifier`

Note the double underscores for elements and the double hyphens for modifiers. This helps visually distinguish between the different parts of your class names.

## 3. Examples

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

## 4. Advantages

- It helps create clear, strict relationships between HTML and CSS.
- It allows for code reuse while avoiding redundancy.
- It gives you a clear understanding of your component's structure just by looking at your code, making it easier to understand for other team members.

## 5. Conclusion

Adopting the BEM methodology can greatly improve the scalability and maintainability of your code. It encourages code reuse and makes your codebase easier to navigate, reducing the chance of unexpected side effects from CSS changes. With BEM, your CSS will be more modular and consistent, making it easier to work with for you and your team.
