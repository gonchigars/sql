# Comprehensive MongoDB Basics with Compass: A Complete Tutorial

## 1. Introduction

MongoDB is a popular NoSQL database that stores data in flexible, JSON-like documents. MongoDB Compass is a graphical user interface for MongoDB that makes it easy to explore and manipulate your data visually.

## 2. Setting Up MongoDB and Compass

1. Download MongoDB Community Server from the official website: https://www.mongodb.com/try/download/community
2. Install MongoDB following the instructions for your operating system.
3. Download and install MongoDB Compass from: https://www.mongodb.com/try/download/compass
4. Start MongoDB by running `mongod` in your terminal.
5. Open MongoDB Compass.
6. In Compass, connect to your local MongoDB instance using the connection string: `mongodb://localhost:27017`

## 3. Creating Your First Database and Collection

1. In Compass, click "Create Database".
2. Enter "friendsDB" as the Database Name and "friends" as the Collection Name.
3. Click "Create Database".

You've now created your first database and collection!

## 4. Basic Operations (CRUD)

### Create (Insert)

1. Click on the "friends" collection.
2. Click "Add Data" and choose "Insert Document".
3. Enter the following JSON:

```json
{
  "name": "Alice",
  "age": 25,
  "email": "alice@email.com"
}
```

4. Click "Insert".
5. Repeat for more friends:

```json
{
  "name": "Bob",
  "age": 30,
  "email": "bob@email.com"
}
```

```json
{
  "name": "Charlie",
  "age": 35,
  "email": "charlie@email.com"
}
```

### Read (Find)

1. To see all documents, simply view the "friends" collection.
2. To filter, use the filter bar. For example, to find friends older than 28, enter:

```json
{ "age": { "$gt": 28 } }
```

3. Click "Find" to apply the filter.

### Update

1. Find the document you want to update (e.g., Alice).
2. Click the pencil icon next to the document.
3. Change Alice's age to 26.
4. Click "Update".

### Delete

1. Find the document you want to delete.
2. Click the trash can icon next to the document.
3. Confirm the deletion.

## 5. Embedding vs Referencing

MongoDB offers two main ways to represent relationships between data: embedding and referencing.

### Embedding

Embedding is storing related data in the same document.

1. In the "friends" collection, insert a new document:

```json
{
  "name": "Diana",
  "age": 28,
  "hobbies": [
    {
      "name": "Painting",
      "yearsExperience": 5
    },
    {
      "name": "Singing",
      "yearsExperience": 3
    }
  ]
}
```

2. To find Diana and her hobbies, use the filter: `{ "name": "Diana" }`
3. To find all friends who enjoy painting, use: `{ "hobbies.name": "Painting" }`

### Referencing

Referencing involves storing related data in separate collections and connecting them using IDs.

1. Create a new "hobbies" collection in "friendsDB".
2. In the "friends" collection, add:

```json
{
  "name": "Eva",
  "age": 32
}
```

3. Note Eva's ObjectId after inserting.
4. In the "hobbies" collection, add:

```json
{
  "name": "Gardening",
  "yearsExperience": 4,
  "friendId": ObjectId("...Eva's ID...")
}
```

5. To find Eva's hobbies:
   - First, find Eva in "friends" and note her ObjectId.
   - In "hobbies", use the filter: `{ "friendId": ObjectId("...Eva's ID...") }`

## 6. Indexing

Indexes improve query performance.

1. In the "friends" collection, go to the "Indexes" tab.
2. Click "Create Index".
3. Set the field to "name" and leave the index type as "Single Field".
4. Click "Create".

Now, queries filtering on the "name" field will be faster.

## 7. Aggregation

Aggregation allows for complex data processing.

1. In the "friends" collection, go to the "Aggregations" tab.
2. Add a stage: $group
3. Set _id to null and add a field averageAge with value { $avg: "$age" }
4. Click "Add Stage".

This calculates the average age of all your friends.

## 8. Data Import and Export

### Import

1. Click on your database.
2. Click "Import Data".
3. Choose your file (JSON, CSV, etc.).
4. Follow the prompts to map fields and import.

### Export

1. In a collection, click "Export Collection".
2. Choose your desired format.
3. Click "Export".


## 9. Performance Monitoring

1. In Compass, go to the "Performance" tab.
2. Here you can monitor various metrics like operations per second, network I/O, and more.

## 10. Practice Exercises

1. Create a new "books" collection and add at least 5 books.
2. Use the filter bar to find all books published after 2000.
3. Update the publication year of one book.
4. Delete a book from your collection.
5. Create a "readers" collection to connect friends with books they've read using referencing.
6. Use the Aggregation pipeline to show which friends have read which books.
7. Create an index on the "title" field of the "books" collection.
8. Export your "books" collection and then import it into a new "favorite_books" collection.
9. Create a new user with read-only access to the "books" collection.
10. Use the Aggregation pipeline to find the average number of books read by friends.

## Conclusion

Congratulations! You've learned the basics of MongoDB with Compass. You now know how to set up MongoDB, perform CRUD operations, understand embedding vs referencing, use indexing and aggregation, manage data, implement basic security, and perform backups. Keep practicing and exploring to become proficient in using MongoDB for your data management needs.
