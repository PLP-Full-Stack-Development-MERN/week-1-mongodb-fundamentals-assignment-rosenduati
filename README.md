
2. **Database and Collection Creation:**

   - use library
   - db.createCollection("books")

3. **Insert Data:**

   db.books.insertMany([
  { title: "The Great Gatsby", author: "F. Scott Fitzgerald", publishedYear: 1925, genre: "Classic", ISBN: "9780743273565" },
  { title: "To Kill a Mockingbird", author: "Harper Lee", publishedYear: 1960, genre: "Fiction", ISBN: "9780061120084" },
  { title: "The Alchemist", author: "Paulo Coelho", publishedYear: 1988, genre: "Philosophical", ISBN: "9780062315007" },
  { title: "Atomic Habits", author: "James Clear", publishedYear: 2018, genre: "Self-Help", ISBN: "9780735211292" },
  { title: "Sapiens", author: "Yuval Noah Harari", publishedYear: 2011, genre: "History", ISBN: "9780099590088" }
])


4. **Retrieve Data:**

   - Retrieve all books from the collection.
   db.books.find().pretty()

   - Query books based on a specific author.
   db.books.find({ author: "Harper Lee" })

   - Find books published after the year 2000.
   db.books.find({ publishedYear: { $gt: 2000 } })


5. **Update Data:**

   - Update the book's published year
   db.books.updateOne({ title: "The Great Gatsby" }, { $set: { publishedYear: 1926 } })

   - Add a new field to all books
   db.books.updateMany({}, { $set: { rating: 4.5 } })


6. **Delete Data:**

   - Delete a book by its `ISBN`.
   db.books.deleteOne({ ISBN: "9780735211292" })

   - Remove all books of a particular genre.
   db.books.deleteMany({ genre: "Fiction" })


7. **Data Modeling :**

  db.users.insertOne({
  _id: ObjectId("user1"),
  name: "John Doe",
  email: "john@example.com",
  address: "123 Main St"
})

db.products.insertOne({
  _id: ObjectId("prod1"),
  name: "Laptop",
  price: 1200,
  category: "Electronics"
})

db.orders.insertOne({
  _id: ObjectId("order1"),
  userId: ObjectId("user1"),
  items: [{ productId: ObjectId("prod1"), quantity: 1 }],
  total: 1200
})


8. **Aggregation Pipeline:**

   - find the total number of books per genre.
   db.books.aggregate([{ $group: { _id: "$genre", totalBooks: { $sum: 1 } } }])

   - Calculate the average published year of all books.
   db.books.aggregate([{ $group: { _id: null, avgYear: { $avg: "$publishedYear" } } }])

   - Identify the top-rated book.
   db.books.find().sort({ rating: -1 }).limit(1)


9. **Indexing:**

   - Create an index on the author
   db.books.createIndex({ author: 1 })

   - Explain the benefits of indexing in MongoDB.
   Speeds up queries involving author.
Reduces the time complexity of searches.
Improves overall database performance.



