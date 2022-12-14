<properties 
	pageTitle="Introduction to Stream Analytics | Azure" 
	description="Understand Azure Stream Analytics" 
	services="stream-analytics" 
	documentationCenter="" 
	authors="jeffstokes72" 
	manager="paulettm" 
	editor="cgronlun"/>

<tags 
	ms.service="stream-analytics" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.tgt_pltfrm="na" 
	ms.workload="data-services" 
	ms.date="05/06/2015" 
	ms.author="jeffstok"/>


# Introduction to Azure Stream Analytics

Azure Stream Analytics is a fully managed service providing low-latency, highly available, scalable, complex event processing over streaming data in the cloud.


## Introduction to Azure Stream Analytics (video)

In this [video](http://azure.microsoft.com/documentation/videos/introduction-to-azure-stream-analytics-with-santosh-balasubramanian/), Santosh Balasubramanian and Scott Hanselman introduce Azure Stream Analytics. (Duration: 11:22)  

> [AZURE.VIDEO introduction-to-azure-stream-analytics-with-santosh-balasubramanian]

## Motivation & overview

Vast amounts of data are flowing at high velocity over the wire today. Organizations that can process and act on this data in real time can dramatically improve efficiencies and differentiate themselves in the market. Scenarios of real-time stream analytics can be found across all industries: personalized, real-time stock-trading analysis and alerts offered by financial services companies; real-time fraud detection; data and identity protection services; reliable ingestion and analysis of data generated by sensors and actuators embedded in physical objects (Internet of Things, or IoT); web clickstream analytics; and customer relationship management (CRM) applications issuing alerts when customer experience within a time frame is degraded. Businesses are looking for the most flexible, reliable and cost-effective way to do such real-time event-stream data analysis to succeed in the highly competitive modern business world.  

Building stream-processing systems is a complex task. Streaming operations such as correlations and aggregations not only need to be implemented efficiently, but also need to be scalable and fault-tolerant. Additional operational challenges layer on this, including deployment, debugging and monitoring. The costs associated with building and maintaining such a solution quickly rise. Larger enterprises have resigned themselves to paying such a high cost with custom-built solutions, while smaller companies often miss the opportunity due to the high barrier to entry and the prohibitive expense. Azure Stream Analytics tackles these challenges.

Azure Stream Analytics is a fully managed, real-time stream computation service hosted in Microsoft Azure. It provides highly resilient, low-latency, and scalable complex event processing of streaming data. It enables developers to combine streams of data with historic records or reference data to derive business insights easily and quickly.  

With a few clicks in the Azure portal, customers can author a streaming job by using an SQL-like language to specify transformations and monitor the scale/speed of their overall streaming pipeline. The service can easily scale from a few kilobytes to a gigabyte or more of events processed per second. Most other streaming solutions available today require customers to write complex custom code, but with Azure Stream Analytics customers can write simple, declarative, familiar SQL.

Azure Stream Analytics provides a range of operators, from simple filters to complex correlations. Defining time-based windowed operations such as windowed aggregates, or correlating multiple streams to detect patterns such as sequences, or even comparing current conditions to historical values and models can be done in a matter of minutes via the simple set of SQL-like Stream Analytics query language operators. Specifying a streaming pipeline is as simple as configuring its inputs and outputs, and providing an SQL-like query describing the desired transformations. While this suffices for most simple cases, higher-scale and more complex scenarios benefit from the configurability of Stream Analytics. Users can determine how much compute power to dedicate to each step of the pipeline to achieve the desired peak throughput.

Azure Stream Analytics currently connects directly to Azure Event Hubs for stream ingestion, and the Azure Blob service for historical data. Using the range of input and output interfaces of Azure Event Hubs, it is easy to integrate Azure Stream Analytics with other data sources and processing engines without losing the streaming nature of the computations. Data can be written from Stream Analytics to Azure Storage, where it can then later be processed again as a series of events, or used in other forms of batch analytics via Azure HDInsight. Azure Stream Analytics leverages years of Microsoft Research work in developing highly tuned streaming engines for time-sensitive processing, as well as language integrations for intuitive specifications of such. Azure Stream Analytics is built leveraging the open-source community of Hadoop, YARN and REEF for scale-out processing.


## Key capabilities

### Ease of use
Stream Analytics supports a simple, declarative query model for describing transformations. In order to optimize for ease of use, we selected an SQL variant as the domain-specific language (DSL), and we insulate customers from the significant technical complexities underlying our streaming system. Using Stream Analytics query language, you can quickly and easily implement temporal functions, including temporal-based joins, windowed aggregates, temporal filters, and other common operations such as joins, aggregates, projections, and filters.  

While we extend the semantics of SQL in a few ways that are intuitive to an SQL user, we stay within the syntactic boundaries of the SQL standard to facilitate implementation and tool usage. For additional information on our query language, please see the ???Next steps??? section.

### Scalability
Stream Analytics is capable of handling high event throughput of up to 1GB/second. Integration with Azure Event Hubs allows the solution to ingest millions of events per second coming from connected devices, clickstreams, and log files, to name a few. In order to achieve this, we leverage the partitioning capability of Event Hubs, which can yield 1MB/s per partition. Stream Analytics provides support for partitioning while processing these ingested events along both horizontal and vertical axes. A user can partition the computation into a number of logical steps within the query definition, each with the ability to be further partitioned into data-parallel execution elements. Over time, Stream Analytics will automatically scale based on the event ingestion rate, complexity of processing, and expected latencies to allow users to customize their workload appropriately. For further details on implementing scalability, refer to the links in the ???Next steps??? section.  

### Reliability, repeatability and quick recovery
Stream Analytics helps prevent data loss and provides business continuity in the presence of node failures through its built-in recovery and checkpointing capabilities. These capabilities are provided by the Stream Analytics client-anchor model architecture. The service is built to persist state to optimize resumption from node failure, recomputations and cache output to efficiently account for downstream failures.  

With the ability to internally maintain state, the service can provide repeatable results where it is possible to archive events and reapply processing in the future, while getting the same results. This feature enables customers to go back in time and investigate computations for scenarios like root-cause analysis and what-if analysis. These features, in combination, provide fast recovery from processing node failures, quickly reprocessing lost state. 

### Low latency
Stream Analytics is currently optimized for end-to-end observable latencies in the sub-second range. This allows the system to process continually at a high throughput. The communication model is a pull-based, adaptive batching model that operates based on configured timeouts and size limits. Hence, events and other records are batched until the limits are reached. Even with high throughput, the system is able to provide low latencies.

### Reference data
Stream Analytics provides users the ability to specify and use reference data. This could be historical data or data that changes less frequently over time. The system simplifies the use of reference data to be treated like any other incoming event stream to join with other event streams ingested in real time to perform transformations. For additional information on construction and usage of reference data, please see the ???Next steps??? section.



## Business motivations for choosing Azure Stream Analytics

### Low cost
The Stream Analytics service is optimized to provide users very low cost to get going and maintain real-time analytics solutions. The service is built for you to pay as you go based on usage. The usage is derived based on the volume of events processed and the amount of compute power provisioned within the cluster to handle the respective streaming jobs.  

### Fast implementation
With Stream Analytics, you can have a highly scalable real-time event processing solution with no hardware or other up-front costs, no time-consuming installation or setup. Azure takes care of all of that for you. You can be up and running in minutes by simply subscribing to the service via the Azure portal. The friendly user interface in the portal walks you through a step-by-step quick start guide to get your input source configured and tested, and your output store configured and tested. An easy query editor provides auto-complete and recommendation features.  

### Rapid development
Stream Analytics helps you reduce friction and complexity when developing analytics functions for scale-out distributed systems. Developers simply describe their desired transformation in an SQL-based query language, and the system will automatically deal with distributing the workload for scale, performance and resiliency, eliminating the need for procedural programming that is necessary in most stream-processing solutions. Through its built-in abilities and the use of a user-friendly portal, Stream Analytics caters to a high-level developer to quickly and easily do real-time processing without having to worry about such things as infrastructure procurement, ongoing maintenance and scaling. 

## Scenarios & use cases

### Real Time analysis for the Internet of Things
As devices become smarter and more devices are built with communication capabilities, the expectation of what can be done with the data generated and collected from these devices continues to evolve in both the commercial and consumer spaces. It is expected that with so much data available, we can quickly combine and process the data, gaining more insight into the environment around us and the devices we use regularly. A canonical IoT scenario can be described through a vending-machine example:

Vending machines regularly send data such as product stock, status, and temperature to either a field gateway (if the vending machine is not IP capable) or to a cloud gateway (if IP capable) for ingestion into the system. The incoming data stream is processed and transformed such that the computed output can be immediately fed back through the gateways to the device to take a corresponding action. For example, if the machine is overheating, the device might need to reboot itself or automatically do a firmware upgrade without any human intervention. The processed output can also trigger other alerts and notifications for a technician to be scheduled automatically based on the events. 

As more data is gathered and processed, machine learning can also be used to develop and learn from patterns seen in the system. For instance, the possibility exists to predict when machines may need to be serviced based on the real-time event streams being fed into the system, or to schedule preventative maintenance on a technician???s route when things are about to go wrong.

This pattern of devices sending information to a processing system and potentially taking action based on the real-time processed results can be commonly seen across IoT use cases. Other such scenarios include connected cars, clickstream analytics, and facilities management. In order to optimize this feedback loop for low latencies and high throughput, Stream Analytics can be used to ingest data from Azure Event Hubs, processing the data and sending the data right back to Event Hubs for the respective subscribed device to take the appropriate action.  


![Azure Stream Analytics real time analysis for the Internet of Things (IoT)][img.stream.analytics.scenario1]


### Telemetry & log analysis via dashboards
As the volume of devices, machines and applications grows, a common enterprise use case to run businesses is the need to monitor and respond to changing business needs by creating rich analytics in near real time. A canonical telemetry/log analysis scenario can be described by using an online service or application example, but the pattern is commonly seen across businesses that collect and report on application or device telemetry:

The application or service regularly collects health data. Data representing the current status of the application or infrastructure at a point in time, user request logs, and other data representing actions or activities performed within the application are collected. The data is historically saved to a blob or other types of data store for further processing.

With the recent trend towards real-time dashboarding, in addition to saving the data to a blob or other type of store for historical analysis, customers are looking to process and transform the stream of incoming data directly such that it can be immediately provided to end users in the form of dashboards and/or notifications when action needs to be taken. For example, if a service site goes down, operations personnel can be notified to begin investigation and resolve the issue quickly. In several of these use cases, a human typically monitors a real-time dashboard built on top of the data set updated after processing of the ingested data via Stream Analytics. 
 
![Azure Stream Analytics telemetry and log analysis via dashboards][img.stream.analytics.scenario2]

### Event archival for future processing
The expectations for fast and agile execution in businesses continue to grow. Businesses and developers are now opting for easy-to-use, cloud-based platforms to cope with the demand for more agility, and are looking for platforms that enable them to ingest and process a continuous stream of data generated by their systems in near real time. Today, these customers are unable to leverage a service that is optimized for low latency writes to a data store and hence end up losing several crucial sets of data that might reveal valuable insights for their business. A canonical event-archival scenario can be described as follows:

Data from various devices and platforms that are distributed across the world is pushed to a centralized data collector. Once the data is at the central location, some stateless transformation is performed on it, such as scrubbing personally identifiable information, adding geo-tagging, and performing IP lookup. The transformed data is then archived into Blob storage in a way that can be readily consumed by HDInsight or other tools for offline processing.

![Azure Stream Analytics event archival for future processing][img.stream.analytics.scenario3]
 
## Get help
For further assistance, try our [Azure Stream Analytics forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=AzureStreamAnalytics)

## Next steps

- [Introduction to Azure Stream Analytics](stream-analytics-introduction.md)
- [Get started using Azure Stream Analytics](stream-analytics-get-started.md)
- [Scale Azure Stream Analytics jobs](stream-analytics-scale-jobs.md)
- [Azure Stream Analytics Query Language Reference](https://msdn.microsoft.com/library/azure/dn834998.aspx)
- [Azure Stream Analytics Management REST API Reference](https://msdn.microsoft.com/library/azure/dn835031.aspx)


<!--Image references-->
[img.stream.analytics.scenario1]: ./media/stream-analytics-introduction/Introduction-to-Azure-Stream-Analytics_01.png
[img.stream.analytics.scenario2]: ./media/stream-analytics-introduction/Introduction-to-Azure-Stream-Analytics_02.png
[img.stream.analytics.scenario3]: ./media/stream-analytics-introduction/Introduction-to-Azure-Stream-Analytics_03.png


<!--Link references-->
[stream.analytics.developer.guide]: stream-analytics-developer-guide.md
[stream.analytics.scale.jobs]: stream-analytics-scale-jobs.md
[stream.analytics.limitations]: stream-analytics-limitations.md
[stream.analytics.introduction]: stream-analytics-introduction.md
[stream.analytics.get.started]: stream-analytics-get-started.md
[stream.analytics.query.language.reference]: http://go.microsoft.com/fwlink/?LinkID=513299
[stream.analytics.rest.api.reference]: http://go.microsoft.com/fwlink/?LinkId=517301
