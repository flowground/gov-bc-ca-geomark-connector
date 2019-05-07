# ![LOGO](logo.png) GeoMark Web Service **flow**ground Connector

## Description

A generated **flow**ground connector for the GeoMark Web Service API (version 4.1.2).

Generated from: https://api.apis.guru/v2/specs/gov.bc.ca/geomark/4.1.2/openapi.json<br/>
Generated at: 2019-05-07T17:42:11+03:00

## API Description

The Geomark Web Service allows you to create and share geographic areas of interest over the web in a variety of formats and coordinate systems. This service is especially helpful when you need to share an area of interest with people who require that the data be in a different format, or they use different mapping software. 

Please note that you may experience issues when submitting requests to the delivery or test environment if using this [OpenAPI specification](https://github.com/bcgov/api-specs) in other API console viewers.

## Authorization

This API does not require authorization.

## Actions

### Create a new geomark by copying the geometries from one or more existing geomarks from the current server.

> The source geomarks can be specified by with the geomarkUrl parameter.  Repeat the parameter if sourcing from multiple geomarks

*Tags:* `create`

#### Input Parameters
* `geomarkUrl` - _required_ - One or more geomark URLs or identifiers to create the new geomark from.
* `resultFormat` - _optional_ - The file format the geomark info resource should be returned using.
    Possible values: json, xml, kml, kmz, shp, shpz, geojson, gml, wkt.
* `allowOverlap` - _optional_ - Select this option to allow overlapping geometries
    Possible values: false, true.
* `callback` - _optional_ - The callback function a JSON result format would be wrapped in to support Ajax requests.
* `redirectUrl` - _optional_ - The optional external URL to redirect the user to when the geomark is created rather than showing the geomark info page. The geomarkId and geomarkUrl query string parameters will be added to the redirectUrl so that the target application gets a reference to the geomark.
* `failureRedirectUrl` - _optional_ - The url to redirect if the geomark could not be created. The URL will include a <fieldName>_Error parameter with the error message for the field that caused the error.
* `bufferMetres` - _optional_ - The amount to buffer the geometry in metres, must only contain numerical digits (e.g 10). Leave blank and no buffer will be added to input geometries. If blank then any Point, LineString, MultiPoint and MultiLineString geometries will be ignored.
* `bufferJoin` - _optional_ - If bufferMetres is specified, The style of buffer to use for joins between the line segments for lines and polygons.
    Possible values: ROUND, MITRE, BEVEL.
* `bufferCap` - _optional_ - If bufferMetres is specified, The style of buffer to use at the ends of a buffered line.
    Possible values: ROUND, SQUARE, FLAT.
* `bufferMitreLimit` - _optional_ - If bufferMetres is specified, the maximum ratio of distance from the original geometry to a mitre buffer point and the buffer amount. If the ratio is greater than this a bevel will be used instead. This prevents infinite distances when the angle between the two lines at a join is small. Must be > 0.
* `bufferSegments` - _optional_ - If bufferMetres is specified, the number of line segments used in each quadrant to approximate the curve for round end-cap and join styles. Must be > 0.

### Create a new geomark

> Create a new geomark from the geometries read from the 'body' parameter or file.

*Tags:* `create`

### Get information about a particular geomark

> The attribution can be downloaded as a info file format. The download files can then be processed by a client application to access the geomark info fields and to get the URLs to the geometry download resources.

*Tags:* `info`

#### Input Parameters
* `geomarkId` - _required_ - The unique identifier for the geomark.
* `fileFormatExtension` - _required_ - The file format name extension used to represent the geomark download.
    Possible values: json, xml, kml, kmz, shp, shpz, geojson, gml, wkt.
* `srid` - _optional_ - The srid of the coordinate system the geometry should be converted to.
    Possible values: 4326, 3005, 3857, 26907, 26908, 26909, 26910, 26911.

### Gets the bounding box of the geomark

> The source geomarks can be specified by with the geomarkUrl parameter.  Repeat the parameter if sourcing from multiple geomarks

*Tags:* `boundingBox`

#### Input Parameters
* `geomarkId` - _required_ - The unique identifier for the geomark
* `fileFormatExtension` - _required_ - The file format name extension used to represent the geomark download.
    Possible values: json, xml, kml, kmz, shp, shpz, geojson, gml, wkt.
* `srid` - _optional_ - The srid of the coordinate system the geometry should be converted to.
    Possible values: 4326, 3005, 3857, 26907, 26908, 26909, 26910, 26911.

### Get the feature and attribution of the geomark

> The geomark feature resource returns a single spatial feature with either a single (Point, LineString, Polygon) or multi-part geometry (MultiPoint, MultiLineString, MultiPolygon) and the geomark attribution.  The geometry and attribution can be downloaded as a spatial download file format in a supported coordinate system. The download files can then be used in a desktop GIS application (e.g. ArcMap), Google Earth or a web mapping application.

*Tags:* `feature`

#### Input Parameters
* `geomarkId` - _required_ - The unique identifier for the geomark
* `fileFormatExtension` - _required_ - The file format name extension used to represent the geomark download.
    Possible values: json, xml, kml, kmz, shp, shpz, geojson, gml, wkt.
* `srid` - _optional_ - The srid of the coordinate system the geometry should be converted to.
    Possible values: 4326, 3005, 3857, 26907, 26908, 26909, 26910, 26911.

### Get the individual geometries within a multi-part geometry

> The geomark parts resource returns a one or more spatial features. One for each part of the Geomark's geomerty. Each part contains a single (Point, LineString, Polygon) geometry and the geomark attribution.

*Tags:* `parts`

#### Input Parameters
* `geomarkId` - _required_ - The unique identifier for the geomark
* `fileFormatExtension` - _required_ - The file format name extension used to represent the geomark download.
    Possible values: json, xml, kml, kmz, shp, shpz, geojson, gml, wkt.
* `srid` - _optional_ - The srid of the coordinate system the geometry should be converted to.
    Possible values: 4326, 3005, 3857, 26907, 26908, 26909, 26910, 26911.

### Gets a single spatial point representative of the geomark.

> The geomark point resource returns a single spatial feature with a single Point and the geomark attribution.  The point geometry will be created from the first geometry part of the Geomark. Point geomarks will return the first Point part in the geomark.  LineString geomarks will return the first coordinate of the first LineString part in the geomark. Polygon geomarks will return the centroid or another point inside the first Polygon part in the geomark. The geometry and attribution can be downloaded as a spatial download file format in a supported coordinate system. The download files can then be used in a desktop GIS application (e.g. ArcMap), Google Earth or a web mapping application.

*Tags:* `point`

#### Input Parameters
* `geomarkId` - _required_ - The unique identifier for the geomark.
* `fileFormatExtension` - _required_ - The file format name extension used to represent the geomark download.
    Possible values: json, xml, kml, kmz, shp, shpz, geojson, gml, wkt.
* `srid` - _optional_ - The srid of the coordinate system the geometry should be converted to.
    Possible values: 4326, 3005, 3857, 26907, 26908, 26909, 26910, 26911.

## License

**flow**ground :- Telekom iPaaS / gov-bc-ca-geomark-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
