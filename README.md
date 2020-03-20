# Splunk SimData Examples

This project is a collection of SimData example scenes and simulation files.
Each example has its own corresponding README file.

SimData is a tool that generates event data from a simulation of a user-defined scenario. Instead of using a sample set of data that is repetitive and unrealistic, SimData allows you to generate a rich and robust set of events from real-world situations by mimicking how multiple systems work together and affect the performance of your system.

## Get started

For details about installing, configuring, and running SimData, see the [Splunk Developer Portal](https://dev.splunk.com/enterprise/docs/dataapps/simdata/).

### Requirements

* Java 8+
* Download SimData the SimData JAR file: https://dev.splunk.com/enterprise/downloads

### Example usage

This example shows how to execute the SimData CLI:

```sh
java -jar <SimData JAR file> --simulation <path to simulation file> --scene <path to scene file>
```

## Contact
If you have questions, reach out to us on [Slack](https://splunkdevplatform.slack.com) in the **#simdata** channel or email us at _devinfo@splunk.com_.