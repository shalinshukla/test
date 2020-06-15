INTRODUCTION
------------

Server-side clustering for mapping.

By clustering data on the server-side, the load is shifted from the client
to the server which allowsdisplaying larger amounts of data in a performant way.

REQUIREMENTS
------------

* geofield (includes geophp) to store coordinates on my node


RECOMMENDED MODULES
-------------------

- views_geojson to return my view results in geojson format
- leaflet_geojson to have a block to integrate my view returned by geoJson
  & apply the bounding box strategy
- page_manager (includes panels & ctools)
  to associate my block & the leaflet map
- leaflet, to provide the map
- leaflet_views, to be able to use LeafletAjaxPopupController 
  to render the popup through ajax

INSTALLATION
------------

* Install Geocluster
* Update existing content (to generate geohashed for geo fields)
* Re-save any previously created content using node_save
  so that the Geocluster index is updated.
  
CONFIGURATION
------------

Cf https://www.drupal.org/project/geocluster/issues/2578537#comment-13314147
* Create a clustered GeoJSON Feed:
 - Create a display based on Views GeoJSON
 - Add the Geofield and exlude it from display
 - Enable Geocluster in the Format Settings of your View
 - Add Geocluster fields for aggregates of latitude, longitude, count
 - Use Geocluster lat, lon as data source in the Views GeoJSON format settings
 - Make sure that no additional fields are used for aggregation, 
  you can still use them with aggregate functions like GROUP_CONCAT
 - Make sure there isn't any sorting
 - You maybe want to save this step until everything else works: 
  set the item limit to 0 so that all your content will get clustered
  
* Create a page and display this view as the source of your block
