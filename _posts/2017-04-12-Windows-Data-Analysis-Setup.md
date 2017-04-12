---
category: Data Analysis
---
# Setting Up My Windows Machine for Data Analysis
This is my recording of the steps I've taken to setup my machine for the data analysis I've done here at the City. Theses instructions would be most useful to those working with spatial databases, especially if an ESRI product is installed. I am configuring my installations of PostgreSQL, ArcGIS for Desktop, and Python.

## Step 1: Assess Current Python Installation
Currently have: ArcGIS for Desktop, Python 2.7
Setting Up: PostgreSQL, Python 3

If, like me, you are running ArcGIS for Desktop (10.4.1 in my case), you will already have the 32-bit version of python 2.7 installed here:
```
C:\Python27\ArcGIS10.4\python.exe
```

## Step 2: Install PostgreSQL and PostGIS Extension
I used the interactive installer provided through EnterpriseDB and recommended on the [PostgreSQL website,](https://www.postgresql.org/download/windows/) using StackBuilder to easily add the PostGIS extension. Devan Morris over at SF Public Health has some great [screenshots](https://github.com/devmorris/transbasesf) to guide you through the installation process.

## Step 3: Install Python 3 if needed
One of the functionalities that I needed to enable includes the Pl/Python language so that I can run python scripts within the PostgreSQL database. Unfortunately, based on information [here](http://stackoverflow.com/questions/24216627/how-to-install-pl-python-on-postgresql-9-3-x64-windows-7), it looks like the Windows builds no longer contain support for plpython2 (for Python 2.7), only plpython3 (for Python 3.X). 

Therefore, to be able to use python within PostgreSQL, make sure to install Python 3. When deciding between the 32 or 64 bit installation, check with your PostgreSQL install to make you match (in my case, I installed the 64-bit version) and then install from the [python website](https://www.python.org/downloads/windows/).

However, the trickiest part of this installation is that you will need to install a specific version of python, which I found out via this [answer.](http://stackoverflow.com/questions/21001890/installing-plpythonu-on-windows) In my case, using the dependency walker on plpython3.dll (found in C:\Program Files\PostgreSQL\9.6\lib) showed that plpython3.dll was looking for python33.dll. I therefore installed the latest version of [Python 3.5](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64.msi) on my machine and updated the path variable. Once this was complete, I was able to go into PgAdmin4, open up my database, right-click "Languages," then "Create Language" and then select plpython3u and it worked perfectly.
