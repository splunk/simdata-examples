# Application Management example

This simulation has CSV files used for mockdata. They are included under the `data` directory here. CSV mockdata files must reside at the same file system path as the simulation file, or the `data` directory at that path.

The application management simulation intends to model a simple web application with 3 entities:

* `User` entities sending requests to `WebServer` entities
* `WebServer` entities receiving requests from `User` entities, and sending/receiving requests to `Database` entities
* `Database` entities receiving requests from `WebServer` entities

## Sending data to Splunk Enterprise HEC

Before using this simulation some configuration needs to be updated.

In `app-man.json`, under the `transports` property there are some placeholder values for the `SplunkHEC` transport.

* `uri` is the Splunk Enterprise URI including the HEC port (8088 by default)
* `token` is the Splunk Enterprise HEC token
* `default_index` is the default Splunk Enterprise index to send events to

## Running the simulation

```sh
java -jar <SimData JAR file> --simulation app-man.simulation --scene app-man.json
```

### Expected output

Since events are configured to go to `SplunkHEC`, nothing will be printed to the console.

```sh
Starting simulation
```