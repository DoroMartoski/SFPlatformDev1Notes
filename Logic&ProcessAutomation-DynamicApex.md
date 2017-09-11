### Describe how to programmatically access and utilize the object Schema

**Dynamic apex enables developers to:**
1. Access sObject and field Describe information - provides metadata information about sObject and field properties. Describe information for an sObject includes :
    + whether that type of sObject supports operations like create or undelete
    + the sObject's name and label
    + the sObject's fields and child objects - describe information for field includes whether the field has a default value, is calculated field, type of field etc.
2. Access Salesforce app information - allows developers to obtain describe information for standard and custom apps available in the Salesforce UI. Each app corresponds to a collection of tabs. 
     + Describe information for an app includes label, namespace, and tabs. 
     + Describe information for a tab includes the sObject associated with the tab, tab icons and colors.
