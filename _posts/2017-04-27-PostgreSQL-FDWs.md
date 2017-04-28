---
category: Data Analysis
---
# Setting Up Foreign Data Wrappers (FDWs) in PostgreSQL
This is a basic tutorial for connecting external data to your PostgreSQL database through what is called a "foreign data wrapper." 
At the time of this writing, the only FDW that comes prepacked with PostgreSQL includes fdw_file, used to query files on your computer. 
In this example, I am going to pull one from a wiki [catalog](http://wiki.postgresql.org/wiki/Foreign_data_wrappers) of third-party wrappers.

## Step 1: Install the OGR FDW
I already have the spatially-oriented fdw wrapper "ogr_fdw" installed as part of 
the [PostGIS Bundle 2.3 for PostgreSQL x64 9.6](http://postgis.net/windows_downloads/),
using the StackBuilder Application Installer. If not done so already, you will need to make
sure to install the extensions:
```
CREATE EXTENSION postgis;
CREATE EXTENSION ogr_fdw;
```

## Step 2: Install the Foreign Data Server and Setup a Foreign Data Table
In this case I wanted to query the BSS Pavement Quality Index, which is listed on the GeoHub Portal [here](http://geohub.lacity.org/datasets/2d945910272548a6ae0b57126000669a_0?geometry=-121.027%2C33.679%2C-115.8%2C34.362&uiTab=table).
```
CREATE SERVER bss_pci
  FOREIGN DATA WRAPPER ogr_fdw
  OPTIONS (
    datasource 'http://geohub.lacity.org/datasets/2d945910272548a6ae0b57126000669a_0.geojson',
    format 'GeoJSON' );
```
After creating the foreign data server, I needed to create a foreign table. The ogr_fdw has a nifty feature for PostgreSQL 9.5+ users; 
you can do automatic foreign table creation, which you can read more about [here](https://github.com/pramsey/pgsql-ogr-fdw).
```
CREATE SCHEMA fgdball;

IMPORT FOREIGN SCHEMA ogr_all 
	FROM SERVER bss_pci 
    INTO fgdball;
```
Unfortunately, when I ran this query I ran into the following error:
```
ERROR:  column "fid" specified more than once
CONTEXT:  importing foreign table "ogrgeojson"
********** Error **********

ERROR: column "fid" specified more than once
SQL state: 42701
Context: importing foreign table "ogrgeojson"
```
And so I am still here troubleshooting...see recent changes; try setting layer name to default name of 'OGRGeoJSON,' based on [this](http://www.gdal.org/drv_geojson.html).

