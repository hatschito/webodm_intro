# Introduction to WebODM and OpenDroneMap

### What is OpenDroneMap and what are it's capabilites?

* OpenDroneMap: An open source toolkit for aerial drone imagery.
* Alternative to propiertary photogrammetric software.

### Quality?

* Conference paper:

Vacca G. Overview of Open Source Software for Close Range Photogrammetry. ISPRS-International Archives of the Photogrammetry, Remote Sensing and Spatial Information Sciences. 2019 Aug;4214:239-45. [Available online at:https://www.int-arch-photogramm-remote-sens-spatial-inf-sci.net/XLII-4-W14/239/2019/]

  * Performance comparison of different photogrammetric software packages. Test object: Basilica of the Beata Vergine Assunta.

  * Found points on 111 images shot by Canon EOS M3 with a sensor CMOS
22.3x14.9 mm and a 24.2 Megapixel resolution

  | Software          | Matched points          |
  | ----------------- |:-----------------------:|
  | Agisoft Metashape |  114.453.295 points     |
  | WebODM            |    3.545.806 points     |



## Installation

### Prerequisites

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

### Install WebODM

```
git clone https://github.com/OpenDroneMap/WebODM --config core.autocrlf=input --depth 1
cd WebODM
./webodm.sh start

```

### Launch WebODM

```
1. Start container: ./webodm.sh start
2. Launch in browser: http://localhost:8000/dashboard/
3.Stop WebODM: ./webodm.sh stop

```



## Sample Data





## QGIS Photo Plugin: Import geotagged photos to qgis

Helpul plugin to explore drone imagery: The plugin creates a layer which will contain the name of the picture, its directory, the date and time taken, altitude, longitude, latitude, azimuth, north, camera maker an

https://plugins.qgis.org/plugins/ImportPhotos/

* Photo plugin
     * Exif tools is a prerequisite:

```
sudo apt-get install libimage-exiftool-perl perl-doc

```




## Generate products: Orthophoto  and Point Cloud

Orthophotos, Point Clouds, digital elevation models (DSM and DTM) and other products can be derived after uploading imagery. It' s a very easy to use drop down menu. 


![Userinterface](/media/administrator/Harald_SSD/projects_harald/Intro_Web_ODM/Manual/bilder/user_interface.png "User interface")

Start processing: Review -> start process




## Access commandline

* Get id of running docker container
```
sudo docker ps -aqf "name=containername"
```

* Access bash of the docker machine
```
docker exec -ti 5d402bd522f3 bash
 
```

## Installation on Server and inside Virtual machine

For your convencience WebODM was installed on a Virtualisation Server and can be used by you on request. The URL of the server is: http://141.89.192.147:8000/ The admin acount to enter the interface is:
admin, the password:btgTk4zf6Z4KbiX A user account can be accesd via: user / @webodm2019

* Server capacities:  
    * 24 Xeon E7 v2/Xeon E5 v2/Core i7 Bridge   
    * 


Further a virtual machine in the Ova2.0 (Open virtualisation) was generated; WebODM was installed insed OSGEOLive an Lubuntu based Live Linux distribution packed with GIS software. It can by using VirtualBox. Be aware, that you need enough diskspace (~40 GB). 


## Issues

Uploading to VM Server sometimes is "incomplete":https://community.opendronemap.org/t/upload-kind-of-complete-but-hangs-after-progress-bar/1352


## Further reading

* OpenDroneMap Manual: https://docs.opendronemap.org

