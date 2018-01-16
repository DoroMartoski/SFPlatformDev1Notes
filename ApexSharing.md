###Apex sharing
* Use the share object associated with the standard or custom object to share that custom object. E.g accountShare for account and 
myCustomObjetShare for myCustomObject.
* Share object includes records supporting all 3 types of sharing: Force.com managed sharing, user managed sharing, and 
Apex Managed sharing.
* Sharing from OWD, role hierarchy, permissions such as "View All" & "Modify All", "View All Data" & "Modify All Data" are not
tracked with this object.

* Every share object has **objectNameAccessLevel**(level of access that specified user or group has been granted ie Edit, Read, ALL),
**ParentID**(Id of the object), **RowCause**(reason why the user or group is being granted access and 
**UserOrGroupId**(user or group being granted access).
* **ParentId, RowCause, UserGroupId cannot be updated**
