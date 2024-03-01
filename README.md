# Simple Scroll App

 is a lightweight javascript library without jQuery, no dependencies. It is used to make scrollspy effect for your menu, table of contents, etc. Only 1.4Kb.


## Install

### Using NPM package

Install NPM package - https://www.npmjs.com/package/scroll-app-laclac

```npm
npm install scroll-app-laclac
```


## Usages

Easy for using, syntax just like this:

```html
scrollSpy(menuElement, options)
```

This little plugin will add `active` class into your existing menu item when you scroll your page to a matched section by ID.
If you are giving it a try, make sure that you:
1. Added CSS for `active` class in your menu item. Because this plugin doesn't include CSS.
2. Added ID for your sections.
    Example: `<section id="first-section">...</section>`
3. Added an attribute which is a section ID into your menu items. The default value is `href`.
    Example: `"href"="#first-section"`.
You also replace `href` with the other name by `hrefAttribute` in `options`.

### Arguments

1. The `menuElement` is a query selector for your menu. It is `String` or `HTMLElement` instance.
2. The `options` is optional. It types of `Object` contains the properties below:

| Name                   | Type                  | Default      | Description                                                  |
| ---------------------- | :-------------------- | :----------- | :----------------------------------------------------------- |
| `sectionClass`         | String                | `.scrollspy` | Query selector to your sections                              |
| `menuActiveTarget`     | String                | `li > a`     | Element will be added active class                           |
| `offset`               | Number                | 0            | Offset number                                                |
| `hrefAttribute`        | String                | `href`       | The menu item's attribute name which contains section ID     |
| `activeClass`          | String                | `active`     | Active class name will be added into `menuActiveTarget`      |
| `scrollContainer`      | String, HTMLElement   | `window`     | User Defined Scrolling Container                             |
| `smoothScroll`         | Boolean, Object       | `false`      | Enable the smooth scrolling feature                          |
| `smoothScrollBehavior` | Function              | `undefined`  | Define your smooth scroll behavior                           |
| `onActive`             | Function<HTMLElement> | `undefined`  | Trigger after the menu item is added the `activeClass` class |

### ES6 example

```js
import scrollSpy from 'simple-scrollspy'

const options = {
  sectionClass: '.scrollspy',           // Query selector to your sections
  menuActiveTarget: '.menu-item',       // Query selector to your elements that will be added `active` class
  offset: 100,                          // Menu item will active before scroll to a matched section 100px
  scrollContainer: '.scroll-container', // Listen scroll behavior on `.scroll-container` instead of `window`
}

// init:
scrollSpy(document.getElementById('main-menu'), options)

// or shorter:
scrollSpy('#main-menu', options)
```

### Inject static file

```html
<script src="/path/to/dist/simple-scrollspy.min.js"></script>
<script>
  window.onload = function () {
    scrollSpy('#main-menu', {
      sectionClass: '.scrollspy',
      menuActiveTarget: '.menu-item',
      offset: 100,
      // smooth scroll
      smoothScroll: true,
      smoothScrollBehavior: function(element) {
        console.log('run "smoothScrollBehavior"...', element)
        element.scrollIntoView({ behavior: 'smooth' }) // default behavior
      }
    })
  }
</script>
```

### Smooth scroll

```javascript
import jumpTo from 'jump.js'

scrollSpy('#main-menu', {
  // ....,

  // enable smooth scroll:
  // - true: enable with the default scroll behavior
  // - false: disable this feature
  // - object: enable with some options that will pass to `Element.scrollIntoView` or `smoothScrollBehavior`
  //   + Default behavior: https://developer.mozilla.org/en-US/docs/Web/API/Element/scrollIntoView
  //   + Jump.js: https://www.npmjs.com/package/jump.js
  smoothScroll: true,

  // customize scroll behavior,
  // - default: Element.scrollIntoView({ ...smoothScroll, behavior: 'smooth' })
  // - customize: you can define your scroll behavior. Ex: use `jump.js`, jQuery, .etc
  smoothScrollBehavior: function(element, options) {
    // use `jump.js` instead of the default scroll behavior
    jumpTo(element, {
      duration: 1000,
      offset: -100,
    })
  }
})
````

## Helpful links
- [Documentation](https://github.com/brittanytatum241/app-scrollspy)

- [See on NPM package](https://www.npmjs.com/package/app-scrollspy)

## Licence
[MIT](./LICENSE)
# app-scrollspy
