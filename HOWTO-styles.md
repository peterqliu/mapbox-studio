Mapbox Studio Vector Tile Styles
======================

Referencing vector tile sources
-------------------------------

In order to design a Mapbox Studio style you will need to have a vector tile source to pull data from. Styles will use the Mapbox Streets source by default, but can also use custom sources you've uploaded to your Mapbox account.

### Remote sources

To change the source of a Mapbox Studio style, click on the __Data layers__ icon near the top-left of the code panel, then click on the blue __Change source__ button at the top of the layers panel. You will be shown a list of any vector tile sources you've uploaded to your Mapbox account.

Mapbox also provides some ready-made sources that you use to design your own custom styles. Documentation is available explaining the data provided by these layers and tips for styling them:

- [Mapbox Streets](https://www.mapbox.com/developers/vector-tiles/mapbox-streets/)
- [Mapbox Terrain](https://www.mapbox.com/developers/vector-tiles/mapbox-terrain/)

### Compositing remote sources

Multiple vector tile sources can be merged together into a single source if they are all hosted on Mapbox.com. For example, you can combine up-to-date OpenStreetMap data from Mapbox Streets with a custom overlay of your own data.

To do this, click on the __Data layers__ icon, then __Change source__, then use the text box below the source list to enter up to 5 map IDs separated by commas. Eg:

    mapbox.mapbox-streets-v5,your-account.abc123

### Local sources

For complex vector tile sources, you might find it helpful to be developing both the source and the style at the same time. Mapbox Studio style projects can also reference local `.tm2source` projects as vector tile sources, so that you can quickly see changes without having to export or upload them.

To reference a local source, click on the Data layers icon, then __Change source__, then toggle from __Remote__ to __Local__. You'll be shown a list of all your local `.tm2source` projects that you can select from.

Local sources will not work in packaged & uploaded styles. Make sure to export & upload your source project and change the reference in your style project before you publish the style.

CartoCSS
--------

Mapbox Studio styles are defined using CartoCSS. A quick introduction to the language and a full reference list of properties are built into Mapbox Studio - click on the help button (question mark icon) at the top-left of the code panel.

If you are new to CartoCSS, the following guides on Mapbox.com will be helpful:

- [Selectors](https://www.mapbox.com/tilemill/docs/guides/selectors/)
- [Styling Lines](https://www.mapbox.com/tilemill/docs/guides/styling-lines/)
- [Styling Polygons](https://www.mapbox.com/tilemill/docs/guides/styling-polygons/)
- [Styling Labels](https://www.mapbox.com/tilemill/docs/guides/styling-labels/)
- [Symbol Drawing Order](https://www.mapbox.com/tilemill/docs/guides/symbol-drawing-order/)

Publishing styles
-----------------

__Note:__ publishing is currently a private beta feature and is not yet available for most Mapbox accounts.

Mapbox Studio styles are packaged into `.tm2z` files for publishing on Mapbox.com. The package contains only the styling information and no data and thus is relatively small. Inside it are:

- `project.xml` - the Mapnik-ready XML style definition automatically built by Mapbox Studio from the project's CartoCSS files and project.yml
- `.png`, `.jpg`, and `.svg` files, unless they begin with an `_`

All other files are omitted from packaging. A `.tm2z` file should not be used as a backup of your `.tm2` project as the original CartoCSS styles are not stored in it or recoverable from it.

If you have any source files (Photoshop/Gimp/Illustrator/Inkscape documents, mockups, reference files, etc) that are not directly required to render the style, they should be named beginning with an underscore or kept in a subdirectory beginning with an underscore. Mapbox Studio will ignore such files & folders when creating packages to deploy for rendering.
