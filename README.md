#Chesapeake OSM Import
###Repository for getting the City of Chesapeake's GIS layers imported to OpenStreetMap  

Source Data Downloaded From City of Chesapeake [Open Data Portal](http://public.chesva.opendata.arcgis.com/)

* Building Footprints (108,822 Records)
  * Building Classification Codes
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

* Address Points (99,058 Records)
  * All Other Addresses (status = 'true','multi';'corner')
  * Add Attributes: Postcode, City, House Number, Street Name

Yeah Open Data!
