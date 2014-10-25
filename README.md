#Chesapeake OSM Import
###Repository for getting the City of Chesapeake's GIS layers imported to OpenStreetMap  
=====================

Source Data Downloaded From City of Chesapeake [Open Data Portal](http://public.chesva.opendata.arcgis.com/)

* Building Footprints (108,822 Records)
  * Building Classification (House, Apartment, Commercial, Industrial)
  * Building Name (Common or Business Name)
  * Main Street Address (Joined From Address Points on 'map_parcel' where status = 'true')
    * Addr: Postcode, City, House Number, Street Name

* Address Points (99,058 Records)
  * All Other Addresses (status = 'multi';'corner')
  * Addr: Postcode, City, House Number, Street Name

Yeah Open Data!
