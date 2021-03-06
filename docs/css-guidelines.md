---
layout: full
title: "CSS Guidelines"
order: 4
---

# CSS Guidelines

1. [Format](#format)
 * [Declaration order](#declaration-order)
 * [Sass specific](#sass-specific)
2. [Naming Conventions](#naming-conventions)
 * [Components](#components)
 * [Utilities](#utilities)
 * [JS Hacks](#js-hacks)
3. [Commenting](#commenting) (NOT FINISHED)
  * [Sass comments](#sass-comments)
  * [CSS Comments](#css-comments)
4. [Sass specific](#sass-specific)
  * [Variables](#specific_variables)
5. Tooling (TODO)
6. [Further reading](#further-reading)

## 1. Format

The chosen code format must ensure that code is: easy to read; easy to clearly
comment; minimizes the chance of accidentally introducing errors; and results
in useful diffs and blames.

* Two (2) spaces indents, no tabs;
* Ideally, 80-characters wide lines;
* Meaningful use of whitespace.
* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Use lowercase and shorthand hex values, e.g., `#aaa`.
* _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
* Include a space after each comma in comma-separated property or function
  values.
* Include a semi-colon at the end of the last declaration in a declaration
  block.
* Separate each ruleset by a blank line.
* Single declarations can use single-lineformat.
* Long, comma-separated property values - such as collections of gradients or
shadows - can be arranged across multiple lines in an effort to improve
readability and produce more useful diffs.


```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  display: block;
  font-family: helvetica, arial, sans-serif;
  color: #333;
  background: #fff;
  background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
  padding: 10px;
}

.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }

.selector {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Declaration order

If declarations are to be consistently ordered, it should be in accordance with
a single, simple principle.


```css
.selector {
  /* Positioning */
  position: absolute;
  z-index: 10;
  top: 0;
  right: 0;

  /* Display & Box Model */
  display: inline-block;
  overflow: hidden;
  box-sizing: border-box;
  width: 100px;
  height: 100px;
  padding: 10px;
  border: 10px solid #333;
  margin: 10px;

  /* Color */
  background: #000;
  color: #fff

  /* Text */
  font-family: sans-serif;
  font-size: 16px;
  line-height: 1.4;
  text-align: right;

  /* Other */
  cursor: pointer;
}
```

## 2.Naming conventions

### Components

The CSS responsible for component-specific styling.

Syntax: `<ComponentName>[-descendentName][--modifierName]`

We use a BEM-like naming convention., meaning Block, Element, Modifier, is a front-end methodology coined by developers working at Yandex. Whilst BEM is a complete methodology, here we are only concerned with its naming convention. Further, the naming convention here only is BEM-like; the principles are exactly the same, but the actual syntax differs slightly.

BEM splits components’ classes into three groups:

* **Block**: The sole root of the component.
* **Element**: A component part of the Block.
* **Modifier**: A variant or extension of the Block.

This has several benefits when reading and writing HTML and CSS:

* It helps to distinguish between the classes for the root of the component,
  descendent elements, and modifications.
* It keeps the specificity of selectors low.
* It helps to decouple presentation semantics from document semantics.


#### ComponentName

The component's name must be written in **UpperCamelCase**.

```css
.MyComponent { /* … */ }
```

```html
<article class="MyComponent">
  …
</article>
```

#### ComponentName--modifierName

A component modifier is a class that modifies the presentation of the base
component in some form (e.g., for a certain configuration of the component).
Modifier names must be written in camelCase and be separated from the
component name by two hyphens. The class should be included in the HTML _in
addition_ to the base component class.

```css
/* Core button */
.Button { /* … */ }
/* Default button style */
.Button--default { /* … */ }
```

```html
<button class="Button Button--default" type="button">…</button>
```

#### ComponentName-descendentName

A component descendent is a class that is attached to a descendent node of a component. It's responsible for applying presentation directly to the
descendent on behalf of a particular component. Descendent names must be
written in camelCase.

```html
<article class="Tweet">
  <header class="Tweet-header">
    <img class="Tweet-avatar" src="{{src}}" alt="{{alt}}">
    …
  </header>
  <div class="Tweet-bodyText">
    …
  </div>
</article>
```

#### ComponentName.is-stateOfComponent

Use `is-stateName` or `has-stateName` to reflect changes to a component's state. Normally used for javascript interactions. The state name must be camelCase.
**Never style these classes directly; they should always be used as an adjoining class.**

This means that the same state names can be used in multiple contexts, but
every component must define its own styles for the state (as they are scoped to
the component).

```css
.Tweet { /* … */ }
.Tweet.is-expanded { /* … */ }
```

```html
<article class="Tweet is-expanded">
  …
</article>
```

```html
<input class="Input has-error">
  …
</article>
```

### Utilities

Low-level structural and positional traits. Utilities can be applied directly to any element within a component.

Syntax: `<property>-<value>-[sm|md|lg]`

#### property-value-size

Utilities must use a camelCase name. What follows is an example of how various utilities can be used to create a simple structure within a component.

```html
<div class="clearfix">
  <a class="float-left" href="{{url}}">
    <img class="display-block" src="{{src}}" alt="">
  </a>
  <p class="fromSmallSize-textAlign-center fromMediumSize-textAlign-left">
    …
  </p>
</div>
```

#### Responsive utilities

Certain utilities have responsive variants using the patterns: `from<breakpoint>-<property>-<value>`. For examle: `fromMedium-textAlign-center`.

#### Visibility utilities

Syntax: `fromSmallSize-hidden` or `upToLargeSize-hidden`.


Visibility classes let you show or hide elements based on screen size or device orientation. You can use visibility classes to control which elements users see depending on their browsing environment.


### JS Hacks

Data-* attributes are used to bind the HTML to a JS Component. For example:

```html
<div data-toggler>
</div>
```


## 3. Commenting

We need to create classes self explanatory, to not be necessary to explain the code. But at times the code is not enough.

#### Sass comments

We use Sass comments `//`, instead of CSS `/* */`. These comments will never be visible in the compiled CSS.

```css
// This is my comment
.selector {}
```

If you want to display comments in the compiled CSS, you have to use CSS comments, type C.

```css

/**
 * Images.
 */

img {
  max-width: 100%;
  height: auto;
  font-style: italic;
}
```

**When do we use comments?:**

At the beginning of a file:

```css

//
// Button Component
// this is the description, if needed
//

```

At the beginning of a section:

```scss

.Component {
  ...
}

// Variations
//
// Variation
.Component--variation {
  ...
}
```

When you have to explain some line of CSS, when needed:

```scss
.selector {
  // why z-index is used?
  z-index: 3;
}
```


#### CSS Comments

CSS comments follows the [Idiomatic CSS style guide ](https://github.com/necolas/idiomatic-css):

```css
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * TODO: This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

/* Basic comment */
```


## 4. Sass specific

* Limit nesting to 1 level deep. Reassess any nesting more than 2 levels deep.
  This prevents overly-specific CSS selectors.
* Avoid selector nesting, if you have to nest then limit it to one level deep.
* Always place `@extend` statements on the first lines of a declaration
  block.
* Where possible, group `@include` statements at the top of a declaration
  block, after any `@extend` statements.
* Only use the parent selector reference (&) for these use cases
  * Appending it to pseudo classes (`&:focus`, `&:hover`, `&:first-child`).
  * Appending it to pseudo elements (`&::after`, `&::before`).
  * Appending it to State hooks in order to chain it to the selector it’s referencing (`&.is-loading`).
  * Referencing itself when combined with any of the above to avoid duplicating CSS properties.
* Never Write Vendor Prefixes, we use [Autoprefixer](https://github.com/postcss/autoprefixer) instead.
* Variablize All Common Numbers and Colors.
* Insert Media Queries in the element/class/component.


```scss
.selector-1 {
  @extend .other-rule;
  @include clearfix();
  @include box-sizing(border-box);

  &:hover {
    color:red
  }


}
```

### Variables

Only create variables when it makes sense to do so. Do not initiate new variables for the heck of it, it won’t help. A new variable should be created only when all of the following criteria are met:

* The value is repeated at least twice
* The value is likely to be updated at least once

#### !default Flag

When building a library, a framework, a grid system or any piece of Sass that is intended to be distributed and used by external developers, all configuration variables should be defined with the `!default` flag so they can be overwritten.

```css
$baseline: 1em !default;
```

Thanks to this, a developer can define their own $baseline variable before importing your library without seeing their value redefined.

```css
// Developer’s own variable
$baseline: 2em;

// Your library declaring `$baseline`
@import 'your-library';

// $baseline == 2em;
```

### Multiple Variables Or Maps

There are advantages of using maps rather than multiple distinct variables. The main one is the ability to loop over a map, which is not possible with distinct variables.

Another pro of using a map is the ability to create a little getter function to provide a friendlier API. For instance, consider the following Sass code:


```css
$z-indexes: (
  'modal': 5000,
  'dropdown': 4000,
  'default': 1,
  'below': -1,
);

@function z($layer) {
  @return map-get($z-indexes, $layer);
}
```

## 5. Tooling (TODO)

Tools to help frontend development: linters (eslint, scsslint), .editorconf, documentation (sassdoc.doc)

## 6. Further reading

* [Suit CSS, Nicolas Gallagher](https://github.com/suitcss/suit/tree/master/doc)
* [Idiomatic CSS, Nicolas Gallagher](https://github.com/necolas/idiomatic-css)
* [CSS Guidelines, Harry Roberts](http://cssguidelin.es/)
* [CSS Guidelines, Chris Pearce](https://github.com/chris-pearce/css-guidelines)
* [Battling BEM: 10 Common Problems And How To Avoid Them] (https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them/)
