### Apex Core Concepts

* Version settings indicate the version of SOAP API and Apex to use. You can also use version settings to associate a class or trigger with a particular version of a managed package that is installed in your organization from Appexchange.
* Apex is a strongly-typed language - the data type of a variable must be declared when you first reference it.

### Triggers
* Use triggers to perform CRUD operations on related records or rrestrict certain operations from haappening.
* Triggers can be defined for custom objects, top-level standard objects and some standard child objects.
```
trigger TriggerName on ObjectName(trigger_events){
    code_block
}
```
* There are 7 possible trigger events ** before insert, before update, before delete, after insert, after update, after delete and after undelete**
* Two types of triggers - before triggers and after triggers.
* Before triggers - **used to update or validate record values before they are saved to the database**.
* After triggers - used to **access field values that are set by the system ( eg record ids or lastmodifieddate field) and to affect changes in other records.**
* **The records that fire the after triggers are read only.**


* **A block is a series of statements that are grouped together with curly braces and can be used in any place where a single statement would be allowed.**
* **Apex has 3 collections - lists(arrays), Maps, and Sets.**
* list is a collection of elements such as Integers, Strings, objects or other collections.
* Use a list when the sequence of elements is important. Lists can contain duplicate elements and the first index position in a list is always 0.
 List<account> acct = new list<account>();
 
* **Set** is a collection of unique, unordered elements. set<account> scctSet = new Set<account>{'a','b','c'};
* **Map** is a collection of key-value pairs. Keys can be any primitive data types. Values can include primitive data types as well as objects and other collections.
* Maps can contain duplicate values in a map but each key must be unique.
 Map<Integer, String> acctMap = new Map<Integer, String>{1 => 'a',2 => 'b', 3 =>'c'};

