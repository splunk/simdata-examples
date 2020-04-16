# Application Management example

This simulation has CSV files used for `mockdata`. They are included under the `data` directory here. CSV `mockdata` files must reside at the same file system path as the simulation file, or the `data` directory at that path.

The application management simulation intends to model a simple web application with three entities:

* `User` entities sending requests to `WebServer` entities
* `WebServer` entities receiving requests from `User` entities, and sending/receiving requests to `Database` entities
* `Database` entities receiving requests from `WebServer` entities

## Sending data to Splunk Enterprise HEC

Before using this simulation, some configuration files need to be updated.

In `app-man.json`, under the `transports` property, there are some placeholder values for the `SplunkHEC` transport.

* `uri` is the Splunk Enterprise URI including the HEC port (8088 by default)
* `token` is the Splunk Enterprise HEC token
* `default_index` is the default Splunk Enterprise index to send events to

## Setup

This simulation will generate data in the index configured in the `app-man.json` file. Make sure the index exists, and the Splunk HEC token is configured to send data to that index.

## Running the simulation

```sh
java -jar <SimData JAR file> --simulation app-man.simulation --scene app-man.json
```

### Expected output

Since events are configured to go to `SplunkHEC`, nothing will be printed to the console.

```sh
Starting simulation
```

### Helpful Splunk searches

The following queries show examples of finding meaningful information in the generated data using Splunk searches.

#### HTTP status error codes by webserver

```
index=[your_index_here] code!=200 | stats count by code, webserverName
```

#### Timechart of load times by page

```
index=[your_index_here] source=user pageName=* | eval totalTime = renderTime + queryTime | timechart avg(totalTime) by pageName
```


#### Timechart of database query execution times

```
index=[your_index_here] source="database" executionTime=* | timechart avg(executionTime) by server
```
