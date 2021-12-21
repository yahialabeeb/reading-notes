# Assets, Metadata, and CSS

## Download Starter Code (Optional)
```bash
npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn/tree/master/basics/assets-metadata-css-starter"
```

## Assets
Next.js can serve static assets, like images, under the top-level public directory. Files inside public can be referenced from the root of the application similar to pages.

## Metadata
<title> is part of the <head> HTML tag, so let's dive into how we can modify the <head> tag in a Next.js page.

### following lines:
```html
<Head>
  <title>Create Next App</title>
  <link rel="icon" href="/favicon.ico" />
</Head>
Notice that <Head> is used instead of the lowercase <head>. <Head> is a React Component that is built into Next.js. It allows you to modify the <head> of a page.
```
* You can import the Head component from the next/head module.


## Third-party JavaScript
it is refers to any scripts that are added from a third-party source.

Adding Third-Party JavaScript

following lines:
``` html
<Head>
  <title>First Post</title>
  <script src="https://connect.facebook.net/en_US/sdk.js" />
</Head>
```

### Using the Script Component
```js
import Script from 'next/script'
```

## Writing and Importing CSS
Next.js has built-in support for CSS and Sass which allows you to import .css and .scss files.

Using popular CSS libraries like Tailwind CSS is also supported.


## Layout Component
First, create a Layout component which will be shared across all pages.

Then, open the wanted page, add an import for the Layout component, and make it the outermost component:

## Adding CSS
```css
.container {
  max-width: 36rem;
  padding: 0 1rem;
  margin: 3rem auto 6rem;
}
```
*Important: To use CSS Modules, the CSS file name must end with .module.css.

To use this container class inside components/layout.js, you need to:

Import the CSS file and assign a name to it, like styles
Use styles.container as the className



## Layout
* Automatically Generates Unique Class Names

* Devtools
This is what CSS Modules does: It automatically generates unique class names. As long as you use CSS Modules, you don’t have to worry about class name collisions.

Furthermore, Next.js’s code splitting feature works on CSS Modules as well. It ensures the minimal amount of CSS is loaded for each page. This results in smaller bundle sizes.

CSS Modules are extracted from the JavaScript bundles at build time and generate .css files that are loaded automatically by Next.js.

## Adding Global CSS
In Next.js, you can add global CSS files by importing them from pages/_app.js. You cannot import global CSS anywhere else.

# React context
## What is React context?
React context allows us to pass down and use (consume) data in whatever component we need in our React app without using props.


## When should you use React context?
when you are passing data that can be used in any component in your application.

### These types of data include:

* Theme data (like dark or light mode)
* User data (the currently authenticated user)
* Location-specific data (like user language or locale)



* You can think of React context as the equivalent of global variables for our React components.

What problems does React context solve?
* React context helps us avoid the problem of props drilling.

* Props drilling is a term to describe when you pass props down multiple levels to a nested component, through components that don't need it.

How do I use React context?

* There are four steps to using React context:

1. Create context using the createContext method. 
2. Take your created context and wrap the context provider around your component tree.
3. Put any value you like on your context provider using the value prop.
4. Read that value within any component by using the context consumer.

## What is the useContext hook?
Another way of consuming context became available in React 16.8 with the arrival of React hooks. We can now consume context with the useContext hook.