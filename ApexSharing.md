### Apex sharing
* Use the share object associated with the standard or custom object to share that custom object. E.g accountShare for account and 
myCustomObjetShare for myCustomObject.
* Share object includes records supporting all 3 types of sharing: **Force.com managed sharing**, **user managed sharing**, and 
**Apex Managed sharing**.
* Sharing from OWD, role hierarchy, permissions such as "View All" & "Modify All", "View All Data" & "Modify All Data" are not
tracked with this object.

* Every share object has **objectNameAccessLevel**(level of access that specified user or group has been granted ie Edit, Read, ALL),
**ParentID**(Id of the object), **RowCause**(reason why the user or group is being granted access and 
**UserOrGroupId**(user or group being granted access).
* **ParentId, RowCause, UserGroupId cannot be updated**
* **"All" access level can only be used by Force.com managed sharing.**
* **Manual** is the default value for sharing objects.

### User Managed Sharing Using Apex
* User managed sharing using Apex is the only shares that is deleted if the owner of the record changes.
* This type of shring manually shares a record to a user or a group.

### APex Managed Sharing
* Allows devs to programmatically manipulate sharing to support their application's behavior through APex or the SOAP API.
* **Only users with "Modify All Data" permission can add or change Apex managed sharing on a record.**.
* Apex managed sharing must use an Apex sharing reason - this enables devs to **easily track why they shared a record** and **be able to share with the same user or group multiple times using differnt reasons".**
* Format => Schema.Object__Share.rowCause.MyReasonName__c
* **Apex sharing reason are defined on an object's detail page**.

