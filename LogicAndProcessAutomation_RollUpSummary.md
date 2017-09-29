### Roll-Up summary

**Roll-up summary field:**
* Calculates values from related records such as those in a related list.
* Displays a value in a master record based on the values of fields in a detail record.
* You can count, calculate the sum, minimum value of a field in the detail records.

#### Implementation
**Create roll-up summary fields on**
* Any custom object that is on the master side of the master-detail relationship
* Any standard object that is on the master side of a master-detail relationship with a custom object.
* Opportunities using the values of the opportunity products related to the opportunity
* Accounts using the values of related opportunities.
* Campaigns using the campaign member status or the values of campaign member custom fields

* You may not change the field type of a field that you reference in a roll-up summary field.
* Make sure that the for your summary field doesn't encounter a formula field that results in "#Error"
* When you delete a child record on a roll-up summary field, Salesforce doesn't recalculate the value of the field. Select the Force a mass recalculation on this field option on the edit page of the roll-up summary field to manually recalculate the value.
* You can't use long text area, multi-select picklist, Description fields, system fields like Last Activity, cross-object formula fields and lookup up fields in the field column of roll-up summary filters.
* You cannot convert an object's master-detail relationship into a look-up relationship after creating a roll-up summary on that object.
* Roll-up summary are not available for mapping lead fields of converted leads.

#### Management
* If a roll-up summary field doesn't contain





