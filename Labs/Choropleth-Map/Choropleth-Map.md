<img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Logo.png">

## Mapping rodent incidence by census tract

In this tutorial you will:

* Upload data as a tileset
* [Create a style](https://docs.mapbox.com/help/how-mapbox-works/map-design/#how-map-styles-work) for a basemap.
* [Add data](https://www.mapbox.com/help/uploads/) to a style
* [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
* Create a web map with basic interactivity 

## Software requirements

* Mapbox account
* JSFiddle 

## Data

## Upload data as a tileset

Let's upload our data to the [tileset editor](https://studio.mapbox.com/tilesets/).  At the top of the tileset editor page, select
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Tileset.png" width="82" height="26" title="Tileset Upload">. Select __Upload File__ and __Select a file__ and navigate to the file containing your census data tracts GeoJSON and select __Confirm__. 

  <p align= 'center'>
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Census_Tileset.png" title="Tileset1">
  </p>

When you upload vector data to your Mapbox account, our servers convert it to a [vector tileset](https://docs.mapbox.com/help/glossary/tileset/) so it can be rendered quickly and efficiently in the Mapbox Studio style editor and with Mapbox GL JS. The tileset information page shows some useful information about the tileset that was created from your uploaded data. Feel free to explore the information page for each of your new tilesets. 


## Create a style for a basemap
  
After you've inspected your data, it's time to create a new style so you can put it on the map! Go to your [Styles page](https://studio.mapbox.com/). Click the <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/New_Style.png" width="82" height="26" title="New Style"> button. Find the Dark Template style and click __Customize Dark__

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Dark_Style.png" title="Rename"> 
</p>

Excellent! Welcome to the Mapbox Studio style editor. This is where you will create your map style!

Rename the style so that you can find it later. Click into the title field in the upper left side of the screen to change the title from Basic Template to __Choropleth Map__.  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/New_Style.png" width="82" height="26" title="New Style"> button.


_You can always refer to the [Mapbox Studio Manual](https://www.mapbox.com/studio-manual/reference/styles/) for more information on getting started._

## [Add data](https://www.mapbox.com/help/uploads/) to a style

To add and style the council district data, you will need to add a new layer to the map. At the top of the layer panel, click <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Add_Layer.png" width="82" height="26" title="Add Layer">.

<p align = "center">
  <img src = "https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Graduated-Points/Images/Add_Layer.gif">
  </p>

The editor is now showing your map in “x-ray mode.” X-ray mode shows all the data in the sources added to the style, regardless of whether there is a layer to style it.

In the New layer panel, look in the list of Data sources for the __Census Tracts__ source. Click the tileset and then select the source layer as the source for this new style layer.

The default Basic map view is not centered on Buffalo, New York. Mapbox Studio recognizes that the data you have uploaded is focused on a different location, so it displays the message "This tileset isn't available from your map view." Click __Go to data__, and the map view will refocus on the United States. Zoom to your layer (Buffalo, New York). 

Each layer in Studio can be styled individually by clicking on the name of the layer in the Layer list. There are several layer types to choose from. Each layer type has a unique set of layer properties that can be specified. There are a few options for specifying property values. You can pick values individually, based on a data attribute, based on the zoom level, or the value of another property. For more information on layer types and their styling rules check out this [reference guide](https://docs.mapbox.com/studio-manual/reference/styles/).
