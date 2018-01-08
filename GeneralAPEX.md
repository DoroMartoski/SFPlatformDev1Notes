### Apex Core Concepts

* Version settings indicate the version of SOAP API and Apex to use. You can also use version settings to associate a class or trigger with a particular version of a managed package that is installed in your organization from Appexchange.
* Apex is a strongly-typed language - the data type of a variable must be declared when you first reference it. 

* **A block is a series of statements that are grouped together with curly braces and can be used in any place where a single statement would be allowed.**
* **Apex has 3 collections - lists(arrays), Maps, and Sets.**
* list is a collection of elements such as Integers, Strings, objects or other collections.
* Use a list when the sequence of elements is important. Lists can contain duplicate elements and the first index position in a list is always 0.
 List<account> acct = new list<account>();
 
* **Set** is a collection of unique, unordered elements. set<account> scctSet = new Set<account>{'a','b','c'};
* **Map** is a collection of key-value pairs. Keys can be any primitive data types. Values can include primitive data types as well as objects and other collections.
* Maps can contain duplicate values in a map but each key must be unique.
 Map<Integer, String> acctMap = new Map<Integer, String>{1 => 'a',2 => 'b', 3 =>'c'};

