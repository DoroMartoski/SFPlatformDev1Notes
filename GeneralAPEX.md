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
***************************************************************************************************************************************
***************************************************************************************************************************************
### Access modifiers
 * A method or variable by default are only visible to the Apex code within the defining class.
 * A method or variable must be explicitly specified as public in order for it to be available to other classes in the same application namespace.
 
 * **Private - the default access modifier. Variable or method only available within the apex class in which it is defined."**
 * **Protected - method or variable is visible to any inner classes in the defining Apex class and to the classes that extend the defining Apex class.**
 * **Protected can only be used for instance methods and member variables**
 * **Public - method or variable can be used by any Apex in the application or namespace.**
 * **global - the method or variable can be used by any Apex code that has access to the class not just the APex code in the same application.**
 * **Use global access modifier if you need to refernece a method in a SOAP API. A class needs to be declared as global before a method can be declared as global.**
**************************************************************************************************************************************
**************************************************************************************************************************************
### Variables and primitives
* A variable declared without being initialized with a value has a null value automatically assigned to it. 
    Boolean x = null; is the same as boolean x;
* All primitive data types are passed by value => **this means pass by copy. the value being passed is a copy of the original variable and hence any changes made to the value does not affect the original variable**
```
int x = 7;
void go(int z){};
foo.go(x); => z gets assigned a copy of the value of x, so z == 7.
```
* All apex variables are initalized to null and hence you need to initialize them before using them.
* Primitives include Blob, boolean, date, datetime, decimal, double, id, integer, long, object, string, time.
* Boolean can be true, false or null. Id can be either 15 character case sensitive or 18 character case insensitive.
* Strings have no limit on the number of characters they can include - the heap size limits ensures the size does not grow too big.

=> further reading: https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/langCon_apex_primitives.htm

***************************************************************************************************************************************
***************************************************************************************************************************************
* **A block is a series of statements that are grouped together with curly braces and can be used in any place where a single statement would be allowed.**
* **Apex has 3 collections - lists(arrays), Maps, and Sets.**
* list is a collection of elements such as Integers, Strings, objects or other collections.
* Use a list when the sequence of elements is important. Lists can contain duplicate elements and the first index position in a list is always 0.
 List<account> acct = new list<account>();
 
* **Set** is a collection of unique, unordered elements. set<account> scctSet = new Set<account>{'a','b','c'};
* **Map** is a collection of key-value pairs. Keys can be any primitive data types. Values can include primitive data types as well as objects and other collections.
* Maps can contain duplicate values in a map but each key must be unique.
 Map<Integer, String> acctMap = new Map<Integer, String>{1 => 'a',2 => 'b', 3 =>'c'};

