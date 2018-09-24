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
* https://developer.android.com/guide/topics/providers/content-provider-creating#ContentURI
* https://developer.android.com/reference/android/content/UriMatcher
* https://docs.oracle.com/javase/tutorial/java/nutsandbolts/switch.html

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
6. Use content URI
7. Use URI matcher
8. Sanity checking
9. Implement contentprovider[MIME Type]

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
- Loader that queries the ContentResolver with a specific URI & returns a Cursor
- Loads data on a background thread because reading & writing to a database can be an expensive operation
- works well with content provider because a loader is tied to a URI
- _Inorder to implement the Cursor loader we requires Content provider_

**Activities to be done to implement a Cursor loader** :
1.onCreate()[getLoaderManager().initLoader()]
2.onCreateLoader()
3.onLoadFinished()[use swapCursor(cursor) in this method]
4.onLoaderReset()[use swapCursor(null) in this method]
- https://developer.android.com/reference/android/widget/CursorAdapter?utm_source=udacity&utm_medium=course&utm_campaign=android_basics

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
- In this content URI content://com.android.contacts/contacts/2
   - content:// - refers to schema
   - com.android.contacts - refers to Content Authority(Unique for each content provider)
   - contacts - refers to Type of data (table name should be given here)
   - 2 - refers to specific rows in the table(inorder to derive a single row)
   
**Why URI matcher is needed** :
- Helps us to ensure that the Contentprovider doesn't try to handle unexpected content URIs

**Steps to create a URI matcher** :
- Setup the URI matcher with the URI patterns your content provider will accept & assign each pattern an integer code
- Call UriMatcher.match(uri) and pass in a uri , which will return the corresponding integer code (if matched)

**Sanity checking** :
- https://developer.android.com/reference/android/content/ContentValues?utm_source=udacity&utm_medium=course&utm_campaign=android_basics

**Why to declare MIME Type** :
- the getType(Uri uri) method. The purpose of this method is to return a String that describes the type of the data stored at the input Uri. This String is known as the MIME type, which can also be referred to as content type.
- The Android system will check the MIME type of that URI to determine which app component on the device can best handle your request.
- https://stackoverflow.com/questions/7157129/what-is-the-mimetype-attribute-in-data-used-for

**Implement this [method] to handle requests for the MIME type** : 
- The returned MIME type should start with “vnd.android.cursor.item” for a single record, or “vnd.android.cursor.dir/” for multiple items.
- Step 1: Declare MIME Type constants in Contract.java file
- Step 2: Implement ContentProvider getType() method

**Related to UI** :
- Populating a listview with a cursor adapter 
- check this :https://github.com/codepath/android_guides/wiki/Populating-a-ListView-with-a-CursorAdapter

   

 


 

