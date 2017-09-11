### Describe how to programmatically access and utilize the object Schema

**Dynamic apex enables developers to:**
1. Access sObject and field Describe information - provides metadata information about sObject and field properties. Describe information for an sObject includes :
    + whether that type of sObject supports operations like create or undelete
    + the sObject's name and label
    + the sObject's fields and child objects - describe information for field includes whether the field has a default value, is calculated field, type of field etc.
2. Access Salesforce app information - allows developers to obtain describe information for standard and custom apps available in the Salesforce UI. Each app corresponds to a collection of tabs. 
     + Describe information for an app includes label, namespace, and tabs. 
     + Describe information for a tab includes the sObject associated with the tab, tab icons and colors.
3. Write dynamic SOQL queries, dynamic SOSL queries and dynamic DML:
    + Dynamic SOQL and SOSL queries provides the ability to execute SOQL and SOSL as a string at runtime.
    + Dynamic DML provides the ability to create a record dynamically and then insert it into the database using DML.
    + Using dynamic SOQL, SOSL, and DML, an application can be tailored precisely to the organizationas well as the user's permissions. Can be useful for applications that are installed from Force.com AppExchange.
    
**sObjects can be described by using 2 data structures:**
* Token - a lightweight, serializable reference to an sObject or a field that is validated at compile time. Used for Token describes.
* DescribeSObjects method - a method in the schema class that performs describes on one or more sObject

#### Describe result - an object of type schema.describeSObjectResult that contains all the describe properties for the sObject or field.
*** Describe result objects are not serializable, and are validated at runtime.** 
*** This result object is returned when performing the describe, using either the sObject token or the describeSobjects method.**

**Both sObject and field tokens have the method getDescribe which returns the describe result for that token**.
* getSObjecType and getSObjectField methods on the describe result return the tokens for sobject and field respectively.
* using tokens can make your code faster and more efficient due to their lightweight nature.

```
// Create a new account as the generic type sObject
sObject s = new Account();

// Verify that the generic sObject is an Account sObject
System.assert(s.getsObjectType() == Account.sObjectType);

// Get the sObject describe result for the Account object
Schema.DescribeSObjectResult dsr = Account.sObjectType.getDescribe();

// Get the field describe result for the Name field on the Account object
Schema.DescribeFieldResult dfr = Schema.sObjectType.Account.fields.Name;

// Verify that the field token is the token for the Name field on an Account object
System.assert(dfr.getSObjectField() == Account.Name);

// Get the field describe result from the token
dfr = dfr.getSObjectField().getDescribe();
```
