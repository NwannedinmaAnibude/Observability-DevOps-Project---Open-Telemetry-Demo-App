# Otel Astronomy Shop Demo App


What is Open Telemetry (OTel)?
OpenTelemetry is an open-source project designed to provide a unified standard for collecting and managing telemetry data from software applications, including traces, metrics, and logs. It helps in observing and understanding the behavior of applications and systems by offering a set of APIs, libraries, and agents for instrumenting code and exporting telemetry data.


<img width="459" alt="image" src="https://github.com/user-attachments/assets/ef852415-6a81-4732-a368-2774ba044a38" />


Architecture Diagram

<img width="435" alt="image" src="https://github.com/user-attachments/assets/0a4042ef-db8e-41fc-8547-852368bee19a" />



## Prerequisites:
1. AWS Cloud

## Steps:

Create EC2 instance with the following configurations: 	
- Ubuntu 22
- T2.xlarge (More than 6GB ram required)
- 15GB storage

<img width="287" alt="image" src="https://github.com/user-attachments/assets/56fcc5a3-2917-4bce-b57e-381f22fc83f6" />





Clone the repo:

<img width="468" alt="image" src="https://github.com/user-attachments/assets/542c6dee-422f-4df4-93e4-9cd61d3e5c36" />
<img width="468" alt="image" src="https://github.com/user-attachments/assets/d28f6542-b12e-438c-94d6-820ced1b42eb" />


As a DevOps Engineer you should understand what this project is doing and how things are happening so letʼs understand the docker compose file responsible for deploying the app.

## Understanding the docker compose file structure!

This Docker Compose file is designed to set up an observability demo
environment using various microservices. If you're new to observability, here's how you can understand this setup:
https://github.com/open-telemetry/opentelemetry-demo/blob/main/docker- compose.yml

## Breakdown of the File:
- ### Logging Configuration ( x-default-logging):
  This section defines how logs are handled. The logs are stored in JSON format with    limits on file size (5m) and number of files (2). The <img width="21" alt="image" src="https://github.com/user-attachments/assets/6cee0de3-fe12-4257-ac6a-5102bf04985f" /> option adds a name tag to each log entry, which is useful for identifying which       service generated the log.
  
 - ### Networks:
  The	networks section defines a custom network called <img width="96" alt="image" src="https://github.com/user-attachments/assets/1ca7ab7f-bbbf-42ed-9c22-5d3b505d6638" /> using the bridge driver, which allows containers to communicate with each other.
	
- ### Services:
  Each service represents a different microservice in the application. These microservices work together to form a complete application.


Now that you understood everything, lets start with deploying the application and then OBSERVE it!


Install Docker

<img width="468" alt="image" src="https://github.com/user-attachments/assets/9cb31abb-aee7-45c2-b9d6-214e84bf2302" />




















Now start the application:

<img width="468" alt="image" src="https://github.com/user-attachments/assets/15036ad6-7586-4547-ab80-8f3c090769d6" />




•After a while all your containers should have been created and started.


<img width="468" alt="image" src="https://github.com/user-attachments/assets/5c1b8494-2ecc-4284-8f38-6f0b7f838806" />


<img width="950" alt="Containers creation2" src="https://github.com/user-attachments/assets/2af9a656-df7c-41d2-afcd-a0991effb3ec" />

































Once all the containers are started, we can see the access them: 
- Web store: http://IP:8080/
- Grafana: http://IP:8080/grafana/
- Load Generator UI: http://IP:8080/loadgen/
- Jaeger UI: http://IP:8080/jaeger/ui/

<img width="955" alt="The Demo app" src="https://github.com/user-attachments/assets/f80b4a19-aed2-45ce-86d4-ee2f4ac8c67f" />


Feature Flags
The demo provides several feature flags that you can use to simulate different scenarios.

https://opentelemetry.io/docs/demo/feature-flags/


Flag values are stored in the 'src/flagd/demo.flagd.json' file. To enable a flag, change
the 'defaultvariant' value in the config file for a given flag to “onˮ.

<img width="406" alt="image" src="https://github.com/user-attachments/assets/dcef8526-9e00-47ee-aa89-8718be70ff66" />


## View and Analyse with the Jaeger UI

With the 'adservice' feature flag enabled, letʼs see how we can use Jaeger to
diagnose the issue to determine the root cause. Remember, that the service will generate an error for GetAds 1/10th of the time.

Jaeger is usually the first tool you get in contact with when you start getting into the world of Distributed Tracing. With Jaeger, we can visualise the whole chain of events. With this visibility we can easier isolate the problem when something goes
wrong.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/d7948c5f-77fd-442d-bb14-537a0f3d89d4" />



## Metrics on Grafana

<img width="958" alt="Grafana metrics 1" src="https://github.com/user-attachments/assets/74ce724b-dbc6-4831-a8da-9e359195bcf1" />


By following these steps, you can set up and explore an observability demo environment using OpenTelemetry and Docker. This setup will help you
understand the intricacies of distributed tracing and how to monitor and diagnose issues in microservices-based applications.
