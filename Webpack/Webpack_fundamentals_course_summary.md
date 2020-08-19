Course: <https://frontendmasters.com/courses/webpack-fundamentals>

**Tóm tắt:**

**I.** Why webpack

\+ Nêu vấn đề chèn script vào browser theo cách truyền thống thì hạn chế
như thế nào? Chỉ ra giải pháp là sử dụng IIFE, giúp "safety" combines
file, hạn chế vấn đề về scope. Nhược điểm: slow, dư thừa code, không hỗ
trợ lazy load

\+ Nêu ra các vấn đề CommonJS in node: không hỗ trợ browser, chậm, không
hỗ trợ lazy load

\+ Nêu các vấn đề về ESM trên browser: không hỗ trợ node, chậm, không hỗ
trợ lazyload

\+ Giới thiệu về webpack: hỗ trợ code splitting, lazy load, hỗ trợ nhiều
module format (commonJS, ESM), loại bỏ code dư thưa.

II\. Webpack from scratch

\+ Cách cấu hình package.json environment dev, prod, debug với webpack

\+ Giới thiệu các cách sử dụng module

\+ Giải thích cách webpack bundle hoạt động

III\. Webpack Core Concepts

\+ Giải thích các khái niệm như entry point, output, loaders, plugins

\+ Cách cấu hình file webpack config theo environment tương ứng

IV\. Using Plugins

\+ Tiến hành cài đặt các plugin quan trọng

\+ Cấu hình preset, các cấu hình webpack mở rộng, không ảnh hưởng đến
cấu hình environment

Contents 
========

