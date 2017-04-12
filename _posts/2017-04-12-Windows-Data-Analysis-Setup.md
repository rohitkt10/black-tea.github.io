---
category: Data Analysis
---
# Setting Up My Windows Machine for Data Analysis
This is my recording of the steps I've taken to setup my machine for the data analysis I've done here at the City. Theses instructions would be most useful to those working with spatial databases, especially if an ESRI product is installed. I am configuring my installations of PostgreSQL, ArcGIS for Desktop, and Python.

## Step 1: Figure out what you have
Currently have: ArcGIS for Desktop, Python 2.7
Setting Up: PostgreSQL, Python 3

If, like me, you are running ArcGIS for Desktop (10.4.1 in my case), you will already have the 32-bit version of python 2.7 installed here:
```
C:\Python27\ArcGIS10.4\python.exe
```

## Step 2: Install PostgreSQL and PostGIS Extension
I used the interactive installer provided through EnterpriseDB and recommended on the [PostgreSQL website,](https://www.postgresql.org/download/windows/) using StackBuilder to easily add the PostGIS extension. One
of the unfortunate things I realized 
