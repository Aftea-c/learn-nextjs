This is a starter template for [Learn Next.js](https://nextjs.org/learn).

# 这是一份关于 Next.js 的总结
# Navigate

- 约定式路由
- Link 标签会进行 prefetch 
- css in link should add a tag `a` 


# Assets,Metadata,and Css

- public 目录下添加 images 可以添加静态资源(图片)
  
  use image component from `/next/image` , Images are lazy loaded by default.

  Resizing & optimizing images

  1.也就是说默认开启优化
  2.不论静态资源有多少图片都不会影响你的编译速度
  3.只有出现在可视化窗口中时,才会加载(滚动加载优化)

- Metadata
  
  1. `<title>` is part of the `<head>`
  2. Third-Party JavaScript 第三方插件
     `strategy` 属性设为 `lazyOnload` 可以懒加载
      `onLoad` 加载完后执行的回调函数

    ```
    import Script from 'next/script'

     <Head>
        <title>First Post</title>
      </Head>
      <Script
        src="https://connect.facebook.net/en_US/sdk.js"
        strategy="lazyOnload"
        onLoad={() =>
          console.log(`script loaded correctly, window.FB has been populated`)
        }
      />

    ```

- css (css in js)  Next.js built-in support
  1. styled-jsx 
  2. CSS Modules
  3. Sass  npm install sass  
     use css modules `.module.scss` or `.module.sass`

- global.css only inside pages/_app.js

- postcss.config.js or tailwind.config.js

# Pre-rendering & Data Fetching

- disable JavaScript on chrome  command + shift + p => javascript => disable javascript 
  `tell me what do you see`
- if disable Javascript on create-react-app ,you will see `You need to enable JavaScript to run this app.`

**Two forms of pre-rendering**
- Server-side rendering            generation HTML on each request 
- Static Generation rendering      generation HTML on build


  Static Generation with Data you should use `getStaticProps` on the page, for example:

  ```
        export default function Home(props) { ... }

        export async function getStaticProps() {
        // Get external data from the file system, API, DB, etc.
        const data = ...

        // The value of the `props` key will be
        //  passed to the `Home` component
            return {
                props: ...
            }
        }

  ```


  # Dynamic Routes

  `getStaticPaths` get route id
    
