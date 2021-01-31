# Semantic segmentation Deep learning models comparison application
TOISON Hugo, MOLINIE Tessan et BARROT Lucas

## Project Presentation :

We have implemented three deep learning models to compute Real-time Semantic Segmentation problem. <br />
The goal of Semantic Segmentation is to categorize each pixel of an image into a given class (examples: road, car, persons).<br />
Our algorithms can only analyze one picture for now, so we are limiting ourselves to create an API that can analyze only one given image at a time.

## Structure :

![Alt text](src/mermaid-diagram-20210131135146.png?raw=true "diagram_mermaid")

## Cloud Hosting :

Cloud hosting conditions:
- Having no sensitive or confidential content in our applications, we use a public cloud.
- Our system is SaaS. We provide a ready-to-use web page allowing visitors to upload an image of their choice which will then be used to make predictions on all three models. If the visitor does not have an image, he can choose one among those offered in the database.
- The database, for its part, is only a file containing ten high resolution images (approximately 1Mb each).
- Our system only predicts low traffic on the web page, maybe 100 visitors at most per day. However, in the event that this figure were to increase, we have planned to use the services of a scalable host.
- Our models are quite large, we estimate that we need at least 3 GB for the stored ones.
- A model requires a computing power of at least 2 GB of RAM for each prediction.
- We use a container to store the models and their environment.
- Uses of a serverless architecture for the host server to dynamically allocate resources to models for ease of management



Cloud Providers:
We have chosen to study the 3 most popular cloud providers.


### Features and things to note:

#### AWS:

+ Automatic container management with Amazon Elastic Container Service (Amazon ECS)
+ Dynamic resource allocation with AWS Lambda
+ Easy file storage with Amazon S3 for the few images available to use
+ Scalability of services: the resources provided by AWS are adapted to the need
+ Fairly low price and adaptable according to use
+ AWS sets default limits on resources (images, volumes, and snapshots) with region.You can launch the limited number of instance per area (negative point)


#### AZURE:

+ Automatic management of containers with Azure Container Service (ACS)
+ Host with the best security
+ Dynamic resource allocation with Azure Functions
+ Most expensive GPU allocation (negative point)


#### GCP:

+ Automatic container management with Kubernetes engine
+ Dynamic resource allocation with Cloud Functions
+ Lowest GPU cost of the three cloud providers we studied


taking into account all of that we have chosen AWS as our cloud provider.

## API :
To link each and every part of our application, we need to build a REST api and we will build it with a python framework, because it enables us to launch python scripts directly from the api endpoints since it's the same language that we use to build our deep learning models.

We chose three frameworks that we will compare in order to decide which one we are going to use :

### Flask :
Flask is a very simple to use and lightweight python framework designed to build python apis, it was released in 2010.

#### Advantages :
+ Easy to use
+ Lightweight
#### Drawbacks :
- Not asynchronous
- Old
- Not a lot of tools available 
### Django :
Django is a high-level Python Web framework designed to make the web development part very fast to build in order to allow developers to spend more time on the python application part of their projects.

#### Advantages :
+ A lot of chunks of code available to build apis very fast 
+ Scalable
+ A lot of pre-builded functionalities 
+ compatible with machine learning apis such as PyTorch and NumPy
#### Drawbacks :
- Not asynchronous
- Not really made for small applications

### FastApi :
FastAPI is a modern and fast web framework for building APIs with Python 3.6+ that was released in 2018.

#### Advantages :
+ One of the fastest python frameworks available
+ Asynchronous
+ Great editor support. Completion everywhere. Less time debugging.
+ Easy to use and learn
+ A lot of built-in functionalities such as almost all noSQL frameworks
#### Drawbacks :
- Recent so not that many online resources, courses and tutorials
### Conclusion :
Each of the three frameworks we introduced earlier could work for our project but the most suitable is FastApi because it is the only one that works with asynchronism, it enables us to handle multiple requests at a time and it has a lot of advantages as well.

## Container :
A container is a standard unit of software that packages up code and all its dependencies 
so the application runs quickly and reliably from one computing environment to another.

### Use case :
To use our algorithms online we need to put it in a container that can protect and simulate an environment configured.
Also we can create multiple session that can work simultaneously and independently from each other. 

### Docker :
Docker was launched in 2013, is open source and was released by the society with the same name Docker, Inc.

#### Advantages :
+ Highly used and numerous sources of information.
+ No specific platform.
+ No compatibility issue.
+ Numerous images and integration tools.

#### Drawbacks :
+ Docker containers only isolate individual processes (cannot use whole system container)(*)


### Rkt :
Rkt was launched in 2014, was released by CoreOS. 

#### Positive point :
+ Not limited by the functionality of the linux core.
+ Protect the containers from each other with the technology KVM.
+ can convert docker image with Quay, not native though.

#### Negative point :
+ fewer images (not directly) and integration tools than docker.
+ Optimized to operate application container (cannot use whole system container)(*same as docker).

### LXC
LXC or Linux containers, released in 2008, it is GNU LGPL.

#### Positive point :
+ Optimized to operate system container.

#### Negative point :
+ No standard function for operating application container.
+ No native implementation other than linux.

### Conclusion :
LXC can be hard to use in our case, because we only have an application.<br />
Other tools like rkt can be a good alternative, but it is more complex to set up and to find a good image.<br />
In our case and for the commodity we use Docker, because it natively offers numerous tools and images, guides, and we had numerous classes where we saw how to use it.<br />






