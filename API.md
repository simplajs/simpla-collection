# API Reference

## Properties

Property   | Type      | Default     | Description                                                 
---------- | --------- | ----------- | -----------                                                 
`path`     | `String`  | `undefined` | Path to the data for the collection on Simpla's API            
`items`    | `Array`   | `[]`        | Array of the items in the collection
`as`       | `String`  | `'item'`    | Item name/key used throughout simpla-collection             
`editable` | `Boolean` | `false`     | Whether the collection is editable                             
`readonly` | `Boolean` | `false`     | Whether the collection is able to become editable                                 
`active`   | `Boolean` | `false`     | Whether the collection is currently being edited               
`loaded`   | `Boolean` | `false`     | Whether the collection content has been loaded from Simpla     

Properties can be set with JavaScript or as attributes on the element

```html
<simpla-collection path="/collection" as="item">
  <template>...</template>
</simpla-collection>

<script>
  document.querySelector('simpla-collection').editable = true;
</script>
```

## Schema

**Type:** `'Collection'`

Data    | Type             | Description                                           
------- | ---------------- | -----------                                           
`items` | `Array<Object>`  | Ordered array of the items in the collection, represented as objects with an `id` property

```json
{
  "path": "/collection/path",
  "type": "Collection",
  "data": {
    "items": [
      { "id": "dwubz" },
      { "id": "h3sqb" },
    ]
  },
  "createdAt": "2017-04-16T09:58:56.276Z",
  "updatedAt": "2017-05-09T09:25:36.835Z"
}
```

## Events

Event              | Properties       | Description                                    
------------------ | ---------------- | -----------                                    
`items-changed`    | `value{Array}`   | Fired when `items` property changes      
`as-changed`       | `value{String}`  | Fired when `as` property changes      
`editable-changed` | `value{Boolean}` | Fired when `editable` property changes 
`active-changed`   | `value{Boolean}` | Fired when `active` property changes
`loaded-changed`   | `value{Boolean}` | Fired when `loaded` property changes      
