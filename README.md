# simpla-collection
![Version][bower-badge] [![Build status][travis-badge]][travis-url] [![Bower dependencies][bowerdeps-badge]][bowerdeps-url] ![Size][size-badge] [![Published][webcomponents-badge]][webcomponents-url]

Create and manage dynamic collections of content in HTML with Simpla

## Installation & usage

Install simpla-collection with Bower

```sh
$ bower install SimplaElements/simpla-collection --save
```

Import it into the `<head>` of your page

```html
<link rel="import" href="/bower_components/simpla-collection/simpla-collection.html">
```

Then use simpla-collection in your project

```html
<simpla-collection></simpla-collection>
```

### Polyfills for cross-browser support
simpla-collection> relies on emerging standards, for full cross-browser support include the [Web Components Lite](https://github.com/webcomponents/webcomponentsjs) polyfill. 

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/webcomponentsjs/0.7.24/webcomponents-lite.min.js"></script>
```

---

MIT © Simpla &lt;friends@simpla.io&gt;

[bower-badge]: https://img.shields.io/bower/v/simpla-collection.svg
[bowerlicense-badge]: https://img.shields.io/bower/l/simpla-collection.svg
[travis-badge]: https://img.shields.io/travis/SimplaElements/simpla-collection.svg
[travis-url]: https://travis-ci.org/SimplaElements/simpla-collection
[bowerdeps-badge]: https://img.shields.io/gemnasium/SimplaElements/simpla-collection.svg
[bowerdeps-url]: https://gemnasium.com/bower/simpla-collection
[size-badge]: https://badges.herokuapp.com/size/github/SimplaElements/simpla-collection/master/simpla-collection.html?gzip=true
[webcomponents-badge]: https://img.shields.io/badge/webcomponents.org-published-blue.svg
[webcomponents-url]: https://www.webcomponents.org/element/SimplaElements/simpla-collection
