## Mapping Census of Canada Data
<br/>
<br/>

Jeremy Buhler, Data Librarian\
[jeremy.buhler@ubc.ca](mailto:jeremy.buhler@ubc.ca)<!-- .element: class="smaller" --> 

Paul Lesack, Data & GIS Analyst\
[paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca)<!-- .element: class="smaller" --> 

Note: 

---

## Learning objectives  

- Understand how Census data is collected and released <!-- .element: class="fragment" -->
- Find and download Census data and boundary files <!-- .element: class="fragment" -->
- Learn about supporting data and tools (e.g. CanMap Content Suite) <!-- .element: class="fragment" -->
- Distinguish among map types <!-- .element: class="fragment" -->

Note: This session is an overview and doesn't allow time for hands-on discovery. It will introduce you to terms and resources that should help you navigate Statistics Canada Census resources. If you have further questions please contact us for individual support.  

The presentation will introduce you to a couple of places where you can find Census Data to use for mapping. Please bear in mind this is just an orientation to get you started - depending on your goals there may be other Census products better suited to your needs. If you have questions about finding data of any kind (not just Census), please contact us at UBC Library.

Possibly ask students for show of hands, to prompt engagement and gauge class level (could be different questions)
- who has prior experience working with Census data? 

---

## Census of population: data collection 

