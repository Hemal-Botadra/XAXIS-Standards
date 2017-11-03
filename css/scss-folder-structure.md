## SASS Structure

The three main folders in our SASS directory are: core, modifiers, and modules.

The **CORE** folder contains:

* Global - styles for base element like `<body>` or `<a>`.
* Fonts - `@font-face` rules for embedding fonts for global use.
* Typography - General styles for all text elements ``h1...h6``, ``p``, ``li`` etc.
* Overrides - common fixes for bootstrap styles or other things.

The modifiers folder contains:

* Utilities - styles for common patterns like `.hidden`, `.visible`, `.has-error` and general helper classes for styling. e.g ``.text-bold`` or ```.mt-10``` 
* Variables - all global variables used throughout the site. e.g Fonts, Colors etc.

The modules folders contain:

* A file within named after the object that contains relevant styles for the object
* **If you need to add more folder levels then please do so**

```diff
└── assets
    └── scss
        ├── core
        |   ├── _global.scss
        |   ├── _fonts.scss
        |   ├── _typography.scss
        |   └── _overrides.scss
        ├── helpers
        |   ├── _utils.scss
        |   └── _vars.scss
        ├── shared
        |   ├── _header.scss
        |   ├── _main.scss
        |   ├── _footer.scss
        |   └── _nav.scss
        ├── modules
        |   ├── _block?.scss
        |   └── blocks?
        |       └── _block?.scss
        ├── ie8.scss
        └── styles.scss
```

When building a comprehensive CMS with different sub sections that do not follow the standard styling. The folder structure should be presented like so:

```diff
└── assets
    └── scss
        ├── core
        |   ├── _global.scss
        |   ├── _fonts.scss
        |   ├── _typography.scss
        |   └── _overrides.scss
        ├── helpers    
        |   ├── _utils.scss
        |   └── _vars.scss
        ├── admin
        |   ├── shared
        |   |   ├── _header.scss
        |   |   ├── _main.scss
        |   |   ├── _footer.scss
        |   |   └── _nav.scss
        |   └── modules
        |       ├── _block?.scss
        |       └── blocks?
        |           └── _block?.scss
        ├── auth
        |   ├── shared
        |   |   ├── _header.scss
        |   |   ├── _main.scss
        |   |   ├── _footer.scss
        |   |   └── _nav.scss
        |   └── modules
        |       ├── _block?.scss
        |       └── blocks?
        |           └── _block?.scss
        ├── admin.scss
        ├── auth.scss
        └── styles.scss
```

## Partials

Sass files that are not intended to be compiled independently, should be named with a leading underscore.

```diff
_media.scss
```

## Silent Comments

Silent comments should be used when the comment is irrelevant to the output.

```scss
//----------------------------------------------------------------------
// Micro Clearfix Mixin
//----------------------------------------------------------------------
@mixin clearfix() {
    &:before,
    &:after {
        content: " ";
        display: table;
    }

    &:after {
        clear: both;
    }
}
```

## Variables

**Global Variables**

Variables defined outside of ruleset are considered to be global and are used for setting values used across multiple modules, such as brand colors.

Define all global variables in the global `helpers/_vars.scss` partial.

Write global variables using camelCase.

```scss
$white: #fff;
$darkGray: #333;

.nav a {
    color: $darkGray;
}
```

**Module Variables**

Module variables are defined outside a ruleset and are intended for use only with a single module.

If the variable is used only in a single file, define it at the top of the file above all rulesets.

If the variable is used by more than one file in the module, define it in a module level `_module_helpers.scss` partial.

To prevent variable collisions, module variables should be prefixed with the base object name separated by a single dash.

```scss
$example-spacingUnit: 10px;

.example-mt {
    margin-top: $example-spacingUnit;
}

.example-mb {
    margin-bottom: $example-spacingUnit;
}
```

**Private Variables**

Private variables are defined inside a single ruleset and are intended for use only within that ruleset.

Write private variables using camelCase letters preceded by a single underscore.

```scss
.example-object {
    $_size: 500px;
    $_offset: -($_size / 2); // Pull the object half its size to center it.
    position: absolute;
    top: 50%;
    left: 50%;
    height: $_size;
    width: $_size;
    margin-top: $_offset;
    margin-left: $_offset;
}
```

## Operators

Operators should always be surrounded by a single space.

Use of operators should always be accompanied by a comment.

```scss
.example-object {
    $_size: 100px;
    $_pull: -($_size / 2); /* Pull the object half its size to center it. */
    position: absolute;
    top: 50%;
    left: 50%;
    height: $_size;
    margin-top: $_pull;
    margin-left: $_pull;
}
```

## Nesting

Ensure you are only nesting module components. Do not nest utilities or modifiers to ensure they are not bound to a container. 

```scss
/* DO */

.text-black {
    color:black;
}

/* DO NOT */
.element {
    .text-black {
        color:black;
    }
}
```

## Mixins

Use mixins to define styles that can be reused throughout the site to avoid repeating common code blocks. Mixins can be used at both the global and module level. Mixins used by a single module should be prefixed with the module name, and defined in the appropriate location.

Mixin definitions should always include the parenthesis.

## @extend

Do not use `@extend`.

```scss
/* DO */
.message {
    padding: 10px;
    border: 1px solid #cccccc;
}

.message-success { color: #00ff00; }
.message-error { color: #ff0000; }

/* DO NOT*/
.message {
    padding: 10px;
    border: 1px solid #ccc;
}

.message-success {
    @extend .message;
    color: #0f0;
}

.message-error {
    @extend .message;
    color: #f00;
}
```

## @control directives

`@if`, `@each`, `@while`, `@for`

Flow control directives should never use the single line syntax.

Curly braces should be formatted identically to selectors.

```scss
.example-object {
    @if 1 + 1 == 2 {
        border: 1px solid;
    }
}
```

## Other @directives

**@import**

Do not include the file extension when using `@import`.

```scss
@import "_media";
```

**@media**

It is acceptable to use `@media` rules nested in selectors if they are used for small tweaks. Separate stylesheets (`screen`, `screen_small`, `screen_large`, etc) should be used for major breakpoints.

```scss
.example-object {
    padding: 10px;
    
    @media (max-width: 500px) {
        padding: 20px;
    }
}
```

**@function**

Function naming should follow the same naming conventions as mixins.

**@warn**

It is acceptable to use `@warn` in-lieu of TODO comments.

**@debug**

It is acceptable to use `@debug` provided it is not committed to the version control repository.