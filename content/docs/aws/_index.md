---
title: 'Integrate with AWS'
---

 You can collect metrics about your AWS services in a CloudWatch repository, then use [AWS CloudWatch Metric Streams](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Metric-Streams.html) to direct a real-time stream of metrics to a destination of your choice, like to Company. Integrating AWS with Company lets you view your AWS data alongside your other observability entities, giving you a seamless monitoring experience as you troubleshoot and make improvements to your system environment. 
 
 To get started, you'll follow three broad integration steps: 
 
 1. Defining an HTTP endpoint set to either our US or EU datacenters
 1. Creating custom configurations for the kinds of AWS data you want to stream, based on your individual use case
 1. Adding your AWS account to your Company account

## Prerequisites 

Before you get started, make sure to update the permissions to your AWS roles:

 * At minimum, create a `ReadOnlyAccess` policy and apply them to your AWS roles associated with your Company account. 
 * If you're managing multiple AWS accounts, make sure you connect all of them to a single Company account. 

 ##  Integrate CloudWatch Metric Streams with the platform

These integration procedures use [AWS console](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-is.html) to complete set up. They assume you've created a Kinesis Data Firehose and metric stream in the past, but we'll provide some external links to AWS docs to help you along the way.  

{{% steps %}}

### Create and configure a Firehose delivery stream

AWS manages your data streaming with Amazon Data Firehose, which lets you [create a separate Kinesis Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html) to deliver your AWS metric data. After creating a new Firehose delivery stream, input the following configurations from AWS constole: 

{{% details title="Delivery stream configurations" %}}

* Destination parameters: 

    * Source: Direct PUT or other sources
    * Data transformation: `disabled`
    * Record format conversion: `disabed`
    * Destination: Choose Company from the dropdown.

* Define these Company-specific configurations under **Destination settings**:

    * HTTP endpoint URL - US Datacenter: `https://aws-api.THISISFAKE.com/cloudwatch-metrics/v1`
    * HTTP endpoint URL - EU Datacenter: `https://aws-api.eu01.THISISFAKE.net/cloudwatch-metrics/v1`
    * API key: Enter your license key
    * Content encoding: `GZIP`
    * Retry duration: `60`

* S3 backup mode: Failed data only
* S3 bucket: select a bucket or create a new one to store metrics that failed to be sent.
* Apply buffer conditions
    * Buffer size: `1MB`
    * Buffer interval: `60 (seconds)`
* For the **Permissions IAM role**, either create or update IAM role for Company.

{{% /details %}}

 If you manage multiple regions across different AWS accounts, create a separate Kinesis Data Firehose per each region and [point them to Company](https://docs.aws.amazon.com/firehose/latest/dev/create-destination.html).


### Create and configure a new metric stream

You can think of a metric stream as a post office for your AWS metrics while the Firehose delivery system is the truck that delivers it to yourr destination. This step assigns your Firehose to a newly created metric stream, which ensures your AWS data is delivered to the platform. 

1. From AWS Console, find **CloudWatch Service**, choose **Streams** from the Metrics menu, then click **Create a metric stream**. 
1. Configure your metric stream based on your use case. For example, you may opt to use inclusion and exclusion filters to push some AWS service metrics to Platform, but not others. 
1. Select the Firehose delivery stream you created in the previous step. We recommend giving it a meaningful name, like `our-company-name-metric-stream`. 
1. Update the default output format to `Open Telemetry 0.7`. JSON is currently unsupported.

### Add your AWS account to platform

You've finished the AWS portion of these procedures, so now it's time to head to the platform. To add your account, go to **PLATFORMWEBSITE > TILE NAME HERE > ANOTHER THING TO SELECT > AWS**. From the left menu, select **Add an AWS account** then select **Use metric streams**. The platform will walk you through the rest!

### Validate your data's streaming

We recommend that you run a simple AWS query using our company's SQL language. Find our query builder anchored at the bottom of the platform, then run this simple query:

```sql
SELECT sum(aws.s3.5xxErrors) FROM Metric WHERE collector.name = 'cloudwatch-metric-streams' FACET aws.accountId, aws.s3.BucketName
```

{{% /steps %}}

## What's next?

Now that you're all set up, we recommend checking out some additional resources:

* Check out how to create alerts, use tags, and manage your AWS data.
* Learn how to monitor your EC2 instances or your EKS cluster.
* Review the mechanics of querying with NRQL to get the most out of your data.