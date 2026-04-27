---
title: "Lesson 4: Doing more with Allmaps"
description: "Now that you've georeferenced a map, how can you do more with Allmaps?"
date: 2026-04-27T02:01:58+05:30
---

{{< callout type="custom" emoji="📚" title="Lesson plan" text="This lesson introduces some additional applications in the Allmaps application, including Viewer, as well as other transformation types. We'll also work together to make a map mosaic of urban atlases that we can all view at the end of the workshop." style="background-color:rgb(244, 228, 245); border: 1px dotted #d340e0;" >}}

{{< toc >}}

## Allmaps Viewer

[Allmaps Viewer](https://viewer.allmaps.org) is used to view georeferenced maps in Allmaps. Similar to the `Results` tab in the Editor, you can see the map overlaid on a web map.
The Viewer also includes additional tools that let you customize the appearance and functionality of your map.

Common tools (found at the bottom of the screen) include sliders that control layer transparency/opacity and background removal.

Background removal is especially useful with historical maps—it removes the blank paper and allows the cartographic information to shine.

![Background removal comparison in Allmaps Viewer](../../images/georef_nz8_Background.png)

Keyboard shortcuts:

- `Space` – Toggle transparency on/off
- `B` – Toggle background removal
- `M` – Display the mask
- `T` – Change the transformation algorithm
- `G` – Display a grid over the image
- `D` – Cycle display of distortions: surface deformation, angle distortion, or none

## Viewing mosaiqued atlases

IIIF manifests often contain objects with multiple maps. Atlases are the quintessential example.

At LMEC, we use Allmaps to work with atlases all the time. Check out this [atlas of Braintree, MA](https://editor.allmaps.org/images?url=https://www.digitalcommonwealth.org/search/commonwealth:xk81nf82h/manifest) in Allmaps Editor, georeferenced by former LMEC interns. Green indicates sheets that are already georeferenced, and the number indicates the number of masks associated with that map image:

![Green indicator for georeferenced pages](../../images/braintreeImages.png)

{{< callout type="warning" text="Yellow warning symbols indicate maps with masks but no georeferencing yet, and red warning symbols indicate a map with errors in its GCPs or mask." >}}

Try [opening this atlas in Allmaps Viewer](https://editor.allmaps.org/images?url=https://www.digitalcommonwealth.org/search/commonwealth:xk81nf82h/manifest) to see how stitched maps are displayed.

As a reminder, you can open a map in Allmaps Viewer using the **Drawers** in the bottom right-hand side of the screen.

When working with multi-sheet objects, the following keystrokes might help:

- `[` and `]`: Cycle through maps
- `Right Click`: Change map layer order

## Changing the transformation algorithm

As we covered in [Lesson 2](../lesson-2), ground control points (GCPs) define locations where features match across old and new maps. A transformation algorithm uses these points to warp the image accordingly.

Cycle through algorithms using `T`.

Different algorithms will produce different results. Some algorithms, like **Thin Plate Spline**, will stretch and distort the image more than others, while algorithms like **Polynomial** maintain a high threshold for distortion:

![Comparison of different transformation algorithms](../../images/transform.gif)

You can set the **transformation type** in the **GCP List Drawer** of Allmaps Editor. Feel free to try it out and see what happens!

## Putting it all together

Now let's try georeferencing and mosaiquing an atlas together! We'll use [this Sanborn atlas of Seattle, WA](https://www.loc.gov/item/sanborn09315_026/manifest.json) from the Library of Congress as an example. 

### Open the atlas

First, open the atlas in [Allmaps Editor](https://editor.allmaps.org).

To open the atlas, recall that you must paste the IIIF manifest into the input box. Digital collections at the Library of Congress are all IIIF-compliant, and their IIIF manifests near the bottom of the object record.

Here's the IIIF manifest for the atlas we're georeferencing:

<a href="https://www.loc.gov/item/sanborn09315_026/manifest.json" target="blank">

```html
https://www.loc.gov/item/sanborn09315_026/manifest.json
```

</a>

### Claim a plate

Visit this [Google Sheet](https://docs.google.com/spreadsheets/d/13KE01w5JwW4Eliabg8qPfmqmJz59M2_2whcW3O6luv4/edit?usp=sharing) and claim an atlas plate to georeference. Depending on how many people are in the workshop, you may be able to claim more than one.

Note that the "Image number" corresponds to the number in Allmaps Editor list, not necessarily the number on the map itself.

When choosing a plate:

1. You don't want to georeference the title sheets or index sheet
2. Use the `image #` underneath each map image as the indicator of which sheet you have chosen

### Georeference

Georeference your map(s)! Follow the best practices for ground control points described in the [previous lesson](../../posts/3-allmaps#ground-control-points).

### View and refine

When everybody is one, we'll view the finished product in Allmaps Viewer.

## Using XYZ tiles in QGIS

Allmaps provides a free **XYZ tile server**, allowing you to bring georeferenced maps directly into GIS software like QGIS.

In **QGIS**, use the **Add XYZ Layer** tool:

![Opening XYZ tile layer dialog in QGIS](../../images/QGIS1.png)

Copy the **XYZ Tile URL** from the Allmaps Editor Share tools:

![Where to find the tile URL](../../images/ShareXYZ.png)

Then create a new XYZ Connection in QGIS and paste in the URL. No other changes are usually needed.

![Adding a new XYZ connection in QGIS](../../images/QGIS2.png)

Now you can use your georeferenced map directly in desktop GIS!

![Georeferenced map shown inside QGIS](../../images/QGIS3.png)

You can even use the **Export** tool to save the result as a **GeoTIFF**, a standard format for georeferenced images.

More info on the Allmaps Tile Server is available in this [Observable notebook](https://observablehq.com/@allmaps/allmaps-tile-server).

## More you can do

What will *you* do with your georeferenced maps?

Here are just a few exciting examples:

- [Stories from Urban Atlases of Waltham](https://www.leventhalmap.org/articles/waltham-urban-atlas-essays/)
- [Atlascope](https://www.atlascope.org/)
- [Architectural Drawings in Allmaps](https://viewer.allmaps.org/?url=https%3A%2F%2Fsammeltassen.nl%2Fiiif-manifests%2Fallmaps%2Frivierahal-blijdorp.json)
- [Georeferenced Aerial Photographs](https://viewer.allmaps.org/?url=https%3A%2F%2Fannotations.allmaps.org%2Fimages%2F4bcc9463d2a68df4)

To go even further, explore the collection of [Allmaps Observable Notebooks](https://observablehq.com/@allmaps):

- Use IIIF maps in MapLibre, Leaflet, or OpenLayers
- Draw vector **GeoJSON** layers on top of Allmaps
- Georeference based on **toponyms** (place names)
- Learn more about the **code and architecture** of Allmaps