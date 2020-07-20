# Big-Data-Project-on-Flight-Data-Analysis-using-Apache-Couch-DB

Flight delays are an important issue in the flight industry, because it will lead to financial crisis in the business. This project identifies the factors influence the occurrence of flight delays. Research survey indicates that every year about 20% of flights are delayed or cancelled. It costs in very big way for both travellers and airlines. 

The project is to analyze flight data by gathering data from official web portal. The data that’s maintained in web portal is big in size and it is increasing every day. So obviously big data analytics are the best way to analyze the data and extract the useful knowledge from the data set. CouchDB and MapReduce function is used here in this project as a big data concept. 

Steps for installing CouchDB : 
 
 Update the package list: sudo apt update  Add the CouchDB PPA repository: 
sudo add-apt-repository ppa:couchdb/stable  Update the package list once more: 
sudo apt update  Then install CouchDB with the command: 
sudo apt install couchdb  Use curl to verify that CouchDB is installed and running: 
curl localhost:5984          The server will respond with a welcome message: 
{"couchdb":"Welcome","uuid":"266009d1980fbda93d96cd3bd 95c2e81","version":"1.6.1","vendor":{"version":"16.04" ,"name":"Ubuntu"}} 
 
Flight Data Analysis Using Couchdb 
 
Department of Computer Science & Engineering, NMAMIT Nitte 10 
 
CouchDB uses a basic HTTP interface, and returns JSON objects. You can use the curl utility from the command line to communicate with CouchDB. 
 The command to view a list of databases is: 
curl localhost:5984/_all_dbs           
         The server will return a JSON reply to the command line: 
 
student@ubuntu:~$ curl localhost:5984/_all_dbs 
["_replicator","_users"] 
 
 The curl command uses the GET method by default. To send CouchDB a request with a different method, use the -X flag to override the default method, and specify the method you wish to use instead: 
curl -X PUT localhost:5984/[etc.] 
 
 We must use the PUT method to create a database. The command to create a database named flights is: 
curl -X PUT http://127.0.0.1:5984/flights 
         The server will confirm the creation: 
{"ok":true}                             
 
 We must use the GET method to get the information of the database. The command to create a database named flights is: 
 
curl -X GET http://127.0.0.1:5984/flights 
 
 
 
 
 
Flight Data Analysis Using Couchdb 
 
Department of Computer Science & Engineering, NMAMIT Nitte 11 
 
 The server will respond with the database information.   {"db_name":"flights","doc_count":50,"doc_del_count":2,"update_seq":69, "purge_seq":0,"compact_running":false,"disk_size":286824,"data_size":31 407,"instance_start_time":"1589356156304603","disk_format_version":6, "committed_update_seq":69} 
 
 The PUT request is used to create new objects, databases, documents, views and design documents. 
 
student@ubuntu:~$ curl -X PUT http://127.0.0.1:5984/flight/"001" -d '{"YEAR":2015,"MONTH":1,"DAY":1,"DAY_OF_WEEK":4,"AIRLINE ":"AS","FLIGHT_NUMBER":98,"TAIL_NUMBER":"N407AS", "ORIGIN_AIRPORT":"ANC","DESTINATION_AIRPORT":"SEA", "SCHEDULED_DEPARTURE":5,"DEPARTURE_TIME":2354, "DEPARTURE_DELAY":11,"TAXI_OUT":21,"WHEELS_OFF":15, "SCHEDULED_TIME":205,"ELAPSED_TIME":194,"AIR_TIME":169, "DISTANCE":1448,"WHEELS_ON":404,"TAXI_IN":4,"SCHEDULED_ ARRIVAL":430,"ARRIVAL_TIME":408,"ARRIVAL_DELAY":22, "DIVERTED":0,"CANCELLED":0,"CANCELLATION_REASON":""," AIR_SYSTEM_DELAY":"","SECURITY_DELAY":"","AIRLINE_DEL AY":"","LATE_AIRCRAFT_DELAY":"","WEATHER_DELAY":""}' 
The server will respond with   The server will return a JSON document with content “ok”-true indicating the operation was successful along with “id” which stores the id of the document and  “rev” indicates revision id. 
 
         "ok":true,"id":"001","rev":"1-7b0679872f892890f77bdbba9a41aadc"} 
 
 The GET request is used to get the information of the document from the specified database. 
 
curl -X GET http://127.0.0.1:5984/flight/001 
 
 
 
 
Flight Data Analysis Using Couchdb 
 
Department of Computer Science & Engineering, NMAMIT Nitte 12 
 
 The server will return the document from specified database and specified id. 
 
{"_id":"001","_rev":"17b0679872f892890f77bdbba9a41aadc","YEAR":2 015,"MONTH":1,"DAY":1,"DAY_OF_WEEK":4,"AIRLINE":"AS","FL IGHT_NUMBER":98,"TAIL_NUMBER":"N407AS","ORIGIN_AIRPO RT":"ANC","DESTINATION_AIRPORT":"SEA","SCHEDULED_DEP ARTURE":5,"DEPARTURE_TIME":2354,"DEPARTURE_DELAY":11,"TAXI_OUT":21,"WHEELS_OFF":15,"SCHEDULED_TIME":205," ELAPSED_TIME":194,"AIR_TIME":169,"DISTANCE":1448,"WHEEL S_ON":404,"TAXI_IN":4,"SCHEDULED_ARRIVAL":430,"ARRIVAL _TIME":408,"ARRIVAL_DELAY":22,"DIVERTED":0,"CANCELLED" :0,"CANCELLATION_REASON":"","AIR_SYSTEM_DELAY":"","SE CURITY_DELAY":"","AIRLINE_DELAY":"","LATE_AIRCRAFT_DE LAY":"","WEATHER_DELAY":""} 
 
 
We can easily use and manage CouchDB from the command line using the Curl utility. However, CouchDB also comes with a built-in web-based administration interface named Futon.       
