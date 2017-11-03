# Javascript Formatting &amp; Framework

#### First things first
We use Angular 4. Therefore strongly use typescript and ES6 syntax.

This does not mean we stray to far from Javascript conventions especially when naming functions etc.

We need to ensure that we are concise and to the point when naming our functions. A simple function that would get posts would be written as so:

```typescript
...
export class PostsComponent imlplements OnInit {
    
    constructor() {}
    
    ngOnInit() {
        this.getPost();
    }
    
    getPosts() {
       this.postService.getPosts()
        .subscribe(
            ...  
        );
    }
}
```

Note that we are using camelCase for function names and also pre-pending the type of request before what they do. The only time we vary this is when doing a POST request or PUT request.

```typescript
...
// Post
createPost() {}

// PUT
updatePost() {}
``` 

For more information on our Framework and Typescript please use the resources below.

**Resources**

* <https://www.typescriptlang.org/>
* <https://angular.io/>