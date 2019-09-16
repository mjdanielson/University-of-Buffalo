<img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Logo.png">

## Mapping rodent incidence by census tract

In this tutorial you will:

* Upload data as a tileset
* [Create a style](https://docs.mapbox.com/help/how-mapbox-works/map-design/#how-map-styles-work) for a basemap.
* [Add data](https://www.mapbox.com/help/uploads/) to a style
* [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
* Create a web map 
* Adding a legend 
* Adding basic interactivity to your map 

## Software requirements

* Mapbox account
* JSFiddle 

## Data

[Census Tract Data](https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Data/Census_Tracts.geojson)

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
    </style>
</head>
<body>
</body>
</html>

```

### Add a title, info box, and legend (front-end UI):

Add the following code between the ```<body>``` opening and ```</body>``` closing tags:

```
<div id='map'></div>
<div class='map-overlay' id='features'><h2>Rodent Incidence by Census Tract</h2><div id='pd'><p>Hover over a census tract!</p></div></div>
<div class='map-overlay' id='legend'></div>
```

Next, you will also want to apply some CSS to visualize what the layout looks like. This creates the visual rules for our front-end elements (legend, title box, information box). Under the opening <style> tag at the top of your code, add the following: 
  
```  
  body {
  margin: 0;
  padding: 0;
}

h2,
h3 {
  margin: 10px;
  font-size: 1.2em;
}

h3 {
  font-size: 1em;
}

p {
  font-size: 0.85em;
  margin: 10px;
  text-align: left;
}

/**
* Create a position for the map
* on the page */
#map {
  position: absolute;
  top: 0;
  bottom: 0;
  width: 100%;
}

/**
* Set rules for how the map overlays
* (information box and legend) will be displayed
* on the page. */

.map-overlay {
  position: absolute;
  bottom: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.8);
  margin-right: 20px;
  font-family: Arial, sans-serif;
  overflow: auto;
  border-radius: 3px;
}

#features {
  top: 0;
  height: 100px;
  margin-top: 20px;
  width: 250px;
}

#legend {
  padding: 10px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
  line-height: 18px;
  height: 100px;
  margin-bottom: 40px;
  width: 100px;
}

