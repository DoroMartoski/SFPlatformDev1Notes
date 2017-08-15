### HTTP and Callouts
* REST callouts are based on HTTP.
* Each callout request is associated with an HTTP method and an endpoint. The HTTP method indicates what type of action is desired.
* Each HTTP request sets a URI, which is the endpoint address at which the service is located.

    public class HTTPCalloutClass {
      public HTTPCalloutClass(){
        
      }
      
      public static list<sObject> getAnimals(){
        HTTP http = new Http();
        HttpRequest request = new HttpRequest();
        request.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals');
        request.setmethod('GET');
        HttpResponse response = http.send(request);
        //If the request is successful, parse the JSON response
        if(response.getStatusCode() == 200){
            //Deserialize the JSON string into collections of primitive data types
            Map<String, Object> results = (Map<String, Object>) JSON.deserializeUntyped(response.getBody());
            //Cast the values in the 'animals' key as a list
            List<Object> animals = (List<Object>) results.get('animals');
            System.debug('Received the following animals: ');
            for(Object animal : animals){
                System.debug(animal);
            }
        }
        
      return null;
    }
    
    public static void postAnimal(){
        HTTP http = new Http();
        HTTPRequest request = new HttpRequest();
        request.setEndpoint('https://th-apex-http-callout.herokuapp.com/animals');
        request.setMethod('POST');
        request.setHeader('Content-Type', 'application/json;charset=utf-8');
        //set the body as a JSON object
        request.setBody('{"name":"mighty moose"}');
        HTTPResponse response = http.send(request);
        //Parse the JSON response
        if(response.getStatusCode() != 201){
            System.debug('The status code returned was not expected: '+ response.getStatusCode() + ' ' + response.getStatus());            
        }else{
            System.debug(response.getBody());
        }        
      }
    }


