# Sqlite_for _android
* https://developer.android.com/training/data-storage/sqlite#java
* https://developer.android.com/training/data-storage/room/
* https://stackoverflow.com/questions/20291307/correct-way-to-trim-a-string-in-java
* https://developer.android.com/guide/topics/data/data-storage
* https://en.wikipedia.org/wiki/SQL_injection
* https://developer.android.com/reference/android/database/Cursor
* https://developer.android.com/reference/android/content/ContentResolver
* https://developer.android.com/guide/topics/providers/contacts-provider
* https://developer.android.com/guide/topics/manifest/provider-element?utm_source=udacity&utm_medium=course&utm_campaign=android_basics

_Code reference_ :
* https://github.com/codepath/android_guides/wiki/Local-Databases-with-SQLiteOpenHelper

_Sql injection_ :
https://www.netsparker.com/blog/web-security/sql-injection-vulnerability/
## Steps :
1. Define a schema & a contract 
2. Create a database using SQL HELPER
3. Add a cursor to it
4. Use content provider
5. Use cursor loader

**Why we need Contract class** :
 
 - [x] To define constants used in the Database .
 - [x] To avoid spelling errors .
 - [x] Ease of updating schema .
 
**Contract class contains** :

 - [x] Outer class .
 - [x] Inner class .
 - [x] String constants .
 
 **Use of SQLiteOpenHelper** :
 
 - [x] Create a sqliteDB .
 - [x] Gives a connection to the DB .
 - [x] Manages updating DB schema if version changes .
 
 **How to implement SQLiteOpenHelper** :
 1. Create a class that extends from SQLiteOpenHelper
 2. Create constants for DBnames & DBversions
 3. Create a constructor
 4. Implement onCreate() method
 5. Implement onUpgrade() method
 
 **Getting a database connection** :
 - use SQLiteDatabase db = mDbHelper.getReadableDatabase();
 - mDbHelper is an instance of SQLiteOpenHelper which will look for the Database , If a DB doesnot exist it will create a new DB using
 onCreate() method.
 
 **Cursor** :
 - A cursor is an object that represents a bunch of rows in a database .
 https://developer.android.com/reference/android/database/sqlite/SQLiteDatabase#query(java.lang.String,%20java.lang.String[],%20java.lang.String,%20java.lang.String[],%20java.lang.String,%20java.lang.String,%20java.lang.String)
 
 **Acessing sqlite3 database in Androidstudio** :
 
 ![as](https://user-images.githubusercontent.com/36688218/45912428-ab8a0880-be3e-11e8-8000-0ccc5dadf445.png)
 
 **Use of Content provider** :
- [x] Inorder to eliminate the direct interaction of the UI with DB , we use content provider .
- [x] Doesnot allow the invalid data to enter the database .
- [x] Good abstraction layer between the data source & the UI code
- [x] Works well with other android framework classes , For an instance:Activity manager

* https://developer.android.com/guide/topics/providers/content-provider-basics

**Use of Cursor loader** :
- The cursor loader will check when any new data is added or removed in the list to keep the list updated
- It also checks the data and updates it
- So the cursor loader works in conjuction with the listView & the cursor adapter
- _Inorder to implement the Cursor loader we requires Content provider_

**How does other app access database of an another app** :
- The external app uses a Content URI to give a request to the Contacts provider of the required app

**How does the Content URI matches with correct content provider** :
- The content Resolver does this work
  - The content URI(content://com.android.contacts/contacts/2) will be passed to the content Resolver 
    - Based on the content authority (i.e: com.android.contacts) the content resolver will handle the data and send to ContactsProvider.
     - To allow the external apps to access the database we should give android:exported="true" in the manifest file
* https://www.androiddesignpatterns.com/2012/06/content-resolvers-and-content-providers.html

**Use of Content URI** :
- can point to a part of a database
- can point to a file(text,images etc..)

 


 

