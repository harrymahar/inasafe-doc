==========================
Frequently Asked Questions
==========================

I found a bug, how should I report it?
--------------------------------------

We manage the project issues using a GitHub issue tracker. The
`InaSAFE <https://github.com/AIFDR/inasafe/issues?direction=desc&sort=created&state=open>`_
issue tracker is open to everyone, though you will first need to register a
(free) account on GitHub to use it. You can find the GitHub self-registration
page `here <https://github.com/signup/free>`_.

Do I need to pay to use |project_name|?
---------------------------------------

No, the software is completely Free and Open Source.

What license is |project_name| published under?
-----------------------------------------------

|project_name| is published under the GPL version 2 license, the full text of
which is available at
`www.gnu.org/licenses/gpl-2.0.txt <http://www.gnu.org/licenses/gpl-2.0.txt>`_.


Under the terms of the license of you may freely copy, share and modify the
software, as long as you make it available under the same license.

How is the project funded?
--------------------------

The project is being developed 'for the good of humanity' and has been
jointly developed by |BNPB|, AusAid & the `World Bank <http://www.worldbank.org/>`_.

Could we request a new feature?
-------------------------------

If you have a feature request, please use the
`issue tracker <https://github.com/AIFDR/inasafe/issues?direction=desc&sort=created&state=open>`_
to let us know about it, using the same procedure as for bug reporting.


How do I rename a shape file and all the helper files?
------------------------------------------------------

Use the rename command. rename [ -v ] [ -n ] [ -f ] perlexpr [ files ].
For example::

    rename -v "s/^building/OSM_building_polygons_20110905/" building.*

How do I reproject a spatial data file to WGS84 geographic coordinates
----------------------------------------------------------------------

For raster data, use gdalwarp, for example::

   gdalwarp -t_srs EPSG:4326 <source>.tif <target>.tif

For vector data use ogr2ogr. For example from TM-3 zone 48.2::

   ogr2ogr -s_srs EPSG:23834 -t_srs EPSG:4326 <target>.shp <source>.shp

How do I get Open Street Map building data into |project_name|?
---------------------------------------------------------------

For Indonesia, you can download latest collections at
`data.kompetisiosm.org <http://data.kompetisiosm.org>`_. or you can add our
Open Street Map building PostGIS mirror to |project_name|:

 * Add PostGIS layer with host=203.77.224.77, database=osm, username=aifdr,
   port 5432, SSL mode=disable
 * Select view named vw_planet_osm_polygon
 * Build query: upper(geometrytype("way")) IN ('POLYGON',
   'MULTIPOLYGON') AND BUILDING != ''

Another way, you can export osm data from HOT Exports:
 * Go to `Preset JOSM <http://josm.openstreetmap.de/wiki/Presets>`_.
 * Find and download `Building` preset created by Kate Chapman and save it
 * Go to HOT Exports website `www.hot-export.geofabrik.de
   <http://hot-export.geofabrik.de>`_.
 * Go to `New Job` menu in the upper right of the page
 * Select region, currently only 3 regions are supported by HOT Export (Haiti,
   Indonesia, Africa)
 * Fill `Job Name` and `Description`
 * Select area that you want to export by zooming or panning the map
 * You can choose smaller area by clicking `Select Smaller Area` and creating
   rectangle in the map or filling min/max longitude/latitude value for it
 * Click `Save` if your map is ready
 * Upload JOSM Preset File which have been downloaded before, and click `Save`
 * Your job is created and you have to wait until it finish. It'll take some
   minutes if your map is big one
 * When the job is finished, there will be a table contains files that can be
   downloaded
 * Download the `ESRI Shapefile (zipped)`
 * Extract it on your computer, and the data will be ready to use

How do I take screen capture e.g. for use in a presentation?
------------------------------------------------------------

On Ubuntu, get the packages gtk-recordmydesktop and mencoder
Record using recordmydesktop (start and stop icon in the top bar)
Convert to other formats using mencoder, e.g::

   mencoder -idx yogya_analysis-6.ogv -ovc lavc -oac lavc -lavcopts \
   vcodec=mpeg4:vpass=1 -of lavf -o yogya_analysis.avi

or::

   mencoder -idx yogya_analysis-6.ogv -ovc lavc -oac lavc -lavcopts \
   vcodec=wmv2 -of lavf -o yogya_analysis.wmv

How do I convert a vector hazard layer to a raster layer?
---------------------------------------------------------

For vector to raster conversion, use gdal_rasterize utility, for example::

   gdal_rasterize -a <attribute_name> -l <source>.shp <destination>.tif


Why does the plugin not show up in my QGIS Plugin Manager?
----------------------------------------------------------

One common issue is that if you upgraded from QGIS 1.7.x to 1.8 you may not
get the new plugin repo added to your repo list. To fix this you can do:

* open QGIS
* Go :menuselection:`Plugins --> Fetch Python Plugins`
* Click :guilabel:`Repositories` tab
* Click :guilabel:`add`
* :guilabel:`Name`: Official QGIS Repository
* :guilabel:`Url`: http://plugins.qgis.org/plugins/plugins.xml
* Save it and the plugin repo list should update. If it doesn't,
  close and open QGIS to force an update.
* In the python plugin manager main tab now you should find |project_name|
  available

How do I fix KeywordDbError on Windows?
---------------------------------------

It’s an issue related to permission issue. Normally, it occurs when
the keyword.db is not writable by current user. The thing that you have to do
is re-run QGIS as administrator or re-install QGIS as administrator.

Another way to solve it is deleting the registry of InaSAFE. You can do it
by opening :guilabel:`regedit` (Registry Editor). To open regedit, you need 
to search it in :guilabel:`Start Menu` (it is usually not shown in Start 
Menu). Open regedit. Find inasafe registry under :menuselection:`My Computer 
--> Software --> QuantumGIS --> QGIS --> PythonPlugins`. After that, 
right click on the inasafe, and click :guilabel:`Delete`. Restart QGIS and 
try to run InaSAFE again to see if it works.

Please see `InaSAFE issue #459 <https://github.com/AIFDR/inasafe/issues/459>`_
, `InaSAFE issue #564 <https://github.com/AIFDR/inasafe/issues/564>`_, and 
`InaSAFE issue #569 <https://github.com/AIFDR/inasafe/issues/569>`_ for
further information.
