# A Comparison of Singapore Highway Traffic in January 2019 and 2020 using Computer Vision Object Detection

## Overview
* Performed exploratory data analysis to compare Singapore highway traffic at the start of the COVID-19 outbreak vs. the previous year
* Scraped 60,211 downtown traffic images with time and geolocation data from the [Government of Singapore's API](https://data.gov.sg/dataset/traffic-images)
* Detected the number of cars in images using computer vision and revealed that traffic volume was largely unchanged vs. the previous year

## Code and Resources Used
<b> Python Version: </b> 3.7 <br>
<b> Packages: </b> requests, pandas, geopandas, matplotlib, geoplot, json, contextily, datetime, time, concurrent, os, io, PIL, cv2, cvlib, seaborn <br>
<b> Data used for Mapping Areas of Singapore: </b> [Master Plan 2014 Subzone Boundary (No Sea)](https://data.gov.sg/dataset/master-plan-2014-subzone-boundary-no-sea)

## Data Collection
<p align='justify'> API requests returned metadata on 89,282 images captured once per minute by 323 traffic cameras across Singapore in January 2019 and January 2020. Downtown traffic was used as a proxy for overall traffic throughout Singapore. Hence, the analysis focused on images captured by camera 1709 located in the downtown area. The dataset includes 30,234 images from January 2019 and 29,977 images from January 2020. </p>
The following features were obtained:
* <b> timestamp: </b> The date and time that the image was captured, written in W3C format
* <b> image: </b> The url containing the traffic image
* <b> camera_id: </b> The four-digit identifier of the camera that captured the image
