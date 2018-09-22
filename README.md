# Sqlite_for _android
* https://developer.android.com/training/data-storage/sqlite#java
* https://developer.android.com/training/data-storage/room/
* https://stackoverflow.com/questions/20291307/correct-way-to-trim-a-string-in-java
* https://developer.android.com/guide/topics/data/data-storage
* https://en.wikipedia.org/wiki/SQL_injection
* https://developer.android.com/reference/android/database/Cursor

_Code reference_ :
* https://github.com/codepath/android_guides/wiki/Local-Databases-with-SQLiteOpenHelper

_Sql injection_ :
https://www.netsparker.com/blog/web-security/sql-injection-vulnerability/
## Steps :
1. Define a schema & a contract 
2. Create a database using SQL HELPER
3. Add a cursor to it
4. Use content provider

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
* https://developer.android.com/guide/topics/providers/content-provider-basics

 


 

