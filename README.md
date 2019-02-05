GPS2MapUrl.config
=================

<!-- toc -->

- [Install](#install)
- [Tag definitions](#tag-definitions)
  * [GoogleMapsUrl](#googlemapsurl)
  * [BingMapsUrl](#bingmapsurl)
  * [OpenStreetMapsUrl](#openstreetmapsurl)
  * [MapquestMapsUrl](#mapquestmapsurl)
  * [YandexMapsUrl](#yandexmapsurl)
- [User Parameters](#user-parameters)
  * [Zoom](#zoom)
- [Notes](#notes)
- [Revisions](#revisions)
- [References:](#references)

<!-- tocstop -->

GPS2MapUrl.config is a user-defined config file for [exiftool](https://www.sno.phy.queensu.ca/~phil/exiftool/).  It creates composite tag definitions to create URLs for various map websites based upon GPS coordinates embedded in the file.

## Install

Place this file in the same directory as exiftool.exe and start the command with `-config GPS2MapUrl.config` (requires exiftool v 10.70 or greater) or include the full path (relative or absolute) if saved elsewhere.  Optionally, tags can be copied from this file (marked by the dash lines) and placed in the `.exifTool_config` file under the `'Image::ExifTool::Composite' => {` line to have these tags available at all times. 

## Tag definitions

### GoogleMapsUrl

This will create a link to Google maps based upon this StackOverflow answer 

https://stackoverflow.com/a/32807681/3525475

Example:

`exiftool -config Map_URL_From_GPS.config -GoogleMapsUrl FILE`

### BingMapsUrl

This will create a link to Bing maps based upon this page

https://docs.microsoft.com/en-us/bingmaps/articles/create-a-custom-map-url

Example:

`exiftool -config Map_URL_From_GPS.config -BingMapsUrl FILE`

###	OpenStreetMapsUrl
This will create a link to OpenStreetMap.org maps 

Example:

`exiftool -config Map_URL_From_GPS.config -BingMapsUrl FILE`

### MapquestMapsUrl

This will create a link to Mapquest maps 

Example:

`exiftool -config Map_URL_From_GPS.config -BingMapsUrl FILE`

###	YandexMapsUrl
This will create a link to Yandex maps 

Example:

`exiftool -config Map_URL_From_GPS.config -BingMapsUrl FILE`

## User Parameters

### Zoom

This user parameter will add the level of zoom for the URL using the exiftool [-userparam](https://sno.phy.queensu.ca/~phil/exiftool/exiftool_pod.html#userParam-PARAM-VAL) option.  There is no check to verify that the parameter passed is a viable value for the zoom.  The zoom value for most of these websites seems to be a number from 1 to 16-20, depending upon the site.

Example:

`exiftool -config Map_URL_From_GPS.config -userparam Zoom=16 -BingMapsUrl FILE`

## Notes

- Bing Maps doesn't allow for the creation of push pins without an API key.  This tag will use the collection `sp=point` option using a dot as the label.

## Revisions

- Ver. 1.0 - 2019-02-04 - Bryan K. Williams (aka StarGeek) Created

## References:

http://u88.n24.queensu.ca/exiftool/forum/index.php/topic,9862.0.html

