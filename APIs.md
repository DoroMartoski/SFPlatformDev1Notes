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





