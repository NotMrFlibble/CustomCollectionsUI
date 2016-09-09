# CustomCollectionsUI
Modify Starbound's collections window to handle custom collections

## Mod authors and maintainers: how to create an item collection

Example file: `/collections/prefix-mycollection.collection`

Example content:
```{
  "name" : "prefix_mycollection",
  "title" : "My Collection",
  "type" : "item",
   "collectables" : {
    "item1" : { "order" : 1, "item" : "item1" },
    "item2" : { "order" : 2, "item" : "item2" },
    "item3" : { "order" : 3, "item" : "item3" },
  }
}```

In the .object files for item1, item2 and item3, add a key looking like
this:
```"collectablesOnPickup" : { "prefix_mycollection" : "item1" }```

And in `/interface/scripted/collections/collectionsgui.config.patch`
(so that this mod can find your collection):
```[
  {
    "op": "add",
    "path": "/customCollections/-",
    "value": "prefix_mycollection"
  }
]```

You will need to depend on this mod if you want to guarantee it being able
to see your collection(s).
