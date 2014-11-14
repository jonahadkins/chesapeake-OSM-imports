#Chesapeake, Virginia OSM Buildings Import
###From ArcGIS Open Data To OpenStreetMap  

Source Data Downloaded From City of Chesapeake [Open Data Portal](http://public.chesva.opendata.arcgis.com/)
The City of Chesapeake recently [`turned on`](https://opendata.arcgis.com/about) open data for their ArcGIS Online instance. This presented a great opportunity to import building footprints and addresses into OSM.

###Pre-Processing  
After an initial download and inspection of the data I engaged with the city's [GIS Team](gisteam@cityofchesapeake.net ) to make them aware of the import plans, as well as, get answers for questions on the data/attributes. The team was very helpful in offering suggestions and answering all my questions.

* Building Footprints (108,822 Records)
  * Existing Building Classification Codes
    * 1 - General/Residential
    * 2 - Government
    * 3 - Medical
    * 4 - Education
    * 5 - Transportation
    * 6 - Commercial
    * 7 - Religious
    * 8 - Recreation
    * 9 - Cultural/Heritage
    * 10 - Hospitality
    * 11 - Airport
    * 12 - Industrial
    * 13 - CommunityCenter
    * 14 - Apartment
  * Building Name (Common or Business Name)
  * Main Street Address
   * ~~Original Plan -> (Joined From Address Points on 'map_parcel' where status = 'true')~~
   * ~~Ches. GIS Office Suggestion -> (Joined From Parcels on 'map_parcel')~~
   * Ran Summary Stats on buildings for `max('area')` and grouped by `'map_parcel'` ; This essentially isolated properties with only one building (40,145) and the largest building for parcels with multiple buildings (26,936), for residential buildings it selected the house only (assuming the house was the largest structure). These structures were given a `addr=1` coding.
   * Resulting file was joined to address points layer `on 'addr'=1` and parsed address information was added to buildings file.
   * Calculated Building types over to OSM Tag methodology
   * Created polygons for splitting features in to smaller areas; `total sections = 35`

Final building file attributes included:
* addr:housenumber
* addr:street (`prefix` + `name` + `type` + `suffix`)
* addr: city
* addr: state
* addr: postcode
* name
* comments: (`map_parcel` - city parcel id)
* unit: (address unit number/letter)

### Upload / Import To OSM  
Building footprint section were uploaded using JOSM with attributes mapped to the OSM Tag convention. Import process was completed over a [1 week period](https://github.com/jonahadkins/chesapeake-OSM-imports/blob/master/upload%20schedule.md)

#ToDo  
Import secondary address points (apts, duplex, shopping center, etc.) 
* Total Address Points (99,058 Records)
  

Yeah Open Data!
