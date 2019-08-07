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

## [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style

Click the Style tab and the map will switch back to style mode displaying your new layer. You will see the polygon data on the map with a default style (black with 100% opacity). 

In the Mapbox Studio style editor, you can assign a color to each state based on its number of rodent incidents in a census tract. Change the name of your data layer to 'Rodent Incidents' and select __color__ ,  __style across a data range__ and then select the __incidence #__ field.

<p align = "center">
  <img src= "https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Rename_Layer.gif">
</p>

The rate of change is set to __Linear__. Click Edit and select __Step__ instead. Click Done. Since you have set the rate of change to step, the colors for each range of density between stops will be uniform.

Now it's time to start adding stops and colors! You will create several stops to break states up into groups with similar overdose rates. We will be breaking the data out into 5 classes using the [Jenks natural breaks](https://en.wikipedia.org/wiki/Jenks_natural_breaks_optimization) method. 

| Incidence Bins   |  Color   |
|------------------|----------|
| 0 - 112          | #edf8fb  |
| 112 - 227        | #b3cde3  |
| 227 - 308        | #8c96c6  |
| 308 - 424        | #8856a7  |
| 424 - 577        | #810f7c  |


Use the color hex codes in the table above to create a color ramp or choose your own colors using [colorbrewer](http://colorbrewer2.org/).

To create the color ramp, locate the __Edit__ button in the first incidence rate stop, which should be fixed at 0. Click on it and change the color to #edf8fb (or your own color). Click Done. 

Next, select the next incidence step (this should be set to 577) and change the incidence number to 112. Adjust the color to match the next step in your color ramp, in this example we will be using #b3cde3. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Color_Change.gif">
 </p>
 
To add another step, select __+ Add another stop__ and type in 227 as the next incidence step. Adjust the color to match your color ramp (#8c96c6) and select __done__. Add the last two stop 308 and 424 and adjust their colors accordingly. 

<p align="center">
  <img src = "https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Color_Ramp.png">
</p>

Once you have finished creating your color ramp, select __opacity__ and change the opacity to __0.7__.  

Play around with some of the other layers made available to you in Studio. Try moving layers to the top of layer list to make them more visible on your map. 

Try adjusting the colors of other layers to create your own unique style. 

## Publish your style 

Now that you've got your map looking good, it's time to publish! Click the Publish style button at the top of the toolbar on the right side of the screen, then click Publish again on the next prompt.

Hooray! Your style is now published! If you go back to your Styles page, you will see your new style at the top of the list.

You can use your ‘Share URL’ to open your style in a new browser tab and share it with collaborators for review.


## Create a web map 

## Create a web map 

Now that we have edited our layers and created a style, let's create a web map! 

For this part of the lesson, we will be using a program called JSFiddle. You can sign up for a free acount at: https://jsfiddle.net/

JSFiddle is a simple tool for building and testing code for web development. We recommend using JSFiddle in a Chrome browser

For simplicity, we recommend that you change the editor layout settings in JSFiddle to display by ‘tabs’.

Initialize your map by copying the following code into the HTML tab of your JSFiddle:

```
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title>Choropleth Map</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.1.0/mapbox-gl.css' rel='stylesheet' />
    <style>
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
    </style>
</head>

```

For the next step you will need a [Mapbox access token](https://docs.mapbox.com/help/how-mapbox-works/access-tokens/) and your [style ID](https://docs.mapbox.com/help/glossary/style-id/). 

<p align = "center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Access_Token.png">
</p>

<p align = "center">
<img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Style_ID.gif">
</p>
