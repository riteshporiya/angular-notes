# Angular

Angular is a popular framework used to create reactive single-page applications (SPAs). SPAs provide a seamless user experience by manipulating the Document Object Model (DOM) within a single HTML document.

## Angular Versions

- **AngularJS (Version 1):** The original version of Angular, which was completely rewritten as Angular 2 (Version 2).
- **Angular (Version 2+):** All versions of Angular after 2, including 4, 5, 6, 7, 8, and 9. These versions frequently introduce small improvements and maintain backward compatibility.

This guide focuses on Angular (Version 2 to 9), and knowledge of Angular 2 is generally applicable to the later versions.

## Angular CLI (Command Line Interface)

Angular CLI is the recommended way to create Angular projects. It optimizes files for deployment and simplifies project setup.

## Why Node.js is Required?

Node.js is necessary for several reasons:

1. It is used by the CLI for bundling and optimizing Angular projects.
2. It provides npm (Node Package Manager) for managing project dependencies, including the Angular framework and other libraries.

## Setting Up an Angular Project (Assuming Node.js is Installed)

1. Install Angular CLI globally:
```javascript 
npm install -g @angular/cli 
```
2. Create a new Angular project:
```js
ng new my-dream-app
```
3. Change directory to your project:
```js
cd my-dream-app
```
4. Start a development server:
```js
ng serve
```
To ensure you have the latest CLI version, use the following command:
```js
npm install -g @angular/cli@latest
```


If you're using Windows, run these commands as an administrator.

## TypeScript in Angular

Angular uses TypeScript, which is a superset of JavaScript (JS). TypeScript provides benefits such as early error detection, shorter syntax, and more features than traditional JavaScript.

- **ES5:** Traditional JavaScript supported by all browsers but may lead to runtime issues.
- **ES6/ES2015:** Enhanced JavaScript with new functionalities, often preferred by developers.
- **TypeScript:** A superset of JS that aids in debugging and offers more features. It's highly recommended for larger projects and teams.

## ECMAScript (ES) and JavaScript

ECMAScript is a scripting language standard that JavaScript follows. Netscape approached ECMA for JavaScript standardization, resulting in the name "ECMAScript" for JavaScript.

## Why "JavaScript"?

JavaScript was initially called "LiveScript," but Netscape changed it to "JavaScript" to compete with Microsoft's "Java." The name change occurred during the standardization process with ECMA. The name "JavaScript" is licensed under Oracle.

## TypeScript

TypeScript is similar to vanilla JavaScript but with additional functionality. It cannot run directly in browsers, so it's transcompiled to JavaScript using tools like the Angular CLI.

### TypeScript Features

- Classes
- Strongly Typed Interfaces
- Decorators
- Type Casting

TypeScript is an object-oriented programming language developed by Microsoft. It helps identify and rectify problems during development, making it suitable for large projects and teams.

TypeScript code is transcompiled for execution, offering benefits such as easy debugging and consistency, which are particularly useful in Angular applications.

# Adding Bootstrap to an Angular Project

## Option 1: Using npm install

To add Bootstrap to your Angular project using npm, follow these steps:

1. Install Bootstrap by running the following command:
```js
npm install bootstrap@3
```
- In your `angular.json` file, under the `build` section, add Bootstrap to the styles array:
```typescript
"styles": [
  "src/styles.css",
  "node_modules/bootstrap/dist/css/bootstrap.min.css"
]
```
## Option 2: Using CDN
- You can also use Bootstrap via CDN by adding the following line to your HTML file:

```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
```
## How Angular Runs with `ng serve`

- When you run `ng serve`, Angular serves the `index.html` file as the entry point.
- The `index.html` file contains scripts inserted by the Angular CLI during compilation.
- Angular CLI bundles JavaScript files and inserts them into `index.html`.
- `<app-root></app-root>` is a custom Angular component and not standard HTML.
- The `main.ts` file is the first to run and calls `platformBrowserDynamic().bootstrapModule(AppModule)` to bootstrap the Angular application.
- `AppModule` is defined in `app.module.ts` and specifies which component to `bootstrap` with the bootstrap property.

## Angular Components

- Components in Angular are building blocks with their own logic.
- They help organize and debug applications, reducing repetition.
- Components are created using the `@Component` decorator.
- Here's an example of creating a component manually:
```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-server",
  templateUrl: "./server.component.html",
})
export class ServerComponent {}
```
## Creating a Component Manually (3 Steps)
1. Create `server.component.ts` and `server.component.html`.
2. Include the component in the `declarations` array of the app module.
3. Mount the component in the required component's template.

## Generating a Component Automatically
You can generate a component automatically using the Angular CLI with either of the following commands:
```angularjs
ng generate component servers
```
OR

```angularjs
ng g c servers
```
This command generates the necessary files and folders for the component.

## Additional Notes
- It's recommended to name components with the "component" suffix to avoid naming conflicts.
- `.spec.ts` files are for testing purposes and can be deleted if not needed.

# Component Templates (Required in Components)

When creating Angular components, you must provide a template for defining the component's HTML structure. You have two options for specifying the template:

1. **Inline Template:**
   You can include the template directly within the component metadata using the `template` property. Here's an example:

   ```typescript
   @Component({
     selector: 'app-servers',
     template: `
       <p>Here it is</p>
       <app-server></app-server>
       <app-server></app-server>
     `,
     styleUrls: ['./servers.component.css']
   })
1. **External Template:**
   Alternatively, you can specify an external HTML file as the template using the `templateUrl` property. The template is then loaded from that file.
## Using Styles in Components
You can also include styles (CSS) in your Angular components. There are two ways to do this:

1. **Using styleUrls:**
   You can link external CSS files to your component using the `styleUrls` property in the component metadata. For example:
```typescript
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
```

   You can define styles directly within the component metadata using the `styles` property. 
   This is useful for small, component-specific styles. Here's an example:
```typescript
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styles: [
    `
    h3 {
      color: blue;
    }
    `
  ]
})
```
Note that you can't use both `styleUrls` and `styles` simultaneously in the same component.

## Selector Types
Selectors in Angular define how components are identified and used in your templates. There are three types of selectors:

1. **Element Selector:**
   The most common selector type is based on HTML element names. For example, if you use `<app-server>` in your template, you define the component with an element selector like this:
```typescript
@Component({
  selector: 'app-server',
  // ...
})
```
2. **Attribute Selector:**
   You can also use attribute-based selectors. This means you add a custom attribute to your HTML element and select components based on that attribute. For example:
```html
<div app-servers></div>
```
And in your TypeScript file:
```typescript
@Component({
  selector: '[app-servers]',
  // ...
})
```
3. **Class Selector:**
   Components can also be selected based on their class. To use class-based selectors, you add a class to your HTML element and select components based on that class. For example:
```html
<div class="app-server"></div>
```
In your TypeScript file:
```typescript
@Component({
  selector: '.app-server',
  // ...
})
```
Note: Selectors cannot be ID-based and cannot include pseudo-selectors.
