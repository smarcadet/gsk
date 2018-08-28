Guide des styles
===============================================================================

The following document outlines a style guide & rules for CSS development.

## 1\. Whitespace

Indents will be soft with **spaces** with **2 spaces per level**. There shouldn't be any trailing space.

Tip: configure your editor to "show invisibles" or to automatically remove end-of-line whitespace.

Tip: use an [EditorConfig](http://editorconfig.org/) file (or equivalent) to help maintain the basic whitespace conventions.

## 2\. Naming conventions

Naming convention is based on [SuitCSS naming conventions](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md).

Basically, class names must follow this conventions :

*   [componentName](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md#ComponentName)
*   [componentName--modifierName](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md#ComponentName--modifierName)
*   [componentName-descendantName](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md#ComponentName-descendentName)
*   [componentName.is-stateOfComponent](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md#is-stateOfComponent)

Just a small difference between original suitCSS convention :
* The componentName must start with lowercase character.


## 3\. Format

The chosen code format must ensure that code is: easy to read; easy to clearly comment; minimizes the chance of accidentally introducing errors; and results in useful diffs and blames.

*   Use one discrete selector per line in multi-selector rulesets.
*   Include a single space before the opening brace of a ruleset.
*   Include one declaration per line in a declaration block.
*   Use one level of indentation for each declaration.
*   Include a single space after the colon of a declaration.
*   Use uppercase and shorthand hex values, e.g., `#AAA`.
*   Use double quotes. e.g., `content: ""`.
*   Quote attribute values in selectors, e.g., `input[type="checkbox"]`.
*   _Where allowed_, avoid specifying units for zero-values, e.g., `margin: 0`.
*   Include a space after each comma in comma-separated property or function values.
*   Include a semi-colon at the end of the last declaration in a declaration block.
*   Place the closing brace of a ruleset in the same column as the first character of the ruleset.
*   etc, check the scss-lint.yml for more rules

Like this :

    .selector-1,
    .selector-2,
    .selector-3[type="text"] {
        -webkit-box-sizing: border-box;
        -moz-box-sizing: border-box;
        box-sizing: border-box;
        display: block;
        font-family: helvetica, arial, sans-serif;
        color: #333;
        background: #FFF;
        background: linear-gradient(#FFF, rgba(0, 0, 0, 0.8));
    }
    .selector-a,
    .selector-b {
        padding: 10px;
    }

Check the _.scss-lint.yml_ file at the root of the project for more details.

### Declaration order

Declarations must be consistently ordered, with cluster related properties (e.g. positioning and box-model) together.

    .selector {
        /* Positioning, Display & Box Model */
        position: absolute;
        z-index: 10;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        display: inline-block;
        overflow: hidden;
        box-sizing: border-box;
        width: 100px;
        height: 100px;
        padding: 10px;
        border: 10px solid #333;
        margin: 10px;

        /* Other */
        background: #000;
        color: #FFF;
        font-family: sans-serif;
        font-size: 16px;
        text-align: right;
    }

### Exceptions and slight deviations

Large blocks of single declarations can use a slightly different, single-line format. In this case, a space should be included after the opening brace and before the closing brace.

    .selector-1 { width: 10%; }
    .selector-2 { width: 20%; }
    .selector-3 { width: 30%; }

Long, comma-separated property values - such as collections of gradients or shadows - can be arranged across multiple lines in an effort to improve readability and produce more useful diffs.

    .selector {
        background-image:
            linear-gradient(#FFF, #CCC),
            linear-gradient(#F3C, #4EC);
        box-shadow:
            1px 1px 1px #000,
            2px 2px 1px 1px #CCC inset;
    }

### Preprocessors: additional format considerations

Different CSS preprocessors have different features, functionality, and syntax. Your conventions should be extended to accommodate the particularities of any preprocessor in use. The following guidelines are in reference to Sass.

*   Limit nesting to 1 level deep. Reassess any nesting more than 2 levels deep. This prevents overly-specific CSS selectors.
*   Avoid large numbers of nested rules. Break them up when readability starts to be affected. Preference to avoid nesting that spreads over more than 20 lines.
*   Always place `@extend` statements on the first lines of a declaration block.
*   Where possible, group `@include` statements at the top of a declaration block, after any `@extend` statements.

Like this :

    .selector-1 {
        @extend .other-rule;
        @include clearfix();
        @include box-sizing(border-box);
        // other declarations
    }

* * *

Conventions based on _Principles of writing consistent, idiomatic CSS_ by Nicolas Gallagher, licensed under the [Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).

## 5\. Comments

Well commented code is extremely important. Take time to describe components, how they work, their limitations, and the way they are constructed. Don't leave others in the team guessing as to the purpose of uncommon or non-obvious code.

The use of KSS Node forces you to use a [special syntax](https://github.com/hughsk/kss-node/blob/master/demo/styleguide.md).

Tip: configure your editor to provide you with shortcuts to output this comment patterns.


    /// Top level description of the feature
     //
     // A description.
     //
     // Markup: <some markup with a specific {{modifier_class}} like class or a pseudo class >
     //
     // .class - description of the class state
     // :pseudo - description of the pseudo state
     //
     // Styleguide category.feature

To comment a hack, a tweak or a workaround, use simple comments but do it.

    // Fix for the double margin bug with iE6


