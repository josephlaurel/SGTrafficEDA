# Analyzing the Impact of COVID-19 on Singapore Traffic using Computer Vision

## Overview
* Performed time series analysis to compare Singapore highway traffic in January 2019 vs. January 2020
* Scraped 60,174 downtown traffic images with time and geolocation data from the [Government of Singapore's API](https://data.gov.sg/dataset/traffic-images)
* Detected the number of cars in images using OpenCV and revealed that traffic volume was largely unchanged vs. the previous year

## Code and Resources Used
<b> Python Version: </b> 3.7 <br>
<b> Packages: </b> requests, pandas, geopandas, libproj-dev proj-data proj-bin, libgeos-dev, cython, cartopy, geoplot, matplotlib, geoplot, json, contextily, datetime, time, concurrent, os, io, PIL, cv2, cvlib, seaborn <br>
<b> Data used for Mapping Areas of Singapore: </b> [Master Plan 2014 Subzone Boundary (No Sea)](https://data.gov.sg/dataset/master-plan-2014-subzone-boundary-no-sea) <br>
<b> Guide to OpenCV Set-Up: </b> ["How to use OpenCV with GPU on Colab?" by C Kuan](https://towardsdatascience.com/how-to-use-opencv-with-gpu-on-colab-25594379945f)

## Data Collection
<p align='justify'> API requests returned metadata on 89,282 images captured once per minute by 323 traffic cameras across Singapore in January 2019 and January 2020. Downtown traffic was used as a proxy for overall traffic throughout Singapore. Hence, the analysis focused on images captured by camera 1709 located in the downtown area. The dataset includes 30,234 images from January 2019 and 29,940 images from January 2020. <br><br> The following features were obtained:</p>

* <b> timestamp: </b> The date and time that the image was captured, written in W3C format
* <b> image: </b> The url containing the traffic image
* <b> camera_id: </b> The four-digit identifier of the camera that captured the image
* <b> location.latitude: </b> The latitude coordinate value of the camera that captured the image
* <b> location.longitude: </b> The longitude coordinate value of the camera that captured the image
* <b> image_metadata.height: </b> The height of the traffic image, measured in pixels
* <b> image_metadata.width: </b> The width of the traffic image, measured in pixels
* <b> image_metadata.md5: </b> The metadata of the image stored in MD5 format
* <b> num_cars </b> (engineered feature): The number of cars in the image as detected using the cv2 package

## Key Findings
![Monthly Traffic](Graphs/monthly%traffic.png)
