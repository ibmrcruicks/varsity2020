# Varsity 2020
workshop options:

+ [Dashboards](#dashboards)
+ [Data stores](#datastores)
+ [IOT](#iot_connection)


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

# IOT connection

IBM offers a basic [Internet of Things platform](https://cloud.ibm.com/catalog/services/iotf-service) for free to allow building prototype IOT solutions; this uses the [MQTT messaging standard](https://mqtt.org) publish and subscribe model to enable applications to create and consume events from edge devices, sensors, and [digital twins](https://www.ibm.com/blogs/internet-of-things/iot-cheat-sheet-digital-twin/).

Node-RED MQTT nodes are usually part of a standard installation, so connecting to IOT platforms (IBM and others) can be straightforward. Using the subscribe mechanism, events can be presented to applications which can then createenhanced timeseries data, using a combination of realtime lookups, reference tables, and predictive models.

<details><summary>Examples/tutorials</summary>
  
+ [Talk to your digital twin](https://developer.ibm.com/recipes/tutorials/talk-to-your-sensor-using-the-watson-iot-platform-and-conversation-services/)
+ [Publishing to IOT clouds](https://labs.eleks.com/2019/01/node-red-library-iot-cloud.html)

</details>
