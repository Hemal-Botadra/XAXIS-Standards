## CSS

### WE DO NOT WRITE VANILLA CSS!!!
You must use a build processor like **Gulp**, DO NOT WRITE standard CSS. Why would you when you can write SASS and nest things?

###Browse Support
We only support modern browsers, simply because the tech stack we use needs modern browsers.

### Responsive Framework

We use Bootstrap 4 (currently in beta). It utilises Flexbox, and as a result does not support any IE version < IE10. YAY (**Front-end devs rejoice**).

For bootstrap support please check out their website. [Boostrap 4](http://getbootstrap.com/)

### Naming Conventions
We use a blend of BEM (Block, Element, Modifier) and SMACSS. 

We do not use ID's to style the page except in 3 places. ``#header``, ``#main``, ``#footer``. These are the prime sections of any web page.

````
--- HEADER
------ Stays the same, exluding admin dashboards

--- MAIN
------ All main page content // Changes from page to page

--- FOOTER
------ Stays the same, exluding admin dashboards
````

We style with classes only and we write in a way to ensure modules/blocks are consistent across the board.

For example the post module/block would look like so:

````
.post {

    .post-header {
    }
    
    .post-body {
    }
    
    .post-footer {
    }
}
````

You will also notice that the above is nested, as we only use SCSS to write styles. Please check out the [build tools](general/build-tools.md) page for more information