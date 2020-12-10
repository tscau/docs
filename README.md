# The Software Company

Welcome to The Software Companies main Correspondence Generation project. We are using this repository to be able to demonstrate to our clients how to use GitHub in a best practices fashhion.

* This project uses .NET Core 3.1.8 (we are not yet ready to go to 5 - but this set of repos will be cloned and upgraded at some point

* The main services will be written as .NET Core Worker Services that will initially target Windows, but will be migrated to use Linux once we are happy with the solution. This will 
* All of the services will use Serilog for their logging
* All of the services will write a local log to the job folders in a sub-directory called logs
* All of the services will also publish their log entries to a SEQ endpoint
* All of the services will alos publish their log entries to a central shared location to cater for when the SEQ endpoint i snot available

* Each of the services will have REST endpoints that will expose:
  * GetCurrentConfig
  * GetVersionInfo
  * CallViaPriorityQueue
  * CallViaLowPriorityQueue
  * CallDirectly
  
* Each of the services wil luse .NET Core self hosted Kestrel server technology to be able to scale to the highest possible 
* Each of the services will be hosted in a docker container, and will be able to be deployed at will and managed as part of a K8s cluster, or a swarm. This will be a highly scalable system
* the initial implementation wil use HangFire as the "glue" that holds all the pieces together, however this will be expanded to use a more robust and scalable solution further down the track
* This project will also make use of the SQL Dacpac technology for the monolithinc database. This has ben chosen to better reflect what most organisations wil be dealing with: a legacy system that they in no way will be able to change easilly, so the datbase schema is non-negotiable
* The assumption is that the product that will actually generate the correspondence will be able to be called via REST endpoints
be done by using compiler switches to enable the worker services on Linux containers,

* We are using HangFire as the "glue" that holds all of this together

* The project consists of the following repositories:
  * TSC.Shared
  * TSC.Shared.DataAccess.MonolithicDB
  * TSC.Services.Shared
  * TSC.Composition.Services.Shared
  * TSC.Composition.Services.Scheduler
  * TSC.Composition.Services.Orchestrator
  * TSC.Composition.Services.PrepareSupportFiles
  * TSC.Composition.Services.RetrieveData
  * TSC.PostComposition.Services.Shared
  * TSC.PostComposition.Services.Orchestrator
  * TSC.PostComposition.Services.FixManifests
  * TSC.PostComposition.Services.XsltTransform
  * TSC.PostComposition.Services.DeliveryScheduler
  * TSC.PostComposition.Services.PaperDelivery
  * TSC.PostComposition.Services.UpdateDelivery
  * TSC.PostComposition.Services.UpdateMasterRecord
  * TSC.Consolidation.Services.Shared
  * TSC.Consolidation.Services.Orchestrator
  * TSC.Consolidation.Services.StageForConsolidation
  * TSC.Consolidation.Services.PaperBatchCOnsolidation
  * TSC.Consolidation.Services.PostCoeSort
  * TSC.Web.OpsPortal
  
* This project will make set up to use CI/CD from the start
* This project will be set up to use docker fropm the start
* All services will have at minimujm UnitTests using XUnit
* All services will also have a set of Integration tests
* All of the tests will be run (Unit and Integration) during automated build and deployment so MUST be designed to be able to do this from the start