I. [Why Webpack](#why-webpack)

1. [Problems with Script Loading](#problems-with-script-loading)

2. [History of modules](#history-of-modules)

3. [EcmaScript Modules (ESM)](#ecmascript-modules-esm)

4. [Introducing Webpack](#introducing-webpack)

5. [Configuring Webpack](#configuring-webpack)

II. [Webpack from scratch](#webpack-from-scratch)

1. [Adding npm Scripts for Environment Builds](#adding-npm-scripts-for-environment-builds)

2. [Setting Up Debugging](#setting-up-debugging)

3. [Coding Your First Module](#coding-your-first-module)

4. [CommonJS Export](#commonjs-export)

5. [CommonJS Named Exports](#commonjs-named-exports)

6. [Tree Shaking](#tree-shaking)

7. [Webpack Bundle Walkthrough](#webpack-bundle-walkthrough)

III. [Webpack Core Concepts](#webpack-core-concepts)

1. [Webpack Entry](#webpack-entry)

2. [Output & Loaders](#output-&-loaders)

3. [Chaining Loaders](#chaining-loaders)

4. [Webpack Plugins](#webpack-plugins)

5. [Passing Variable to Webpack Config](#passing-variable-to-webpack-config)

6. [Adding Webpack Plugins](#adding-webpack-plugins)

7. [Setting Up a Local Development Server](#setting-up-a-local-development-server)

8. [Splitting Environment Config Files](#splitting-environment-config-files)

9. [Webpack Q&A](#webpack-q&a)

IV. [Using Plugins](#using-plugins)

1. [Using CSS with Webpack](#using-css-with-webpack)

2. [Hot Module Replacement with CSS](#hot-module-replacement-with-css)

3. [File Loader & URL Loader](#file-loader-&-url-loader)

4. [Loading Images with JavaScript](#loading-images-with-javascript)

5. [Limit Filesize Option in URL Loader](#limit-filesize-option-in-url-loader)

6. [Implementing Presets](#implementing-presets)

7. [Bundle Analyzer Preset](#bundle-analyzer-preset)

8. [Compression Plugin](#compression-plugin)

9. [Source Maps](#source-maps)

V. [Wrapping Up](#wrapping-up)

## Why Webpack

### Problems with Script Loading

Why webpack? What is solving?

Only 2 ways to use JavaScript in the browser.

The first way is adding a script tag for passing a source attribute and
a reference to that JS file

![](media/fundamentals/image1.png?raw=true)

The second way is write your job description to html

![](media/fundamentals/image2.png?raw=true)

-   Problems:

> \+ Doen't scale: to many script load from script tags in HTML
>
> ![](media/fundamentals/image3.png?raw=true)
>
> \+ Unmaintainable scripts: everything is global in its scope.There's a
> lot of issues with just scope and variable conflicts.

-   Solutions?

> \+ IIFE:
>
> ![](media/fundamentals/image4.png?raw=true)

-   Treat each file as IIFE (revealing module). Concatenate =\> we can
    "safely" combine files without concern of scope collision

> However, there's still problems with this. Anytime you want to change
> one file, you have to rebuild the whole thing. If you're just
> concatenating files together, how do you remove code that you've
> actually not using? Like, you need to adding the entire library for 1
> function in Lodash.
>
> IIFE is kinda slow. it forces JavaScript engines to eager parse the
> code, and so you incur much more intensive or costly parsing time when
> your JavaScript\'s loading, so it leads to slower loading apps.
>
> And how do you lazy load with a task runner? You don\'t, well there is
> no way, whatever you\'re building.

### History of modules

Node is JavaScript that runs on the server, how do you load JS if
there's no DOM?

How do you add a script tag if there is no HTML in node.

-\> CommonJS have a syntax called required, which allows you to inject
other pieces of a module into the current module

![](media/fundamentals/image5.png?raw=true)

Problems:

\+ There is no browser support for CommonJS

\+ No live bindings (problems with circular references)

(It means that when the exporting module changes a value, the change
will be visible from the importer side. This is not the case for
CommonJS modules. Module exports are copied in CommonJS. Hence importing
modules cannot see changes happened on the exporter side.)

\+ the resolution algorithm for CommonJS is kinda slow, it\'s really
slow (it\'s synchronous)

\+ No static async/lazy loading (all bundles up front). Require is kind
of dynamic, but there's no way to asynchronously load st.

### EcmaScript Modules (ESM)

![](media/fundamentals/image6.png?raw=true)

-   Reusable, encapsulated, organized, convenient

Problems?

ESM for node it not support yet

How do thay work in the browser?

ESM for bowser is very very slow. When you're using that syntax, the
browser has to basically read top down. It needs to start at import
statement.

### Introducing Webpack

Webpack is a module bundler. Let you write any module format, complies
them for the browser.

Webpack support code splitting or static async bundling, where you can
create separately lazy lot of bundles at build time.

Today, it is the most performance way, if you want to write the most
performant application. It allows us to be incredibly flexible or do any
sort of custom workflow and makes it possible.

### Configuring Webpack

![](media/fundamentals/image7.png?raw=true)

## Webpack from scratch

### Adding npm Scripts for Environment Builds

![](media/fundamentals/image8.png?raw=true)

### Setting Up Debugging

![](media/fundamentals/image9.png?raw=true)

<chrome://inspect/#devices>

![](media/fundamentals/image10.png?raw=true)

### Coding Your First Module

![](media/fundamentals/image11.png?raw=true)

### CommonJS Export

You cannot use CommonJS and ES syntax in the same file.

![](media/fundamentals/image13.png?raw=true)

You should not to use CommonJS as much as possible. There are tools like
Babel and Typescript that safety default to converting your ESM to
CommonJS behind the scenes and then passing it to Webpack.

But webpack supports ESM out of the box and that's makes it possible to
tree shake, to code eliminate and all the optimizations.

### CommonJS Named Exports

![](media/fundamentals/image15.png?raw=true)

### Tree Shaking

Let's bundle this code in production.

![](media/fundamentals/image17.png?raw=true)

-   ![](media/fundamentals/image19.png?raw=true)

This is what is called dead code elimination or tree shaking. It's the
fact that Webpack is using statically the syntax to identify what am I
using?

Becarefull

![](media/fundamentals/image20.png?raw=true)

### Webpack Bundle Walkthrough

![](media/fundamentals/image22.png?raw=true)

Let's bundle code in production.

![](media/fundamentals/image23.png?raw=true)

-   It's an IIFE. Take an arguments is modules -\> array of IIFE

I usually call it the runtime code

![](media/fundamentals/image24.png?raw=true)

It takes an ID, and it actually calls the module and then returns any
exports if it's available![](media/fundamentals/image26.png?raw=true)

ESM support live binding, it's a feature support cyclical dependencies.
This is the code required to be able to implement it. Basically it
freezing the object so that it can't be reassigned or changed

![](media/fundamentals/image27.png?raw=true)

The last line that gets executed, what happening here?

What's the ID getting passed through? -\> The first module

We're executing our entry point.

![](media/fundamentals/image28.png?raw=true)

So, webpack_require is just replacing these import statements, the
require statements to st that actually work in the browser. Execute and
behaves the same in the right order

## Webpack Core Concepts

### Webpack Entry

![](media/fundamentals/image30.png?raw=true)

The top file is your entry point. Tell webpack what (files) to load for
the browser. Compliments the Output property.

![](media/fundamentals/image31.png?raw=true)

### Output & Loaders

![](media/fundamentals/image32.png?raw=true)

Output tell Webpack where and how to distribute bundles (compilations).
Works with Entry

\***Loaders**

![](media/fundamentals/image33.png?raw=true)

As webpack's creating this dependency graph, it's adding files to it. If
webpack comes across something that matches one of these regular
expressions here, this rule apply this node module, which is just a
function behind the scenes and tranform whatever file that comes across.

Example: this entry file might be importing a .ts file. Webpack's not
gonna understand typescript out of the box -\> it would throw out errors
trying to parse that file. Ts-loader tranform .ts file to .js

![](media/fundamentals/image34.png?raw=true)

### Chaining Loaders

![](media/fundamentals/image36.png?raw=true)

Style(css(less())): style.less -\> style.css -\> \*.js -\>
inlineStyleBrowser.js

### Webpack Plugins

Plugins: adds additional funcitonality to Compilations(optimized bundled
modules). More powerful more access to CompilerAPI. Does everything else
you'd ever want to in webpack.

\+ Objects (with an 'apply' property): it's a js object has an apply
property in the prototype chain

\+ Allow you to hook into the entire compilation lifecycle

\+ Webpack has a variety of built in plugins

![](media/fundamentals/image37.png?raw=true)

Webpack itself is a completely event driven architecture. It allow us to
pivot really quickly. We could instantly adopt a new feature without
breaking anything. Or we can drop a feature really easily and we could
slowly deal with just a deprecation and barely have to manage it without
breaking changes.

### Passing Variable to Webpack Config

![](media/fundamentals/image39.png?raw=true)

### Adding Webpack Plugins

![](media/fundamentals/image41.png?raw=true)

![](media/fundamentals/image42.png?raw=true)

Html-webpack-plugin is an essential, specifically for single page
applications. It inject whatever output assets are there into this file
for you

### Setting Up a Local Development Server

![](media/fundamentals/image43.png?raw=true)

I wanna talk about webpack-dev-server. It takes the whole contents of
your disk and server it up.

It's going to reset and refresh the browser any time that we make
changes. So this is one of these awesome opportunities using the
dependency graph

It is a web server based on Express. And all it's doing is webpack,
instead of creating a bundle to your dist folder. It actually generates
a bundle in memory and it serves that information up to Express which
then does a web socket connection and says, hey, I just updated. Then it
reload.

### Splitting Environment Config Files

Libary webpack-merge, it's essentially just object assign for
webpack-config

![](media/fundamentals/image44.png?raw=true)

### Webpack Q&A

So you can use webpack-dev-server for server side for development?

-   You can use it, but you actually use a pieace that abstracts it
    called webpack-dev-middleware. So webpack-dev-server is just made up
    of webpack-dev-middleware and express. So you can use this package
    itself standalone. You can npm install webpack-dev-middleware and
    add it to your express application.

Are there situations where webpack, the process runs into an out of
memory error and where would you capture that exception?

-   When you think about in just programmatic complexity, webpack has to
    create an entire graph of all of your source files. And store it in
    memory before it creates a bundle. webpack space complexity, will be
    linear in terms of how many modules you have in your app. So you
    will end up consuming more and more memory because it needs more
    memory. So if it\'s for a production build and it\'s just a build
    and not dev server, I would say increasing the memory limit for
    Node. But we have some caching for webpack 5. We have a whole
    caching store that\'s aiming to solve this. So that would be one way
    to cache it.

## Using Plugins

### Using CSS with Webpack

![](media/fundamentals/image46.png?raw=true)

![](media/fundamentals/image48.png?raw=true)

This is what style-loader actually does. It's adds the script tag in the
browser.

### Hot Module Replacement with CSS

Loaders are really useful for helping support a unique webpack feature
called hot module replacement.

![](media/fundamentals/image49.png?raw=true)

If we change something. Instantly, you're seeing changes and we're not
reloading the browser.

So the CSS that we have now, it's just adding a module and it's blocking
the main thread. Because you're relying on JS to attach a style tag.

-   We would wanna extract it out and have it in a seperate tag. We can
    do it with **mini-css-extract-plugin**

![](media/fundamentals/image50.png?raw=true)

![](media/fundamentals/image51.png?raw=true)

### File Loader & URL Loader

![](media/fundamentals/image53.png?raw=true)

Why do we only pass node module references for these loaders?

-   Loaders are serialized, the first premise with webpack is that when
    loaders were originally invented, the way that you were using them
    actually was doing something like this.

With css-loader: import {style} from 'css-loader!./button.css'

What happens is that we stringtify and we serialize this entire request,
but sometimes you can add options and even functions as options, those
aren't serializable. We couldn't just pass a function itself in the
config or the function object cuz we need to be able to serialize that
information and then we parallelize it.

![](media/fundamentals/image54.png?raw=true)

### Loading Images with JavaScript

![](media/fundamentals/image55.png?raw=true)
![](media/fundamentals/image56.png?raw=true)

It will increase bundle file size, not good for performance. In
production:

![](media/fundamentals/image57.png?raw=true)

### Limit Filesize Option in URL Loader

![](media/fundamentals/image54.png?raw=true)
![](media/fundamentals/image58.png?raw=true)

![](media/fundamentals/image59.png?raw=true)

This option specifying the maximum size of a file in bytes. If the file
size is **equal** or **greater** than the
limit [**file-loader**](https://webpack.js.org/loaders/file-loader/) will
be used (by default) and all query parameters are passed to it.

### Implementing Presets

The idea of presets is that, there are gonna be more than just dev and
prod. You've gonna have some different scenarios like, I wanna try this
feature or I wanna analyze my build just this one time. But you don't
want it like shipped right in your prod config because it's not relevant
every time you run it. (can call it add-ons)

![](media/fundamentals/image60.png?raw=true)

In package.json add:

\"prod:typescript\": \"npm run prod \-- \--env.presets typescript\",

![](media/fundamentals/image61.png?raw=true)

### Bundle Analyzer Preset

Webpack-bundle-analyzer analyzing why did this certain dependency get
pulled into my application? Why is this file so large?

![](media/fundamentals/image62.png?raw=true)

    \"prod:analyze\": \"npm run prod \-- \--env.presets analyze\",

-   ![](media/fundamentals/image63.png?raw=true)

This is incredibly valued for identifying like, why do I have
duplication across these bundles? Or why is this file not getting
separated out? Or why is this not being tree shaken.

We'll use this preset for identifying performance issues.

### Compression Plugin

Compression-webpack-plugin take any of your assets that you wanna
include, and it compresses them.

\"compress\": \"npm run prod \-- \--env.presets compress\",

-   Npm run compress \-- \--env.presets analyze

![](media/fundamentals/image64.png?raw=true)

If you wanted to take performance seriously. I've seen this method and I
wanna create a service around this. Allows you to have an AV testing
enviroment for different types of methododology, different ways of
bundling your application and switching on these different presets in
combination.

Webpack-bundle-analyzer:

if you set the analyzer mode property to static, what this does is it
generates all the static assets to visualize. And then they actually
serve it up on a separate port for every production build that they do.
So, at any time they notice we\'ve regressed in performance.

For any build they can just go to like colon, whatever port forward
slash analyze, and it\'s there for that build. And so, they just
redeploy it every time as a part of their build.

### Source Maps

<https://webpack.js.org/configuration/devtool/>

![](media/fundamentals/image65.png?raw=true)

You can see your entire project structure if you want.

![](media/fundamentals/image66.png?raw=true)

You can use another devtool for better speeded builds

![](media/fundamentals/image67.png?raw=true)

## Wrapping Up

Is there a lazy load plugin you\'d recommend?

-   So lazy loading is code splitting in Webpack.

For example: I would only want to load the footer when somebody clicks
on that button.

![](media/fundamentals/image68.png?raw=true)

This syntax only work with typescript or babel.

You don't need any plugin for it.

How do you go about finding good plugins versus bad plugins?

![](media/fundamentals/image69.png?raw=true)

I would say the best way is just to look and see, kind of like, how
maintained is it? What version of Webpack is in their tests?

So really the best way is kinda just like the same way you would
approach anything else, how much is it contributed? How active are its
commits? And it may just be, it\'s a finished module.
