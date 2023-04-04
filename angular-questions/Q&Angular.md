## Q&A
General questions (with answers!)

### What's AOT ([Ahead-of-time](https://angular.io/guide/aot-compiler))? 
<details>
  <summary></summary>
An Angular application consists primarily of components and their HTML templates. Because the components and templates provided by Angular cannot be understood by the browser directly, Angular applications require a compilation process before they can run in a browser. The Angular ahead-of-time (AOT) compiler converts your Angular HTML and TypeScript code into efficient JavaScript code during the build phase before the browser downloads and executes that code.
</details>

### What's Lazy-loading? 
<details>
  <summary></summary>
  By default Angular applications load all the components that are imported into the main module (`app.module.ts`). This may mean loading modules that the user will not use at any time. Lazy loading is a design pattern to delay the loading of an object until the very moment of its use. That is, if we implement lazy loading in Angular we will load only the modules we need at the beginning of the application and the others on demand as we need them
</details>