- Collected every 5 years (2016, 2021, 2026...)
- Mandated by law
- _Short form_ (100%) and _long form_ (25%) [questionnaires](https://www12.statcan.gc.ca/census-recensement/2021/ref/98-304/2021001/chap5-eng.cfm) 


Note: From StatCan info page: "The Census of Population is the primary source of socioeconomic data for specific population groups and for detailed or small geographies. The Census of Population is mandated by law in the Constitution Act (1867) and the Statistics Act (1985) to determine the population of Canada and its' provinces and territories, every five years."

"The data are needed by both the public and private sectors to support decision-making, like planning community services (e.g., schools and emergency services) or determining consumer and market demand in all parts of the country."



---

## Does the Census count everyone?

- Only counts homeless people if in a shelter <!-- .element: class="fragment" data-fragment-index="1"  -->
- Incompletely enumerated reserves and settlements <!-- .element: class="fragment" data-fragment-index="2" -->


<https://www12.statcan.gc.ca/census-recensement/2021/ref/iers-repd-eng.cfm> <!-- .element: class="fragment" data-fragment-index="2" -->
 

Note: Depending on your area of research, it's important to know that even the short form questionnaire misses some people, even though it goes to 100% of households. Here are two examples: homeless people, for example, are only counted if they're stay in a shelter when the count happens. And there are also indigenous reserves and settlements that are counted only partially, if at all. The link on this slide is to a table showing these areas. Some are not counted because the indigenous band council did not give permission to enter its territory. In other cases access may not have been possible (e.g. forest fires) or safe from a health perspective (e.g. COVID 19) 


---

## Census Documentation

- Guides
- Dictionary
- Questionnaires

<br/>
<br/>

See [Reference Materials, 2021 Census](https://www12.statcan.gc.ca/census-recensement/2021/ref/index-eng.cfm)

---

## How Census data is released

- Aggregated data 
	- Published tables
	- Census profiles
- Public Use Microdata File (PUMF) <!-- .element: class="fragment" data-fragment-index="1" -->
	- Case-level data <!-- .element: class="fragment" data-fragment-index="1" -->
	- Some variables suppressed/aggregated<!-- .element: class="fragment" data-fragment-index="1" -->
	- Limited geographic detail<!-- .element: class="fragment" data-fragment-index="1" -->


Note: **Aggregated data**, also referred to as statistics, is data that someone has already done some grouping or calculations on. Examples from the Census could include the population count for each neighbourhood in vancouver, the average income for a region, and so on. If aggregated data is already avaialble for the topic that interests you, this is usually the most efficient route. However, for some research projects aggregated data might not be available... in those cases you might want to look for...

**Public Use Microdata Files**, or PUMFS, are files that provide one row for _each person_. Microdata is useful because it provides a lot of detail, allowing you to build your own tables or conduct your own analysis.

We'll focus on Aggregated data, but the 'resources' slide has links to Public Use Microdata.


---

<!-- .slide: style="font-size:0.8em" data-transition="slide-in fade-out" -->
## Census geographic levels

- Census division<!-- .element: class="fragment semi-fade-out" data-fragment-index="1" -->
- Census metropolitan area 
- Census subdivision
- Census tract
- Designated place<!-- .element: class="fragment semi-fade-out" data-fragment-index="1" -->
- Dissemination area
- Dissemination block<!-- .element: class="fragment semi-fade-out" data-fragment-index="1" -->

_<https://www150.statcan.gc.ca/n1/pub/92-195-x/92-195-x2021001-eng.htm>_ 

Note: This is a partial list of the geographic areas referred to on Statistics Canada Census pages and in other StatCan products. The source, linked at the bottom of the slide, includes descriptions of each of the areas. For this clas I'm going to illustrate four frequently used Census geograpies. (Highlight, read 4). We'll look at each of these using Greater Vancouver as our example.

None of these correspond exactly to what municipalities designate as neighbourhoods. You might need to group them during analysis and mapping to produce areas that more closely match neighbourhood boundaries.

---

<!-- .slide: data-transition="fade" -->
### Census metropolitan area (CMA)

![CMA example](./Images/2025-01-20_Census_Data/geog_CMA.png)


Note: This is the _Census Metropolitan Area_ - or CMA - of Vancouver. Many of the Public Use Microdata Files (PUMFs) only provide data at the CMA level. But in this class I understand you're interesed in variation _within_ the Vancouver CMA.

---

<!-- .slide: data-transition="fade" -->
### Census subdivision (CSD)

![CSD example](./Images/2025-01-20_Census_Data/geog_CSD.png)


Note: The Census subdivision breaks the area down into smaller chunks

---

<!-- .slide: data-transition="fade" -->
### Census tract (CT)

![CT example](./Images/2025-01-20_Census_Data/geog_CT.png) <!-- .element class="fragment semi-fade-out" data-fragment-index="1" -->
![CT example with detail](./Images/2025-01-20_Census_Data/geog_CT_inset.png) <!-- .element class="fragment" style="position: absolute; left: 200px" data-fragment-index="1" -->



Note: The Census tract breaks the area down into smaller chunks


---

<!-- .slide: data-transition="fade-in slide-out" -->
### Dissemination area (DA) 

![DA example](./Images/2025-01-20_Census_Data/geog_DA.png)


Note: The Dissemination area breaks the area down into smaller chunks. 


---

<!-- .slide:  style="font-size:smaller"-->

_Tour of Census Profiles on Statistics Canada website_  

<https://www12.statcan.gc.ca/census-recensement/2021/dp-pd/prof/index.cfm>

Note:
- Statcan page ->
- Census of population page (Census Data, Census Geography, Census Profile ->
- Census profile, search for Vancouver, choose CMA ->
- Show 'add a geography', show 'add/remove' as way to see scope
- Scroll down to 'age' section, 100% enumration
- Use 'add/remove' to show only 'Ethnocultural... -> Visible Minority'
	- show that it's only 25% (selected b/c included in lab file)
- Discuss download options
	- if table has the area you need, download 'as displayed intable'
	- if need data for many areas, click 'Comprehensive Download Files'
		- filter to 'census tract' but do not download
		- File is 2.5GB and more than 16M rows

---
<!-- .slide: data-transition="slide-in none-out" -->
#### Census profile download: **long** format

![Comprehensive download file](./Images/2025-01-20_Census_Data/profile_download.png)

---

<!-- .slide: data-transition="none-in slide-out" -->
#### Reformatted profile data: **wide** format

![Reformatted profile data](./Images/2025-01-20_Census_Data/reformatted_profile.png)

---

<!-- .slide:  style="font-size:smaller"-->

_Download Census 2021 Cargotraphic Boundary File (as shapefile)_

<https://www12.statcan.gc.ca/census-recensement/2021/geo/sip-pis/index-eng.cfm>

Note: 
- From Census main page, click "Census Geography"
- Click "Spatial information products"
- Scroll down, show "Reference", then click "Boundary files"
- Choose 2021, then select: 
	- Cartographic Boundary File
	- Statistical Boundaries -> Census Tracts
	- Format = Shapefile

---


<!-- .slide:  style="font-size:smaller"-->

_Tour of SimplyAnalytics (for map-ready data)_

<https://resources.library.ubc.ca/page.php?details=simplyanalytics&id=1044>

Note:
- Open project for Canada, Vancouver CMA ->
- Leave default variables ->
- Show drop-down menus at top, go to CT, Zoom in to show DA change ->
- Add variable by 'data folder' ->
- Choose Census ->
- Choose 'occupied private dwellings by tenure', show ownership percentage ->
- Add to map ->
- Export ranking table by DA

---

## DMTI Spatial

* Infrastructure
* Land use/landcover
* Vector contours
* Postal codes at the Forward Sortation Area level (six digit postal codes)
* <https://abacus.library.ubc.ca/dataverse/dmti>


Note:

* Not all of our resources are from governmental sources
* DMTI Spatial is a [reputable] private company which contains frequently requested geospatial data
* 400+ layers on over 20 different subjects

---

## Why use DMTI

* Easy
* Historical
* Broad coverage

Note:

* Ease of use; all data is from the same source
* Yearly updates, so it's possible to look for a *specific* year
* DMTI covers all of Canada, so if the area of interest falls outside of BC, it's still possible to get data
* All data is available in the form of shapefiles
* Some years have network data available (for routing)
    * all years *can* be made into a network data set
* Also contains census data in case you don't feel like downloading it from Statistics Canada

---

## Why *not* to use DMTI

* Data is *not* shareable
* Academic use only

Note:

* Unlike Statcan data, DMTI data is *not* public. This means:
    * A login is required to use it
    * Data can not be shared with others who do not also have access (ie, outside of UBC)
    * Academic use only
* For academic purposes, though, it's super useful

---

## Open Street Map

Can get many types of data quickly

* QGIS: [Quick OSM plugin](https://plugins.qgis.org/plugins/QuickOSM/)
* ArcGIS: [OSMQuery](https://github.com/riccardoklinger/OSMquery)

Note:

* Both of these allow importation of **selected** data from Open streetmap
* Key/Values: <https://wiki.openstreetmap.org/wiki/Map_features>

---

## Spatial Visualizations: Choropleth Maps

![choroplethmap](./Images/2025-01-20_Census_Data/choropleth1.jpeg)<!-- .element:  height="400"-->  
Tips on data classification, color ramps etc here: [Choropleth Maps by Uli Ingram](https://alg.manifoldapp.org/read/introduction-to-cartography/section/c3c06272-8b8b-49e7-a957-da0d06550b73#3-part-1)

Note: 

- Coloured or shaded area on a map represents relative rates or intensities across space
- Easy to create and interpret; great for showing data at a quick glance
- Data represented needs to be linked to an enumeration area and standardized as a rate or ratio
- Not appropriate for continuous data, or any data not representing an area (i.e. data assigned to a specific point)
- Need to use data classification scheme; 4-7 classes are preferred

---

## Spatial Visualizations: Graduated or Proportional Symbol Maps

<div class="r-stack">

<img src="./Images/2025-01-20_Census_Data/graduated_symbol.png" alt="graduatedsymbolmap" height="400"  class="fragment" data-fragment-index="1">

<img alt="proportionalsymbolmap" src="./Images/2025-01-20_Census_Data/proportional_symbol.png" height="400" class="fragment">
</div>

Read more: [ArcGIS Proportional Symbols Guide](https://pro.arcgis.com/en/pro-app/latest/help/mapping/layer-properties/proportional-symbology.htm)  
Read more: [ArcGIS Graduated Symbols Guide](https://pro.arcgis.com/en/pro-app/latest/help/mapping/layer-properties/graduated-symbols.htm)  


Note:

- Good alternative to choropleths for visualizing quantities and raw counts
- Good alternative to choropleths for visualizing quantities and raw counts
- Represent data through differently sized symbols
     - Graduated symbol uses data classes
     - Proportional does not use data classes; symbol proportional to corresponding data value
- Data used should be total values, percentage values or rate values and should occur at a point
- Not appropriate for density data, interval data or data with small ranges of value

- Represent data through differently sized symbols
     - Graduated symbol uses data classes
     - Proportional does not use data classes; symbol proportional to corresponding data value
- Data used should be total values, percentage values or rate values and should occur at a point
- Not apprporpriate for density data, interval data or data with small ranges of value

---

## Spatial Visualizations: Heat Maps


![heatmap](./Images/2025-01-20_Census_Data/heatmap.jpeg)<!-- .element: height="400"-->

Read more: [Dot Density Maps by Uli Ingram](https://alg.manifoldapp.org/read/introduction-to-cartography/section/c3c06272-8b8b-49e7-a957-da0d06550b73#3-part-1)

Note:

- Represents the density of data points across a geographic area through a continuous colour ramp
- Make it easy to understand overall trends in point data by highlighting areas of high or low density
- Good alternative to point maps where clusters might affect legibility; also does not use geographical boundaries to group data
- Good for overall trends rather than accurate numerical analysis

---

## Spatial Visualizations: Dot Density Maps


![dotdensity](./Images/2025-01-20_Census_Data/dot_density.png)<!-- .element: height="400"-->

Read More:[ArcGIS Dot Density Guide](https://pro.arcgis.com/en/pro-app/latest/help/mapping/layer-properties/dot-density.htm)

Note:

- Represents density of data points across a geographic area through randomly placed dots (vs. dot size in previous maps)
     - One-to-one dot density = one dot represents one object or count
     - One-to-many dot density = one dot stands for a number of things/values
- Data used should be total values; should be represented and aggregated to an enumeration area
- Good for displaying a variable's overall geographic pattern and density more accurately; can convey magnitude of more than one group
- Not great for retrieving rates or numbers from the map and may also lead readers to infer dot locations as precise locations of what's being mapped

---

<!-- .slide: data-background="lightblue" style="font-size: 0.7em;" -->
## Selected resources 

- [Census of Population](https://www12.statcan.gc.ca/census-recensement/index-eng.cfm) main page 
- [Census Profile](https://www12.statcan.gc.ca/census-recensement/2021/dp-pd/prof/index.cfm) 
- [Illustrated Glossary of Census Geography](https://www150.statcan.gc.ca/n1/pub/92-195-x/92-195-x2021001-eng.htm) 
- [Geographic Attribute File](https://www12.statcan.gc.ca/census-recensement/2021/geo/aip-pia/attribute-attribs/index-eng.cfm) 
- [SimplyAnalytics](https://resources.library.ubc.ca/page.php?details=simplyanalytics&id=1044) UBC login page 
- [2021 Census PUMF](https://hdl.handle.net/11272.1/AB2/1WTDOP) in Abacus 

\
\
Data analysis/GIS workstations in [Digital Scholarship Lab](https://researchcommons.library.ubc.ca/digital-scholarship-workstations/) or by [remote login](https://remotelabs.ubc.ca/#group-1028-data)
\
\
Alex Alisauskas, Humanities & Social Sciences Librarian [alexandra.alisauskas@ubc.ca](mailto:alexandra.alisauskas@ubc.ca)\
Jeremy Buhler, Data Librarian [jeremy.buhler@ubc.ca](mailto:jeremy.buhler@ubc.ca)\
Paul Lesack, Data/GIS Analyst [paul.lesack@ubc.ca](mailto:paul.lesack@ubc.ca)

