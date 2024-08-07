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

`exiftool -config GPS2MapUrl.config -GoogleMapsUrl FILE`

### BingMapsUrl

This will create a link to Bing maps based upon this page

https://docs.microsoft.com/en-us/bingmaps/articles/create-a-custom-map-url

Example:

`exiftool -config GPS2MapUrl.config -BingMapsUrl FILE`

### OpenStreetMapsUrl
This will create a link to OpenStreetMap.org maps 

Example:

`exiftool -config GPS2MapUrl.config -OpenStreetMapsUrl FILE`

### MapquestMapsUrl

This will create a link to Mapquest maps 

Example:

`exiftool -config GPS2MapUrl.config -MapquestMapsUrl FILE`

### YandexMapsUrl
This will create a link to Yandex maps 

Example:

`exiftool -config GPS2MapUrl.config -YandexMapsUrl FILE`

## User Parameters

### Zoom

This user parameter will add the level of zoom for the URL using the exiftool [-userparam](https://sno.phy.queensu.ca/~phil/exiftool/exiftool_pod.html#userParam-PARAM-VAL) option.  There is no check to verify that the parameter passed is a viable value for the zoom.  The zoom value for most of these websites seems to be a number from 1 to 16-20, depending upon the site.

Example:

`exiftool -config GPS2MapUrl.config -userparam Zoom=16 -BingMapsUrl FILE`

## Notes

- Bing Maps doesn't allow for the creation of push pins without an API key.
- Requires exiftool version to be before 11.54 or later than 11.57

## Revisions

- Ver. 1.0 - 2019-02-04 - Bryan K. Williams (aka StarGeek) Created
- Ver. 1.1 - 2019-07-25 - Changed undef to empty string, fixed examples
- Ver. 1.2 - 2024-08-03 - Fixed MapQuest URL, note that MapQuest seems to have problems with some GPS Coordinates. For example, coordinates 40.6892, -74.0445 will not be found in MapQuest. Disabled Zoom in MapQuest as it no longer works. Removed "sp=point" from the Bing URL as it is ignored, Added default level 16 for Bing because without it Bing's default level of zoom shows to wide of an area

## References:

https://exiftool.org/forum/index.php?msg=51226

