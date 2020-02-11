# Varsity 2020
workshop options:

+ [Cloud catalog](#catalog)
+ [Developing applications](#developing-applications)
+ [Node-RED low code enironment](#node-red)
+ [Data stores](#datastores)
+ [IOT](#iot)
+ [Dashboards](#dashboards)
+ [Weather](#weather)
+ [Analytics](#analytics)
+ [Machine Learning](#machine-learning)


# Catalog

The core of any cloud environment is its catalog - the go-to list of service and capabilities that you as a developer can exploit to build and run applications. You will find very simialr approaches by all the major cloud platform vendors, with varying degrees of attractiveness and usability.

The [IBM Cloud catalog](https://cloud.ibm.com/catalog) provides a comprehensive list of services you can use, and includes the
charging models available -- i.e. how much would you pay to use a particular service.

To get you started building applications, IBM provide a wide range of the services through a `Lite` plan - essentially this allow free use of these services within their particular limits/constraints) to allow you to build prototype applications. Some of these service can be used indefinitely, without ever incurring charges; others may have a time-limit on how long the free use lasts.

An alternative view of the catalog [MyCatalog](https://mycatalog.mybluemix.net) provides a quick and consistent view of available services, their descriptions, and available billing models.

# Developing applications

All the best cloud platforms provide a variety ofroutes to developing, and running applications; most offer some mechanism that support virtual machines and, more recently, containers. Most offer `application runtimes` - these allow developers to concentrate on their application code, and links to services, and largely ignore the underlying technologies and dependencies needed to run that code.

In the IBM Cloud, you will find:
+ **cloud foundry**
  
  an application runtime environment that allows you to build applications in (any combination of):
  <table>
  <tr>
    <td>Ruby</td>
    <td>Java</td>
    <td>Javascript</td>
  </tr>
  <tr>
    <td>Go</td>
    <td>Python</td>
    <td>PHP</td>
  </tr> 
  <tr>
    <td>Swift</td>
    <td>.Net</td>
    <td>tomcat</td>
  </tr>
  </table>
  There are also community-maintained "buildpacks", which can be used to extend the runtimes supported [public buildpacks](https://github.com/cloudfoundry?utf8=✓&q=buildpack)
  
+ **virtual machines**
  
  \preconfigured software environments to which you add your application code, management tools, and links to other services and functions

# Node-RED

# Datastores

## Structured data

for data that is unlikely to change "shape" once defined, or data that needs to be continually analysed/aggregated, SQL databases can be a simple and effective choice.

[Db2 on Cloud](https://cloud.ibm.com/catalog/services/dashdb-for-transactions) offers a free SQL database to try out capabilities; you can also use other cloud databases (ElephantSQL, Azure SQL, Amazon RDS, Google Cloud db, etc)

To integrate easily with Db2 from Node-RED, install the [dashdb node](https://flows.nodered.org/node/node-red-nodes-cf-sqldb-dashdb) - this will allow you to query tables, update rcords, and magae database schemas - perfect for experiementing with a relational datastore.

<details><summary>Examples/tutorials</summary>
  
+ [SQL on Raspberry Pi](https://randomnerdtutorials.com/sqlite-with-node-red-and-raspberry-pi/)
+ [Steve Cope - Storing IOT events with SQL](http://www.steves-internet-guide.com/storing-iot-data-sql-database/)
+ [NoSQL to DB2](https://github.com/cloudant-labs/data-flow-examples/tree/master/node-red)

</details>

## Unstructured data

for data that changes shape over timre (or from one isntance to the next), or has a variety of frequency in when values are produced or changed, a schema-less datastore can be a good starting point.

[Cloudant](https://cloud.ibm.com/catalog/services/cloudantnosqldb) offers a free NoSQL JSON datastore for handling key/value and document-oriented data instances. Alternatives that you might consider - MongoDB, Redis, Cassandra, Google Cloud Spanner, Azure Cosmos db, Amazon DynamoDB, etc.

Node-RED in the IBM Cloud environment has automatic access to a cloudant datastore instance, as it is used to store the application configurations. In other  environemnts, Cloudant integration is available through the installation of the [Cloudant node](https://flows.nodered.org/node/node-red-node-cf-cloudant)

<details><summary>Examples/tutorials</summary>
  
+ [Basic cloudant I/O](https://www.youtube.com/watch?v=FXm2Bk-tCIc)
+ [MongoDB prototyping](https://www.compose.com/articles/power-prototyping-with-mongodb-and-node-red-2/)
+ [NoSQL to DB2](https://github.com/cloudant-labs/data-flow-examples/tree/master/node-red)

</details>

# IOT

## IOT connection

IBM offers a basic [Internet of Things platform](https://cloud.ibm.com/catalog/services/iotf-service) for free to allow building prototype IOT solutions; this uses the [MQTT messaging standard](https://mqtt.org) publish and subscribe model to enable applications to create and consume events from edge devices, sensors, and [digital twins](https://www.ibm.com/blogs/internet-of-things/iot-cheat-sheet-digital-twin/).

Node-RED MQTT nodes are usually part of a standard installation, so connecting to IOT platforms (IBM and others) can be straightforward. Using the subscribe mechanism, events can be presented to applications which can then createenhanced timeseries data, using a combination of realtime lookups, reference tables, and predictive models.

While there are some namespace restrictions, and access controls that the Watson IOT Platform enforces, it is still under the covers an MQTT broker - that means any MQTT client device/system can connect and exchange messages, as long as the authentication and authorisation requirements are followed.

<details><summary>Examples/tutorials</summary>
  
+ [MQTT from CC3200](https://developer.ibm.com/answers/questions/492812/how-to-subscribe-ibm-watson-iot-platform-with-cc32/)
+ [Talk to your digital twin](https://developer.ibm.com/recipes/tutorials/talk-to-your-sensor-using-the-watson-iot-platform-and-conversation-services/)
+ [Publishing to IOT clouds](https://labs.eleks.com/2019/01/node-red-library-iot-cloud.html)
+ [Connect to IBM IOT with MQTT](https://www.opc-router.com/connecting-ibm-watson-iot-platform-via-mqtt/)

</details>

## IOT simulation

When IBM launched the Internet of Things platform, it provided a free unauthenticated service instance that anyone could connect to, mainly intended for those would wanted try out device-level connection to the platform; this was known as [Quickstart](https://quickstart.internetofthings.ibmcloud.com/#/). Associated with this instance is a [browser-based simulator](https://quickstart.internetofthings.ibmcloud.com/iotsensor/) which provides automatic publishing of pseudo events, and manual override -- a great tool for testing how IOT application handle edge-case, and extreme values.

This service is due to be discontinued during [February 2020](https://developer.ibm.com/iotplatform/2020/01/17/advanced-notice-withdrawal-of-watson-iot-platform-quick-start/). 

The recommended alternative is to create your own [IOT service instance](https://cloud.ibm.com/catalog/services/iotf-service), and then use the [Device Simulation](https://cloud.ibm.com/docs/services/IoT?topic=iot-platform-sim_device_data) capability. This is provides much richer functions for generating data for single or multiple devices and device-types, but provides no mechanism for maunual override. 

# Dashboards

Use your Node-RED skills to build interactive dashboards for
+ data visualisation
+ control systems interfaces
+ documentation

Install the [node-red-dashboard](https://flows.nodered.org/node/node-red-dashboard) into your Node-RED palette (best done through the package.json, but can also be added via `Manage Palette`.

![dashnoard](https://nodered.org/images/dashboarde.png)

This node provides quick and easy access to buttons, charts, forms, and other interactive web gadgetry.

<details><summary>Examples/tutorials</summary>
  
+ [basic IOT dashboard](https://developer.ibm.com/recipes/tutorials/ui-dashboard-for-iot-device-data-using-node-red/)
+ [Freewave dashboard tutorial](https://www.youtube.com/watch?v=X8ustpkAJ-U)
+ [Earthquake monitor](https://developer.ibm.com/tutorials/simple-earthquake-monitoring-system-using-nodered/)

</details>

# Weather

A growing area of interest in the IOT world is knowing weather observations in the local area where IOT events are generated, and being able to use historical/almanac information to help predict similar conditions, as well as exploiting a variety of forecasting options.

IBM, through the [Weather Company](https://www.ibm.com/uk-en/marketplace/weather-company-data-packages/purchase) offers a rich set of weather-related services, including "lifestyle" related data (pollen, skiiing, cycling, etc); until Autumn 2019, there was a free developer-oriented service available through the IBM Cloud platform - it has been withdrawn. You can have free developer access to the Weather Company API as a particpant of the annual [Call for Code challenge](https://callforcode.org/) - check the website for validity period. Annual challenges are announced February/March each year.

A great alternative free source of weather data - observations, forecasts and hostorical averages - is available through [Dark Sky](https://darksky.net/) (previously known as **forecast.io**).

<details><summary>Examples/tutorials</summary>

+ [Call for Code - Weather API](https://github.com/Call-for-Code/weather-api-nodejs)
+ [Dark Sky weather dashboard](https://www.instructables.com/id/Build-a-Weather-Dashboard-Using-Dark-Sky-API/)
+ [Get started with OpenWeatherMap](https://openweathermap.org/appid)

</details>

# Analytics

Statistical modelling and analysis, data ingest and feature engineering, visualisation - all aspects of data anayltics that you can use to better understand and shape your data. IBM's [Watson Studio](https://cloud.ibm.com/catalog/services/data-science-experience) provides an intregated environment for linking data with tools, and providing sharing capabilities. It is available as a free option, with plenty of capacity to experiment.

The most popular tools used in data analysis - Jupyter Notebooks, R Studio, and SPSS Modeler - are built in to Watson Studio.

<details><summary>Examples/tutorials</summary>
  
+ [Watson Studio - SPSS Modeler](https://developer.ibm.com/technologies/data-science/tutorials/watson-studio-spss-modeler-flow/)
+ [Data visualisation with python](https://developer.ibm.com/technologies/analytics/patterns/visualize-data-with-python)
+ [Watson Studio - Air quality notebook](https://github.com/IBM/smart-city-analytics) and [working notebook](https://github.com/IBMDeveloperUK/air-quality-analysis)

</details>

# Machine Learning

![pretty picture](https://www.risk.net/sites/risk/files/styles/landscape_750_463/public/2017-06/neural-network.jpg?itok=ev-Fja8p)

[overview](https://www.ibm.com/topics/machine-learning)

<details><summary>Examples/tutorials</summary>
  
+ [Machine Learning environment](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-overview.html?audience=wdp)
+ [Cognitive IOT application in 7 steps](https://developer.ibm.com/technologies/data-science/tutorials/iot-cognitive-iot-app-machine-learning)
+ [AutoAI - AI for AI tutorial](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/autoai_example_binary_classifier.html?audience=wdp)
  
</details>
