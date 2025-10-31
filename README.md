Reflection

#1. How did you implement CRUD using SQLite?
I implemented the CRUD (Create, Read, Update, Delete) operations by developing a custom SQLite database helper class that extends SQLiteOpenHelper. This class manages the creation and versioning of the database while providing reusable methods for data manipulation.
Create: I used the insert() method of SQLiteDatabase to add new notes when users save entries from the Add Note screen.
Read: To display saved notes, I retrieved all records using the query() or rawQuery() methods and populated them into a RecyclerView through a custom adapter.
Update: When users edited a note, the update() method was called with a WHERE clause referencing the note’s unique ID to ensure that only the correct record was modified.
Delete: The delete() method was used to remove a selected note from the database, again using the note ID to identify the record.
This structured implementation allowed seamless interaction between the UI and the database, ensuring smooth note management within the app.

2. What challenges did you face in maintaining data persistence?
One of the key challenges I encountered was ensuring that data remained accessible even after closing and reopening the application. Initially, the notes were visible only during runtime due to improper handling of the database connection. I resolved this issue by correctly managing the lifecycle of the SQLiteOpenHelper, ensuring the database was opened and closed at appropriate points in the app’s lifecycle. Another challenge was reflecting real-time changes in the RecyclerView after performing CRUD operations. To solve this, I refreshed the adapter using notifyDataSetChanged() or reloaded the data cursor, ensuring that updates appeared instantly without restarting the app.

3. How could you improve performance or UI design in future versions?
For better performance, I plan to migrate from raw SQLite to the Room Persistence Library, which offers a more robust abstraction layer and integrates well with Android’s lifecycle components. Additionally, I would implement background threading using AsyncTask, Executors, or LiveData to prevent blocking the main UI thread during database operations. If the number of notes increases significantly, I could also incorporate pagination to optimize data loading.
In terms of UI design, I would enhance the interface using Material Design components, add a search and filter feature for easier navigation, and implement dark mode for a more user-friendly experience. These improvements would not only make the app more efficient but also elevate its usability and overall visual appeal.