<table>
<tr>
<th>action</th>
<th>overview</th>
</tr>
<tr>
<td><code>Load</code></td>
<td>

`Load` replaces an entire asset with a version you provide.

For example, if you have an `assets/abigail.png` image with custom portraits for Abigail, this
would change her portraits in-game:

```js
{
   "Format": "1.28.0",
   "Changes": [
      {
         "Action": "Load",
         "Target": "Portraits/Abigail",
         "FromFile": "assets/abigail.png"
      }
   ]
}
```

This isn't recommended if you can use one of the `Edit*` actions instead.

See the [`Action: Load` documentation](author-guide/action-load.md) for more info.

</td>
</tr>
<tr>
<td><code>EditData</code></td>
<td>

`EditData` changes the data read from a data asset. This supports simple lookup assets like
`Data/ObjectInformation`, or full data model assets like `Data/WildTrees`. Any number of content
packs can edit the same asset.

This lets you...
* add, edit, or delete entries;
* reorder entries in a list;
* or edit individual fields within an entry.

For example, this doubles the price of coffee (see [object fields](https://stardewvalleywiki.com/Modding:Object_data)):

```js
{
    "Format": "1.28.0",
    "Changes": [
        {
            "Action": "EditData",
            "Target": "Data/ObjectInformation",
            "Fields": {
                "395": {   // item #395 (coffee)
                    1: 300 // set field 1 (price) to 300g
                }
            }
        }
    ]
}
```

You can do much more using `EditData`, including add completely custom items, fruit trees, etc.
See the [`Action: EditData` documentation](author-guide/action-editdata.md) for more info.

</td>
</tr>
<tr>
<td><code>EditImage</code></td>
<td>

`EditImage` edits one of the game's image assets. Any number of content packs can edit the same
image.

This lets you...
* edit or replace any portion of the image;
* overlay a new image onto the existing one with transparency support;
* or extend the image size (e.g. to add more sprites to a spritesheet).

For example, if your content pack has an `assets/tuna.png` image with a custom
[tuna](https://stardewvalleywiki.com/Tuna) sprite, this would replace tuna sprites in-game:

```js
{
   "Format": "1.28.0",
   "Changes": [
      {
         "Action": "EditImage",
         "Target": "Maps/springobjects",
         "FromFile": "assets/fish-object.png",
         "ToArea": { "X": 160, "Y": 80, "Width": 16, "Height": 16 }
      }
   ]
}
```

See the [`Action: EditImage` documentation](author-guide/action-editimage.md) for more info.

</td>
</tr>
<tr>
<td><code>EditMap</code></td>
<td>

`EditMap` changes part of an in-game map. Any number of content packs can edit the same map.

This lets you...
* change map properties, tile properties, and tiles;
* paste a local map into part of the target map (with various merge options);
* add custom tilesheets;
* or resize the map (e.g. to add more content to an existing game location).

For example, this replaces the town square with a custom version in your content folder:
```js
{
    "Format": "1.28.0",
    "Changes": [
        {
            "Action": "EditMap",
            "Target": "Maps/Town",
            "FromFile": "assets/town.tmx",
            "ToArea": { "X": 22, "Y": 61, "Width": 16, "Height": 13 }
        }
    ]
}
```

See the [`Action: EditMap` documentation](author-guide/action-editmap.md) for more info.

</td>
</tr>
<tr>
<td><code>Include</code></td>
<td>

`Include` adds patches from another file. This is just a way to organize your content pack into
multiple files, instead of having everything in one `content.json`. The included patches work
exactly as if they were directly in `content.json`.

For example, you can combine this with [tokens and condition](#tokens) to load a dynamic file:
```js
{
    "Format": "1.28.0",
    "Changes": [
        {
            "Action": "Include",
            "FromFile": "assets/john_{{season}}.json"
        }
    ]
}
```

See the [`Action: Include` documentation](author-guide/action-include.md) for more info.

</td>
</tr>
</table>