.legend-key {
  display: inline-block;
  border-radius: 20%;
  width: 10px;
  height: 10px;
  margin-right: 5px;
}
```

Hit run to see your changes. 

In the next step, you will add the map to your page and the project will start taking shape.

### Initialize the map 

For the next step you will need a [Mapbox access token](https://docs.mapbox.com/help/how-mapbox-works/access-tokens/) and your [style ID](https://docs.mapbox.com/help/glossary/style-id/). Without this, the rest of the code will not work. 

<p align = "center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Access_Token.png">
</p>

<p align = "center">
<img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Style_ID.gif">
</p>

Add the following code after ```<div class='map-over' id='legend'></div>``` and before the closing ```</body>``` tag

```
<script>
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'your-style-url', // replace this with your style URL
    center: [,], // starting position [lng, lat] - adjust the starting position to be centered on Buffalo, New York 
    zoom: 3 // starting zoom - change the starting zoom position to 11 
});
</script>
```

Add your style id to the map variable. Edit the line of code that has the comment 'replace this with your style URL'.

```
style: 'your-style-url', // replace this with your style URL
```

Next, we want to center our map onto Buffalo, New York. Locate the line of code that is telling the map where to center the view. Try changing the center location by picking a new coordinate using http://geojson.io/ (or looking at the bottom of the right-hand panel in the Mapbox Studio style editor). Change the coordinates in your code and run your changes.

```
center: [,], // starting position [lng, lat] - adjust the starting position to be centered on Buffalo, New York 
```

Change the zoom level to 11.

```
zoom: 3 // starting zoom - change the starting zoom position to 11 
```

Hit run to see your changes. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Map_No_Legend.png">
</p>


### Add additional information

With some projects, this is where you'd stop: you put a map on a page! But for this map, you will add two pieces of additional information that will make the map even more useful: a legend and an information window that shows the population density for whatever state the cursor is hovering on

### [The load event](https://docs.mapbox.com/help/tutorials/choropleth-studio-gl-pt-2/#the-load-event)

What is a callback?

Initializing the map on the page does more than create a container in the map div. It also tells the browser to request the Mapbox Studio style you created in part 1. This can take variable amounts of time depending on how quickly the Mapbox server can respond to that request, and everything else you're going to add in the code relies on that style being loaded onto the map. As such, it's important to make sure the style is loaded before any more code is executed.

Fortunately, the map object can tell your browser about certain events that occur when the map's state changes. One of these events is load, which is emitted when the style has been loaded onto the map. Through the map.on method, you can make sure that none of the rest of your code is executed until that event occurs by placing it in a [callback function](https://github.com/maxogden/art-of-node#callbacks) that is called when the load event occurs.

To make sure the rest of the code can execute, it needs to live in a callback function that is executed when the map is finished loading.

Add the load event before the closing script tag ```</script>``` -- __The rest of your code will go inside of the load callback function.__

```
map.on('load', function() {
  // the rest of the code will go in here
});
```

### [Create arrays of intervals and colors](https://docs.mapbox.com/help/tutorials/choropleth-studio-gl-pt-2/#create-arrays-of-intervals-and-colors)

Creating a list of the stops you used when styling your layer that contains state data will allow us to add a legend to our map in a later step.

__Remember: this code goes inside of the load callback function!__

```
var layers = ['0-112', '112-227', '227-308', '308-424', '424-577'];
var colors = ['#edf8fb', '#b3cde3', '#8c96c6', '#8856a7', '#810f7c']; //add the colors that we used to style our choropleth map!
```

### Add a legend

The following code adds a legend to the map. To do so, it iterates through the list of layers you defined above and adds a legend element for each one based on the name of the layer and its color. 

```
for (i = 0; i < layers.length; i++) {
  var layer = layers[i];
  var color = colors[i];
  var item = document.createElement('div');
  var key = document.createElement('span');
  key.className = 'legend-key';
  key.style.backgroundColor = color;

  var value = document.createElement('span');
  value.innerHTML = layer;
  item.appendChild(key);
  item.appendChild(value);
  legend.appendChild(item);
}
```

Hit run to see your changes. The legend box is slightly too big. Can you figure out how to adjust the height of the legend box in your code? Change the height to 100 px.

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/Map_legend.png">
 </p>

Your code should look like this:

```
map.on('load', function() {
  // the rest of the code will go in here
var layers = ['0-112', '112-227', '227-308', '308-424', '424-577'];
var colors = ['#edf8fb', '#b3cde3', '#8c96c6', '#8856a7', '#810f7c']; //add the colors that we used to style our choropleth map!

for (i = 0; i < layers.length; i++) {
  var layer = layers[i];
  var color = colors[i];
  var item = document.createElement('div');
  var key = document.createElement('span');
  key.className = 'legend-key';
  key.style.backgroundColor = color;

  var value = document.createElement('span');
  value.innerHTML = layer;
  item.appendChild(key);
  item.appendChild(value);
  legend.appendChild(item);
}
});

````

### Add the information box 

When the cursor is hovering over a census tract, the information window should show the rodent incidence information for that state. If the cursor is not hovering over a state, the information window should say, "Hover over a census tract!"

To do this, add a listener for the mousemove event, identify which census tract is at the location of the cursor if any, and update the information window:

```
map.on('mousemove', function(e) {
  var tracts = map.queryRenderedFeatures(e.point, {
    layers: ['Rodent Incidence']
  });

  if (tracts.length > 0) {
    document.getElementById('pd').innerHTML = '<h3><strong>' + tracts[0].properties.Incidence + '</strong></h3><p><strong><em>';
  } else {
    document.getElementById('pd').innerHTML = '<p>Hover over a census tract!</p>';
  }
});

```

### Cursor

Add a single line of code to give the map the default pointer cursor.

```map.getCanvas().style.cursor = 'default';```

## Mission complete

You have created an interactive choropleth map!

<p align = "center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/Images/final_map.png">
 </p>

The final code can be [here](https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Choropleth-Map/index.html).

