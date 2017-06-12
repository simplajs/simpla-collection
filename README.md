# Simpla Collection
[![Build status][travis-badge]][travis-url] ![Size][size-badge] ![Version][bower-badge] [![Published][webcomponents-badge]][webcomponents-url] [![Simpla slack group][slack-badge]][slack-url]

Simpla-collection lets you create dynamic collections of content in HTML. It consumes a HTML template, which users can add, remove, and reorder instances of inline on your page. It's built on the [Simpla][simpla] content system.

<!---
```
<custom-element-demo>
  <template>
    <script src="../webcomponentsjs/webcomponents-lite.js"></script>
    <script src="https://unpkg.com/simpla@^2.0.0"></script>
    <script>
      Simpla.init('local');
      Simpla.editable(true);
    </script>

    <link rel="import" href="simpla-collection.html">
    <link rel="import" href="../simpla-img/simpla-img.html">

    <style>
      body {
        min-height: 350px
      }
      img {
        max-width: 15rem;
      }
      simpla-collection {
        margin-top: 2rem;
      }
    </style>
    <next-code-block></next-code-block>
  </template>
</custom-element-demo>
```
-->
```html
<simpla-collection path="/collection">
  <template>
    <img is="simpla-img" path="/collection/[item]">
  </template>
</simpla-collection>
```

## Installation and setup

Install simpla-collection with Bower (Yarn support coming soon)

```sh
$ bower i simpla-collection --save
```

[Setup Simpla][setup-simpla] on your page, then import simpla-collection into your `<head>`

```html
<link rel="import" href="/bower_components/simpla-collection/simpla-collection.html">
```

Use the `<simpla-collection>` element wherever you want to create a collection of items. Define the item template in a `<template>` inside simpla-collection. Give each collection a unique `path`, where it will store its content in your project. Simpla-collection also exposes an `[item]` key to use in the paths of Simpla elements inside your template.

```html
<simpla-collection path="/collection">
  <template>
    <img is="simpla-img" path="/collection/[item]">
  </template>
</simpla-collection>
```

## Editing a collection

Manage the items in your collection by entering edit mode with Simpla (which makes all Simpla elements on a page editable) or setting the `editable` property directly on the element.

```js
// Enter edit mode
Simpla.editable(true);
```

```html
<!-- Make only this collection editable -->
<simpla-collection path="/collection" editable>
  <template>...</template>
</simpla-collection>
```

Entering edit mode with Simpla is the recommended way to edit collections. It ensures all elements on a page remain in sync and updates Simpla's public `'editable'` state, which other elements may rely on.

## Saving collections

Save a `simpla-collection` by calling Simpla's `save` method, which will save all modified content on the page. It returns a promise.

```js
// Save all modified Simpla content
Simpla.save();
```

> You must be authenticated with Simpla before saving content

## Using simpla-paths

Simpla-collection works with [simpla-paths](https://github.com/SimplaElements/simpla-paths), which lets you build content paths for Simpla elements declaratively with HTML attributes. This is useful for creating more complex collection items

```html
<simpla-colleciton sid="faqs">
  <template>
    <div sid="[item]">
      <simpla-text sid="question"></simpla-text> 
      <simpla-text sid="answer"></simpla-text> 
    </div>
  </template>
</simpla-colleciton>
```

## Custom item names

You can change the default item name used by simpla-collection with the `as` property. Setting a custom item name changes the key used for templating Simpla paths, as well as labels throughout simpla-collection's edit UI. It doesn't effect the data saved by the colleciton.

```html
<simpla-collection path="/gallery" as="image">
  <template>
    <img is="simpla-img" path="/gallery/[image]">
  </template>
</simpla-collection> 
```

## Collection data model

Simpla-collection stores meta information about its items on Simpla's API and in its `items` property as an ordered Array:

```js
[
  { id: 'dwubz' },
  { id: 'h3sqb' },
  ...
]
```

The order of the items objects in the `items` array determines the order of the items rendered in the collection.

Each item has a unique ID, which is generated for the `[item]` templating key in the item template. A single item ID can map to several paths of content. For example, given the following template:

```html
<simpla-collection path="/gallery">
  <template>
    <img is="simpla-img" path="/gallery/[item]/img">
    <simpla-text path="/gallery/[item]/caption"></simpla-text>
  </template>
</simpla-collection> 
```

A single item ID (eg: `'dbuwz'`) would map to the following paths:

```
/gallery/dbuwz/img
/gallery/dbuwz/caption
```

## API reference

### Properties

Property      | Type    | Default           | Description                                                   
------------- | ------- | ----------------- | -----------                                                   
`items`       | Array   | `[]`              | Array of the items in the collection, saved to Simpla's API
`as`          | Array   | `'item'`          | Item name/key used throughout simpla-collection
`path`        | String  | `undefined`       | Path to the data for the collection on Simpla's API
`editable`    | Boolean | `false`           | Whether the collection is editable                                 
`active`      | Boolean | `false`           | Whether the collection editor is open                   

Properties can be set either directly with JavaScript or as attributes on the element

```html
<simpla-collection path="/collection">
  <template>...</template>
</simpla-collection>

<script>
  document.querySelector('simpla-collection').editable = true;
</script>
```

### Events

Event              | Description                                    
------------------ | -----------                                    
`items-changed`    | Fired whenever the `items` property changes      
`as-changed`       | Fired whenever the `as` property changes      
`editable-changed` | Fired whenever the `editable` property changes 
`active-changed`   | Fired whenever the `active` property changes   

## Contributing

If you find any issues with simpla-collection please report them! If you'd like to see a new feature in supported file an issue or let us know in Simpla's public [Slack group](https://slack.simpla.io). We also happily accept PRs. 

***

MIT © [Simpla][simpla]

[simpla]: https://www.simpla.io
[setup-simpla]: https://www.simpla.io/docs/guides/get-started
[bower-badge]: https://img.shields.io/bower/v/simpla-collection.svg
[bowerlicense-badge]: https://img.shields.io/bower/l/simpla-collection.svg
[travis-badge]: https://img.shields.io/travis/SimplaElements/simpla-collection.svg
[travis-url]: https://travis-ci.org/SimplaElements/simpla-collection
[bowerdeps-badge]: https://img.shields.io/gemnasium/SimplaElements/simpla-collection.svg
[bowerdeps-url]: https://gemnasium.com/bower/simpla-collection
[size-badge]: http://img.badgesize.io/SimplaElements/simpla-collection/master/simpla-collection.html?compression=gzip&label=render_bundle_%28gzip%29
[webcomponents-badge]: https://img.shields.io/badge/webcomponents.org-published-blue.svg
[webcomponents-url]: https://www.webcomponents.org/element/SimplaElements/simpla-collection
[slack-badge]: http://slack.simpla.io/badge.svg
[slack-url]: https://slack.simpla.io

