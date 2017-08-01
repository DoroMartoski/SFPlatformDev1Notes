# Salesforce APIs
## Salesforce Data API includes:
* REST API
* SOAP API
* BULK API and
* Streaming API

### Rest API:
* Based on RESTful principles using REST resources and HTTP methods. This allows you to perform CRUD functions on records, search or query data, retrieve object metadata and access information about limits in your org
* REST API supports both XML and JSON. REST API is lightweight request and response framework and hence great for mobile and web pages.

### SOAP API:
* SOAP API: robust and powerful and based on SOAP web service. It uses a Web Services Description Language(WSDL) file to rigorously define the parameters for accessing data through the API.
* SOAP API supports XML only.
* Most SOAP API functionality is also available through the REST API - which one to use depends on which standard meets your needs better.
* SOAP API is great for writing server-to-server integrations as it uses the WSDL file as a formal contract between the API and consumer.

### Bulk API:
* This is a specialized RESTful API for loading and querying lots of data and querying lots of data at once - 50k or more.
* Bulk API is asynchronous.

### Streaming API:
* Streaming API is a specialized API for setting up notifications that trigger when changes are made to your data.
* Uses publish-subscribe (pub/sub) model in which users can subscribe to channels that broadcast certain types of data changes.
* Pub/sub model reduces the number of API requests by eliminating the need for polling.
* Best used for writing apps that would otherwise need to frequently poll for changes.

**_All API Calls except for the SOAP API login() call, require authentication_**
**_Use one of the supported OAuth flows or authenticate with a session ID retrieved from the SOAP API login() call_**

### API Limits:
#### There are 2 types of API limits.
  * Concurrent limits: caps the number of long-running calls (20 seconds or longer) that are running at one time. 5 for dev edition and 25 for sandbox org.
  * Total limits: caps the number of calls made within a rolling 24-hour period. The limits vary by org edition, license type and expansion packs that are purchased.

* To check remaining API calls => Setup -> System Overview. You can also set up notifications for API remaining calls.

### Rest Resources and Methods
* A REST request consists of 4 components: a resource URI, an HTTP method, request headers, request body.
* Request headers specify metadata for the request.
* Request body specifies data for the request, when necessary(body is omitted from the request if there is no data to specify).

### REST Resources and Methods
* Each resource in REST API is identified by a named Uniform Resource Identifier(URI) and accessed using standard HTTP methods (HEAD, GET, POST, PATCH, DELETE).

##### A rest resource consists of 4 components:
* Resource URI
* HTTP method
* Request headers - specify metadata for the request
* Request body - specifies data for the request, when necessary. 

### SOAP API
#### Salesforce provides 2 SOAP API WSDLs for 2 different uses cases:
* Enterprise WSDL is optimized for a single Salesforce org - strongly typed and reflects the org's specific configuration meaning that two enterprise WSDL files generated from 2 different orgs contain different information.
* Partner WSDL - optimized for use with many Salesforce orgs. It's loosely typed and doesn't change based on an org's specific configuration.

### Bulk API
#### Bulk API is based on REST principles but is optimized for working with large sets of data and runs asynchronously whereas SOAP and REST API use synchronous requests and are optimized for real time client applications that update a few records at a time.
* Easiest way to use Bult API is to enable it for processing records in Data Loader using CSV files

#### Uploading data using the Bulk API:
* Create a job by submitting a POST request to the JobInfo resource with the job's properties in the request body.
* use the URI "/services/async" instead of "/services/data". async portion specifies that we are making a Bulk API request.
* Like SOAP API, the API version number doesn't include a "v" prefix in contrast with the REST API.
* "/job" indicates that we are accessing the JobInfo resource. => "/services/async/39/job"
* Bulk API supports payloads in CSV, XML and JSON.

### Streaming API
####Unlike the other APIs, Streaming API uses push paradigm based on criteria defined to push notifications from Salesforce to the client app.
* Streaming API allows you to keep your external system in sync with your Salesforce data. 
* Also lets you process business logic in an external system in response to data changes in Salesforce.
* It can be used to broadcast notifications for events defined outside of Salesforce

##### PushTopics
* Streaming API can be interfaced with through PushTopics.
* PushTopic is an sObject that contains the criteria of events you want to listen to - eg data changes for a particular object.
* Enables you to define the objects, fields, and criteria you are interested in receiving event notifications for.
* You define the criteria as a SOQL query in the PushTopic and specify the record operations to notify on(create, update, delete, and undelete).
* Id field must be included in the PushTopic query.
* Only 1 object per query allowed.

###### PushTopic represents the channel that client apps subscribe to.
* Account, campaign, Case, contact, lead, opportunity, task are standard objects supported by PushTopics.

Code:
pushtopic pushtopic = new PushTopic()'
pushTopic.name = 'AccountUpdates';
pushtopic.query = ''select Id, Name, Phone From Account Where BillingCity=\'San Francisco\'';
pushtopic.ApiVersion = 37.0;

insert pushTopic;

* You can change which fields generate notifications by modifying the PushTopic field NotifyForFields.

##### Retrieve Past Notifications Using Durable Streaming
* Since API version 37.0 you can retrieve past events that match a PustTopic query within a 24 hr window using replayId.

##### Generic Streaming
* This supports sending notifications with a generic payload that aren't tied to Salesforce data changes such as boradcasting messages to specific teams or entire organization, sending notifications for events that are external to Salesforce.

###### Things needed for generic streaming include:
* A streaming channel that defines the channel
* One or more clients subscribed to the channel
* The streaming Channel Push resource to monitor and invoke events on the channel.

* You can create a streaming channel for generic streaming either through the Streaming Channels app in the user interface or through the API
* A streaming channel is represented by the StreamingChannel sObject so can be created through Apex, RESTAPI or SOAP API.
* Format of the channel name for generic streaming is /u/ChannelName.

E.g of a channel named Broadcast:

StreamingChannel ch = new StreamingChannel();
ch.Name = '/u/Broadcast';

insert ch;












