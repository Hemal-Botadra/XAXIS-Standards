# Methodology
The following are key points and ideas that make up our Development methodology here at Xaxis EMEA Tech Services. Our standards touch on most of these points however this document is a deeper insight into our thinking.

## Modularity

## CSS Selectors

One of the quickest ways to improve the modularity and flexibility of code is to think harder about the selectors you choose. The first step is to eliminate IDs from CSS selection. IDs do nothing that classes can't also do, but instantly limit reuse and flexibility as they cannot appear on a page more than once. They are also difficult to work with due to their high specificity. The ideal selector is a single classname like `.post`.

The next step is to avoid contextual selection, especially across unrelated objects. By styling an object based on context, we again reduce flexibility by needlessly tying an object's appearance to some unrelated class farther up the DOM tree. Now we've created a situation where those styles can only be used within that container, whereas had we simply written the object without contextual selection, we would be free to move that module anywhere in our site and it would still function as it should.

Contextual selection introduces complexity and unpredictability into the mix. If the next developer is unaware of a myriad of contextual conditions for an object, imagine the frustration as an object breaks or changes simply by moving it somewhere else in the site. By avoiding contextual selection, we keep our selector specificity low and gain predictable, robust objects.

Contextual selectors also add weight to our selectors, making them more difficult to work with.

```css
/* DO */
.util-nav { }

/* DO NOT */
.masthead .util-nav { }
```

Avoid overqualified selectors. Similar to contextual selectors, overqualification limits flexibility and needlessly increases selector weight.

```css
/* DO */
.util-nav { }

/* DO NOT */
div.util-nav { }
```

Avoid using elements in selectors. Elements are risky for a couple of reasons. First, they limit the markup elements we can apply a given class to - making semantic decisions for us in our CSS. Second, they have a high depth of applicability - meaning the likelihood that something will accidentally receive or collide with those styles goes up.

```css
/* DO */
.util-nav-item { }

/* DO NOT */
.util-nav a span { }
```

By simply avoiding IDs, elements and contextual selection, the potential for reuse and modularity increases dramatically.

One false sense of reuse is the use of stacked selectors. In most cases, stacked selectors are an indication that objects aren't properly being identified and abstracted into objects. If selectors are being stacked, a single class probably should have been used.

```css
/* DO */
.util-nav { }

/* DO NOT */
.news-nav,
.events-nav,
.legal-nav { }
```

## Object Identification

One key to writing modular, object based front end code is getting the granularity right. This usually involves thinking about the items on our pages "inside out" instead of "outside in."

Instead of thinking about creating pages, think about the little bits that combine to make that page. The bits are smaller and generally good at doing one thing - being a button, being a list with top borders on my items, being a container that has space for an image, a heading and some copy, being a grid to lay out major components of a site. With each object doing an excellent job, being free of contextual specificity and elemental restraints - it can be placed into the site at will, in a predictable, flexible fashion.
