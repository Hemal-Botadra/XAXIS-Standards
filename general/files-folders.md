# Files &amp; Folders

## Folder Structure

Our standard folder structure is as follows:

```diff
└── assets
    ├── media
    |   └── img
    ├── scss
    └── js
```
When compiled via gulp for distribution.

```diff

└── dist
    ├── media
    |   ├── img
    |   ├── fonts
    |   └── videos
    ├── css
    └── js
```

Additionally, an example of a typical sass directory structure can be found in [the sass section](/css/scss-folder-structure.md).

## File Names

Use lowercase for all file names (including images) with hyphens as delimiters between words.

The only exception to this rule is SCSS partials which should be prefixed with an underscore.

**Good Examples**

* styles.css
* admin-header.html
* josh-with-a-horses-head.jpg
* _vars.scss

## Storage of Dev Assets

Do not store development assets such as wireframes, PSDs, sprite source files, etc. in the actual project respository.