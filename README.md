FINAL VERSION:
* GIS Programming project to find a location for a new astronomical 
  observatory in France
* 05/04/2020
* This project has been developed for the Geospatial Programming class
  of Spring 2020, an international collaboration between two universities,
  EPF of Sceaux, France and RUDN of Moscow, Russia.
* EPF : https://www.epf.fr/
* RUDN : http://www.rudn.ru
* Author : Maelle Sannier, EPF engineering student in 4th year, 
  Aeronautics and Space major
* Instructor : Naci Dilekli, RUDN Professor, https://github.com/ndilekli/


DATA ARE FROM: 
* See data in Folder « Images »

* Luminous Pollution and Cloudiness: Image and data processing by NOAA’s 
  National Geophysical Data Center. MSP data collected by US Air Force 
  Weather Agency. https://ngdc.noaa.gov/eog/dmsp/downloadV4composites.html#AVSLCFC
* Altitude: Copernicus Land Monitoring Services 
  https://land.copernicus.eu/imagery-in-situ/eu-dem/eu-dem-v1.1?tab=mapview
* GPS coordinates of French cities: https://www.galichon.com/codesgeo/index.php
* Number of people in French cities in 2017: INSEE 
  https://www.insee.fr/fr/statistiques/4265429?sommaire=4265511
* List of french observatories: Wikipedia & Google Maps


PURPOSE: 
* This project can be used to find a location for a new astronomical 
 observatory in France. It takes as inputs the Altitude in France, the 
 Luminous pollution in France, the cities and their number of inhabitants,
 as well as the cloudiness in France, and the location of existing astronomical
 observatories in France. 


HOW TO GET STARTED:
* Download the data under one and only folder that you will call « Observatories »
* Check that you do have a folder called « Results » that will host your results layers
  inside the Observatories folder
* Download ArcGIS if you do not have it already on your pc.
* Open Find_Observatories.ipynb and run it with your own parameters.


PARAMETERS:
* The user have to set as inputs inside the function parameters the following parameters
* workspace = storage space defined by the user e.g "C:/Observatories"
* fc1 = first layer to use to create buffers : "frenchville.shp"
* b1  = Radius Buffer in Kilometers for 1rst feature class "30 Kilometers"
* fc2 = second layer to use to create buffers : "Observatories.shp"
* b2  = Radius buffer in kilometers for 2nd feature class
* citysize = We want to avoid cities over <citysize> inhabitants e.g <50000>
* coef1 = coefficient in the weighted sum for Crit1 e.g <3>
* coef2 = coefficient in the weighted sum for Crit2
* coef3 = coefficient in the weighted sum for Crit3
* percentage = percentage between 0 and 100 of best pixels of the weigthed 
  sum layer that the user wants to keep e.g <10>


STEPS:
* Buffers are created around the existing observatories and the cities over
  city size inhabitants.
  ![buffers observatories](Cities_and_Observatories_with_buffers.png)
* The buffers are united and erased from the 3 principal layers 
  (luminous pollution, altitude, cloudiness) of the study.
  ![buffers erased from layers](Layers_with_Erased_buffers.png)
* The 3 layers are normalized from 0 to 100 and then summed with coefficients entered by 
  the user in an arithmetic layer
* The user choose how much percentage of this layer he wants to keep. It means
  the best pixels will be extract in another layer (the pixels that will have the higher 
  values --> the best places in France relatively to our criteria)
* This percentage is intersected with the frenchville (french cities)
  layer database.
* As a result the user will have one or a list of cities/villages, satisfying 
  its criteria and that is able to host this new astronomical observatories.


QUICK VISUALIZATION:
* See Screenshots and Flowchart contained in the repository.
  ![Flowchart](Flowchart-finalversion.jpg)

USEFULNESS:
* Run the code with several parameters, one can choose the minimum size 
  of the cities to avoid, as well as the sizes of the buffers around 
  them and around the existing observatories. The GPS coordinates of the final
  cities will be given in output. One can run the code several times and this
  automatization is a lot faster than doing it on Arcmap. Moreover, one do not
  need to have any qualification on ArcGis to get a result.

——————————————————————————————————————

HOW TO GET HELP:
* Contact the author by electronic mail : maelle.sannier@epfedu.fr

WHO MAINTAINS AND CONTRIBUTES TO THE PROJECT:
* Contributor : Maelle Sannier
* The project will not be updated after the Final Version release.





