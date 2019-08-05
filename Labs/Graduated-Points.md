![logo](Images/Logo.png)

## Mapping rodent incidence by council district 

In this tutorial you will:

* Upload data as a dataset
* Draw & edit data with the dataset editor 
* Create centroid points in QGIS
* Upload data as a tileset 
* [Create a style](https://docs.mapbox.com/help/how-mapbox-works/map-design/#how-map-styles-work) for a basemap.
* [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
* [Add data](https://www.mapbox.com/help/uploads/) to a style
* Embed a map into a web page

## Software requirements

* Mapbox account
* QGIS
* Text editor 
* GitHub Account

## Data
[Council District GeoJSON](https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Data/Council%20Districts.geojson)
[Rodent Incident Table](https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Data/Rodent_Incidence.csv)

## Uploading and editing datasets to Mapbox

You can use the Mapbox Studio [dataset editor](https://studio.mapbox.com/datasets/) to import, create, and edit point, line, and polygon features and their properties. A collection of these features in Mapbox is called a [dataset](https://docs.mapbox.com/help/glossary/dataset/). Datasets can either be downloaded as GeoJSON or exported to tilesets for use in Mapbox styles (see the [Introduction](https://docs.mapbox.com/studio-manual/overview/) section for more information). 

## [What is a dataset?](https://docs.mapbox.com/studio-manual/reference/datasets/#what-is-a-dataset)

A dataset is an editable collection of [GeoJSON](https://www.mapbox.com/help/define-geojson) features. Datasets are distinct from [tilesets](https://www.mapbox.com/help/define-tileset) in that datasets can be edited on a feature-by-feature basis, but cannot be used directly in [Mapbox Studio style editor](https://docs.mapbox.com/studio-manual/reference/styles/#style-editor).

To get started with this tutorial, you will need to go to the [dataset editor](https://studio.mapbox.com/datasets/) in Mapbox Studio and upload your District Council data. 

![DatasetUpload](Images/Dataset_Upload.png)

On your Datasets page, click the __Upload dataset__ button and select the District Council GeoJSON from your local drive. 

![DatasetUpload](Images/dataset-upload.gif)

Explore your dataset by clicking on different polygons. What property values to see on the left side of the screen? 

![DatasetExplorer](Images/dataset_explore.gif)


Notice that there are multiple polygons with the same name - there are two polygons for district council 'North', two for 'Niagara' amd 4 polygon features for 'Lovejoy'. Before we continue with this exercise, we need to merge our polygon features. Let's start by selecting both of the 'North' district council polygons. Hold down the shift button to select both features at once. With both features selected, click on the __Combine features into multifeature__ button.


![Multifeatures](Images/Multifeatures.png)

Repeat the steps above for both the 'Niagara' and 'Lovejoy' districts (hint: one of the polygons for the Lovejoy district is very small, you may have to zoom in to see it). 

You should now have a single polygon feature for each of the council districts. Next, we will add a new property field to each of our polygons. The new property field will contian information about the incidence of rodents in each district area. The following table contains information on the rodent incidence rate by district: 

| Council District | Incidence Rate |
|------------------|----------------|
| Delaware         | 1950           |
| Ellicott         | 1556           |
| Fillmore         | 2344           |
| Lovejoy          | 2278           |
| Masten           | 2319           |
| Niagara          | 2265           |
| North            | 1912           |
| South            | 2155           |
| University       | 1596           |



Select the 'North' district polygon and select __+ Add Property__ located under the properties panel on the left side of your screen. Add a new property field called __Incidence__ and set the value to 1912 (same as the table above). Select __Confirm__ when you have made this changes. 

![Incidence](Images/incidence.png)

Next, select the 'Niagara' district polygon and select __+ Add Property__ located under the properties panel on the left side of your screen. Add a new property field called __Incidence__ (you can set the field name by selecting the 'available field names' pop up) and set the value to 2265 (same as the table above). Select __Confirm__ when you have made this changes. 

![Available_Fields](Images/available_fields.png)

Repeat these steps for each council district. 

Once you are finished, select __save__ and return to the [dataset editor homepage](https://studio.mapbox.com/datasets/).

Our final map for this tutorial is going to be a graduated point map of rodent incidence rates by council district. In order to creat this map, we will need to create centroid points for each of the polygon features. We will use QGIS to create the centroid points. 

Download your edited dataset as a GeoJSON by clicking on the ![options | 75%](Images/Symbol.png) button and selecting download. 

![Dataset Download](Images/Dataset_Download.png)

Open QGIS and add the Council District GeoJSON that you just downloaded as a vector layer to your map. 

Use the __Processing Toolbox__ search bar to find the Vector geometry __Centroids__ tool. This tool creates a new point layer, with points representing the centroid of the geometries in an input layer. Make sure that your __Council_Districts__ layer is selected as the input layer and hit __run__.

<p align = "center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Images/Centroid_Tool.png" width="754" height="454" title="QGIS">
</p>

Right click on the layer and select __Export__ --> __Save Feature As__ and export your file as a GeoJSON. 

We have now successfully created a point feature from our polygon file! There is still one more pre-processing step that we need to do before we can style our data in Mapbox Studio. A common error that occurs when uploading GeoJSON data to Mapbox is that the GeoJSON contains an old-style CRS attribute. To prevent this error, open your GeoJSON in a text editor (for this example, we will be using Atom). Delete the CRS attribute from your code and save your edits. For more information about common data uploading errors check out this helpful [documentation](https://docs.mapbox.com/help/troubleshooting/uploads/).

<p align = "center">
  <img src="https://github.com/mjdanielson/University-of-Buffalo/blob/master/Labs/Images/Text_Editing.png" title="Text Editing">
</p>




