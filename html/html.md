## HTML
#### Lets get modular
We use the foundation of Atomic Design to help create user experiences (UX) that are forward thinking and ultimately designed with a user first approach. Atomic design enables us to design separate components, in this case called **Modules** (organisms) that together can be joined to create numerous pages.

### Atoms
Every inidividual HTML element is an Atom. e.g:
``<label></label>`` or ``<input type="text" ... />``

### Molecules
Molecules are simple UI clusters of Atom's. The simplest explanation is to use the below example:

````
<div class="form-group">
    <label>Form Label</label>
    
    <input type="text" placeholder="This is an input" />
    
    <button>Submit</button>
</div>
````
Again the above is a simple example. In real world situations these may be larger entities. Be careful with confusing Molecules with Organisms.

### Organisms
We refer to organisms as Modules, we like that word better, however the principles are the same. A module is a cluster of Molecules that form complex UI groups. In keeping with the above examples:

````
<section class="example-module">
    <div class="container">
        <div class="row">
            <div class="col text-center">
                <h1>Title goes here</h1>
                <p>This is a paragraph element</p>
            </div>
        </div>
        
        <div class="row">
            <form id="example-form" ...>
                <div class="form-group">
                    <label>Form Label</label>
                    <input type="text" placeholder="This is an input" />
                    <button>Submit</button>
                </div>
            </form>
        </div>
    </div>
</section>
````
As you can see we have an encompassing module which has a title, paragraph and form inside it, forming a module (organism).

### Templates
Simply put a template is a wireframe and example of the finished page <u>**without**</u> real content.

### Pages
The complete article a finished page with real data.