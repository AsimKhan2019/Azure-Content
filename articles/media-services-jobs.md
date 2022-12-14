<properties 
	pageTitle="Working with Azure Media Services Jobs" 
	description="This topics gives an overview of how to manage Managing Azure Media Services Jobs." 
	services="media-services" 
	documentationCenter="" 
	authors="juliako" 
	manager="dwrede" 
	editor=""/>

<tags 
	ms.service="media-services" 
	ms.workload="media" 
	ms.tgt_pltfrm="na" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.date="03/10/2015" 
	ms.author="juliako"/>

#Working with Azure Media Services Jobs

A **Job** contains metadata about the processing to be performed. Each **Job** contains one or more **Tasks** that specify an atomic processing task, its input Assets, output Assets, a media processor and its associated settings. For more information on encoder settings, see Encoder Guides and Encoder Schemas.

An encoding job is usually combined with other processing, for example, packaging, or encrypting the asset or assets generated by the encoder. Tasks within a Job can be chained together, where the output asset of one task is given as the input asset to the next task. In this way one job can contain all of the processing necessary for a media presentation.

This section provides links to common tasks that you would perform when working with Jobs\Tasks.

>[AZURE.NOTE]There is currently a limit of 30 tasks per job. If you need to chain more than 30 tasks, create more than one job to contain the tasks.


##Getting Media Processor

Get Media Processor with **.NET** or **REST API**.

[AZURE.INCLUDE [media-services-selector-get-media-processor](../includes/media-services-selector-get-media-processor.md)]

##Creating jobs 

A job is an entity that contains metadata about a set of tasks (for example, encoding or indexing). Each task performs an atomic operation on the input asset(s). For example on how to create encoding jobs, see:

[AZURE.INCLUDE [media-services-selector-encode](../includes/media-services-selector-encode.md)]

##Indexing

[AZURE.INCLUDE [media-services-selector-index-content](../includes/media-services-selector-index-content.md)]

##Encoding 

Encode with **Azure Media Encoder** using **Azure Management Portal**, **.NET**, or **REST API**.
 
[AZURE.INCLUDE [media-services-selector-encode](../includes/media-services-selector-encode.md)]

##Monitoring job progress

Monitor job progress using **Azure Management Portal**, **.NET** or **REST API**.

[AZURE.INCLUDE [media-services-selector-job-progress](../includes/media-services-selector-job-progress.md)]

##Related links

[Quotas and Limitations](media-services-quotas-and-limitations.md) ??? Describes quotas used and limitations of the Media Services Encoder
