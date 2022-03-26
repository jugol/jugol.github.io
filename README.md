## Neumorphic components

All components are perfectly in compliance with the neumorphism design trend making use of the specific shadow and coloring attributes. Neumorphism UI also comes with the shadow inset style add-on.

Check out [all components here](https://demo.themesberg.com/neumorphism-ui/html/components/all.html).

## Example pages

Neumorphism UI comes with 13 example pages including an about, pricing, contact, log in and register pages. You can use these example pages to quickly set up a working website in no time.

## Full documentation

Each component, plugin and the general workflow is well documented. Check out the [online documentation for Neumorphism UI](https://themesberg.com/docs/neumorphism-ui/getting-started/quick-start/).

## Workflow

This product is built using the following widely used technologies:

- Most popular CSS Framework Bootstrap
- Productive workflow tool Gulp
- Awesome CSS preprocessor Sass

## Table of Contents

* [Demo](#demo)
* [Quick Start](#quick-start)
* [Documentation](#documentation)
* [File Structure](#file-structure)
* [Browser Support](#browser-support)
* [Resources](#resources)
* [Reporting Issues](#reporting-issues)
* [Technical Support or Questions](#technical-support-or-questions)
* [Licensing](#licensing)
* [Useful Links](#useful-links)

## Demo

| Components | About | Contact |
| --- | --- | --- |
| [![Components](https://themesberg.s3.us-east-2.amazonaws.com/public/products/neumorphism-ui/github/all-components.jpg)](https://demo.themesberg.com/neumorphism-ui/html/components/all.html) | [![About page](https://themesberg.s3.us-east-2.amazonaws.com/public/products/neumorphism-ui/github/about.jpg)](https://demo.themesberg.com/neumorphism-ui/html/pages/about.html) | [![Contact page](https://themesberg.s3.us-east-2.amazonaws.com/public/products/neumorphism-ui/github/contact.jpg)](https://demo.themesberg.com/neumorphism-ui/html/pages/contact.html)

| Login | Register | Documentation |
| --- | --- | --- |
| [![Login page](https://themesberg.s3.us-east-2.amazonaws.com/public/products/neumorphism-ui/github/login.jpg)](https://demo.themesberg.com/neumorphism-ui/html/pages/sign-in.html) | [![Register page](https://themesberg.s3.us-east-2.amazonaws.com/public/products/neumorphism-ui/github/register.jpg)](https://demo.themesberg.com/neumorphism-ui/html/pages/sign-up.html) | [![Documentation](https://themesberg.s3.us-east-2.amazonaws.com/public/products/neumorphism-ui/github/docs.jpg)](https://themesberg.com/docs/neumorphism-ui/getting-started/quick-start/)

-   [Live Preview](https://demo.themesberg.com/neumorphism-ui/)
-   [Details](https://themesberg.com/product/ui-kits/neumorphism-ui?ref=github-neumorphism)

## Quick start

1. Download from [Themesberg](https://themesberg.com/product/ui-kits/neumorphism-ui?ref=github-neumorphism)
2. Download the project's zip
3. Make sure you have Node locally installed.
4. Download Gulp Command Line Interface to be able to use gulp in your Terminal.

```
npm install gulp-cli -g
```

5. After installing Gulp, run npm install in the main `neumorphism/` folder to download all the project dependencies. You'll find them in the `node_modules/` folder.

```
npm install
```

6. Run gulp in the `neumorphism/` folder to serve the project files using BrowserSync. Running gulp will compile the theme and open `/index.html` in your main browser.

```
gulp
```

While the gulp command is running, files in the `assets/scss/`, `assets/js/` and `components/` folders will be monitored for changes. Files from the `assets/scss/` folder will generate injected CSS.

Hit `CTRL+C` to terminate the gulp command. This will stop the local server from running.

## Theme without Sass, Gulp or Npm

If you'd like to get a version of our theme without Sass, Gulp or Npm, we've got you covered. Run the following command:

```
gulp build:dev
```

This will generate a folder `html&css` which will have unminified CSS, Html and Javascript.

## Minified version

If you'd like to compile the code and get a minified version of the HTML and CSS just run the following Gulp command:

```
gulp build:dist
```

This will generate a folder `dist` which will have minified CSS, Html and Javascript.

## Documentation

The documentation for Neumorphism UI is hosted on our [website](https://themesberg.com/docs/neumorphism-ui/getting-started/overview).
