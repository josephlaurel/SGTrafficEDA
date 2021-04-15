# Analyzing the Impact of COVID-19 on Singapore Traffic using Computer Vision

## Overview
* Performed time series analysis to compare Singapore highway traffic in January 2019 vs. January 2020
* Scraped 60,174 downtown traffic images with time and geolocation data from the [Government of Singapore's API](https://data.gov.sg/dataset/traffic-images)
* Detected the number of cars in images using OpenCV and revealed that traffic volume was largely unchanged vs. the previous year

## Code and Resources Used
<b> Python Version: </b> 3.7 <br>
<b> Packages: </b> requests, pandas, geopandas, libproj-dev proj-data proj-bin, libgeos-dev, cython, cartopy, geoplot, matplotlib, geoplot, json, contextily, datetime, time, concurrent, os, io, PIL, cv2, cvlib, seaborn <br>
<b> Coordinates used for Map of Singapore: </b> [Master Plan 2014 Subzone Boundary (No Sea)](https://data.gov.sg/dataset/master-plan-2014-subzone-boundary-no-sea) <br>
<b> Guide to OpenCV Set-Up: </b> ["How to use OpenCV with GPU on Colab?" by C Kuan](https://towardsdatascience.com/how-to-use-opencv-with-gpu-on-colab-25594379945f)

## Data Collection
<p align='justify'> API requests returned JSON objects metadata on 89,282 images captured once per minute by 323 traffic cameras across Singapore in January 2019 and January 2020. Downtown traffic was used as a proxy for overall traffic throughout Singapore. Hence, the analysis focused on images captured by camera 1709 located in the downtown area. The dataset includes 30,234 images from January 2019 and 29,940 images from January 2020. <br><br> The following features were obtained:</p>

* <b> timestamp: </b> The date and time that the image was captured, written in W3C format
* <b> image: </b> The url containing the traffic image
* <b> camera_id: </b> The four-digit identifier of the camera that captured the image
* <b> location.latitude: </b> The latitude coordinate value of the camera that captured the image
* <b> location.longitude: </b> The longitude coordinate value of the camera that captured the image
* <b> image_metadata.height: </b> The height of the traffic image, measured in pixels
* <b> image_metadata.width: </b> The width of the traffic image, measured in pixels
* <b> image_metadata.md5: </b> The metadata of the image stored in MD5 format
* <b> num_cars </b> (engineered feature): The number of cars in the image as detected using the cv2 package

## Data Exploration
![Downtown Singapore](Graphs/downtown_sg.png)
Scraped camera locations and names of key downtown subzones were plotted on the map of Singapore. Based on the plot, camera 1709 was found to be located between the geographical center of Singapore and the coastal downtown area. Hence, traffic volume captured by this camera was the focus of the analysis.

## Data Preparation
* Rows of data with identical image URLs were dropped.
* Images were extracted concurrently from the scraped URLs. Counts of car in the images were detected using OpenCV and were appended to the dataframes.
![Labeled Cars](Graphs/labeled_cars.png)
* Timestamp strings were converted to datetime objects to allow the dataframes to be sorted chronologically.
* The converted timestamps were set as the dataframe indices to allow the data to be resampled by day.

## Key Findings

![Monthly Traffic](Graphs/monthly%20traffic.png)
### Monthly Traffic
<p align='justify'> For the majority of January 2020, there was no significant difference in traffic volume compared to the same month in 2019. However, traffic from January 23 to 27, 2020 was lower by several hundred cars per day versus the same period in the previous year. As Singapore reported its first COVID-19 case on January 23, 2020 <i><a href='https://www.channelnewsasia.com/news/singapore/singapore-covid-19-outbreak-evolved-coronavirus-deaths-timeline-12639444'> (Channel News Asia, 2020),</a> </i> we may infer that this event was associated with the relatively lower traffic levels. </p> <br>

![Weekly Traffic](Graphs/weekly%20traffic.png)
### Weekly Traffic
<p align='justify'> Average traffic volume on each day of the week in 2019 and 2020 does not appear to have differed significantly. This suggests that the start of the COVID-19 outbreak was not correlated with a notable shift in weekly traffic trends. <p>
