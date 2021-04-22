# NEXT.JS starter project

This is a starter template for [Learn Next.js](https://nextjs.org/learn).

## CREATE A NEXT.JS REACT APP

`npx create-next-app nextjs-blog --use-npm --example "https://github.com/vercel/next-learn-starter/tree/master/learn-starter"`

You now have a new directory called nextjs-blog. Let’s cd into it:

`npm run dev`

## ROUTING

/pages/index.js is the file root for the app. The page that will be displayed by default.

Every pages for routing needs to be stored at /pages.
The Link component enables client-side navigation. There will be no reload from the browser when the user navigate.
All navigation happen with javascript.

```
<Link href="/posts/first-post">
    <a>this page!</a>
  </Link>
```

Furthermore, in a production build of Next.js, whenever Link components appear in the browser’s viewport, Next.js automatically prefetches the code for the linked page in the background. By the time you click the link, the code for the destination page will already be loaded in the background, and the page transition will be near-instant!

Next.js automatically optimizes your application for the best performance by code splitting, client-side navigation, and prefetching (in production).

Note: If you need to link to an external page outside the Next.js app, just use an <a> tag without Link.

If you need to add attributes like, for example, className, add it to the a tag, not to the Link tag. Here’s an example.

## Assets, metadata and CSS

### Assets

All assets should go to the top-level folder **public**

1. create the /public/images folder
2. add your images inside this /public/images folder

Instead of optimizing images at build time, Next.js optimizes images on-demand, as users request them.
Images are lazy loaded by default. That means your page speed isn't penalized for images outside the viewport.
Images load as they are scrolled into viewport.

```
import Image from 'next/image'

const YourComponent = () => (
  <Image
    src="/images/profile.jpg" // Route of the image file
    height={144} // Desired size with correct aspect ratio
    width={144} // Desired size with correct aspect ratio
    alt="Your Name"
  />
)
```

### Metadata

Next provide the **Head** component which is used to dynamically update the html tag head.
For example we can add the Head component to all the route page in our app and change the title tag with the title of the page.

```
import Head from "next/page"
export default function FirstPost() {
  return (
    <>
      <Head>
        <title>First Post</title>
      </Head>
      <h1>First Post</h1>
      <h2>
        <Link href="/">
          <a>Back to home</a>
        </Link>
      </h2>
    </>
  )
}
```

### Styling

Next has built-in support for **styled-jsx**. It's a **CSS-in-JS** library.

```
<style jsx>{`
  …
`}</style>
```

Next has also built-in support for **css** and **sass**.

We can create a wrapper (<Layout />) component which will be common for all pages. The only purpose for this is to cascade the style for all its children.

```
export default function Layout({ children }) {
  return <div>{children}</div>
}
```

Next code splitting feature works on **Css modules** as well. It ensures the minimal amount of CSS is loaded for each page!

### Global styling

CSS Modules are useful for component-level styles.
But if you want some CSS to be loaded by every page, Next.js has support for that as well.

To load global CSS files, **create a file called pages/\_app.js** with the following content:

```
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}
```
