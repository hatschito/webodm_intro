# Introduction to WebODM and OpenDroneMap (ODM): A few notes

These notes are part of a short introduction to WebODM. The motivation behind this introducion is to show, that an alternative to Agissoft Metashape or Pix4D exists. 

## What is OpenDroneMap and what are it's capabilites?

* OpenDroneMap: An open source toolkit for aerial drone imagery.
* Alternative to propiertary photogrammetric software, able to generate Orthophotos, Point Clouds, digital elevation models (DSM and DTM) and other products….
 * Uses the  Scale invariant local features algorithm (SIFT) :https://www.youtube.com/watch?v=oKAnOzIu66c&t=31s
Nice explanation from udemy
* WebODM: A web based interface for OpenDroneMap 
* ODM developers started to include MICMAC, *the holy grail?*:
https://www.opendronemap.org/2019/05/nodemicmac-a-new-webodm-node/


## Quality?

*There are not that much studys out there*

* Conference paper:

Vacca G. Overview of Open Source Software for Close Range Photogrammetry. ISPRS-International Archives of the Photogrammetry, Remote Sensing and Spatial Information Sciences. 2019 Aug;4214:239-45. [Available online at:https://www.int-arch-photogramm-remote-sens-spatial-inf-sci.net/XLII-4-W14/239/2019/]

  * Performance comparison of different photogrammetric software packages. Test object: Basilica of the Beata Vergine Assunta.

  * Found points on 111 images shot by Canon EOS M3 with a sensor CMOS 22.3x14.9 mm and a 24.2 Megapixel resolution

  | Software          | Matched points          |
  | ----------------- |:-----------------------:|
  | Agisoft Metashape |  114.453.295 points     |
  | WebODM            |    3.545.806 points     |


* Further paper: Burdziakowski, P. (2017). Evaluation of open drone map toolkit for geodetic grade aerial drone mapping–case study.

## Installation

Ways to install ODM:
* Docker (Windows, MacOS, Linux)
* Natively using Ubuntu 16.04 or later (or with Virtual Machine e.g. vagrant)
* Windows WebODM installer is sold
 https://WebODM.org

### Prerequisites to install WebODM on Ubuntu 18.04

* Docker and GIT

### Install Docker on Ubuntu 18.04

```
#Install Docker
sudo apt-get update 
sudo apt-get upgrade
sudo apt install docker.io
#Start and Enable Docker
sudo systemctl start docker
sudo systemctl enable docker

#In some cases docker has to be updated after installation to avoid backport errors
sudo pip install --upgrade docker

```

### Enable non root users to use docker

```
sudo groupadd docker
sudo gpasswd -a student docker
#activate the changes
sudo newgrp docker
```


### Install WebODM

```
git clone https://github.com/OpenDroneMap/WebODM --config core.autocrlf=input --depth 1
cd WebODM
./webodm.sh start
```


### Installations for the introduction

#### Virtual machine

Further a virtual machine in the Ova2.0 (Open virtualisation) was generated; WebODM was installed insed OSGEOLive an Lubuntu based Live Linux distribution packed with GIS software. It can by using VirtualBox. Be aware, that you need enough diskspace (~40 GB). 
*Docker inside a virtual machine, does this make sense?*

OSGEOLive: https://live.osgeo.org/en/index.html

#### Server based installation

For your convencience WebODM was installed on a virtualisation server and can be used by you on request. The URL of the server is: http://141.89.192.147:8000/ The admin acount to enter the interface is:
admin, the password:xxxxxx A user account can be accesd via: user / xxxxxx 

* Server capacities:  
    * Processor: 24 Xeon E7 v2/Xeon E5 v2/Core i7 Bridge
    * RAM: 128 GB

* Issues with the server installation:

Uploading to VM Server sometimes is "incomplete":https://community.opendronemap.org/t/upload-kind-of-complete-but-hangs-after-progress-bar/1352

## Launch WebODM


```
1. Start container: ./webodm.sh start
2. Launch in browser: http://localhost:8000/dashboard/
3.Stop WebODM: ./webodm.sh stop

```

## Sample Data

Examples to play around with WebODM
https://github.com/OpenDroneMap/ODMdata

In the intro this dataset is used:

Geopark Kielce-Centrum Geoedukacji: https://github.com/merkato/odm_wietrznia

### Explore the sample data: QGIS Photo Plugin: 

The QGIS Photo Plugin is a plugin to import geotagged photos to QGIS. It's a helpul plugin to explore drone imagery: The plugin creates a layer which will contain the name of the picture, its directory, the date and time taken, altitude, longitude, latitude, azimuth, north, camera maker. 

https://plugins.qgis.org/plugins/ImportPhotos/

* Photo plugin
     * Exif tools is a prerequisite and can be installed via

```
sudo apt-get install libimage-exiftool-perl perl-doc

```

## Generate products:

Orthophotos, Point Clouds, digital elevation models (DSM and DTM) and other products can be derived after uploading imagery. It' s a very easy to use drop down menu. 
The process simply can be started with: *Start processing: Review -> start process*


## Go further I: Access the docker container and it's commandline

* Get id of running docker container
```
sudo docker ps -aqf "name=containername"
```

* Access bash of the docker machine
```
docker exec -ti 5d402bd522f3 bash
 
```

*But I did not manage to run ODM commands within the container*

## Go further II: Install ODM docker



### Include Gcps
Gcps can be used as text file as followed: 

* coordinate system descriptionx1 y1 z1 pixelx1 pixely1 imagename1x2 y2 z2 pixelx2 pixely2 imagename2x3 y3 z3 pixelx3 pixely3 imagename3

* WGS84 UTM 10N544256.7 5320919.9 5 3044 2622 IMG_0525.jpg544157.7 5320899.2 5 4193 1552 IMG_0585.jpg544033.4 5320876.0 5 1606 2763 IMG_0690



## Further reading
* OpenDroneMap Manual: https://docs.opendronemap.org


