```markdown
# 📘 MongoDB Tutorial with `mongosh`

Welcome to this hands-on MongoDB tutorial using the Mongo Shell (`mongosh`). This guide walks through how to connect to a MongoDB Atlas database and perform basic operations like inserting, updating, deleting, and querying data.

---

## 📦 Prerequisites

- Node.js installed (optional if using MongoDB locally)
- `mongosh` (MongoDB Shell) installed
- A MongoDB Atlas cluster or local MongoDB instance
- Basic familiarity with JavaScript syntax

---

## 🔌 Connecting to MongoDB Atlas

### ▶️ Step 1: Get Your Connection String

Log into your [MongoDB Atlas](https://cloud.mongodb.com), go to your cluster, and click **"Connect" > "Connect using MongoDB Shell"**. You’ll get a URI like:

```bash
mongosh "mongodb+srv://<username>:<password>@cluster0.mongodb.net/myDatabase"
```

Replace `<username>` and `<password>` with your Atlas credentials.

### ▶️ Step 2: Connect via Terminal

```bash
mongosh "mongodb+srv://Developer:MySecurePassword@cluster0.mongodb.net/school"
```

---

## 📁 Working with Databases and Collections

### 🔄 Switching Databases

```js
use school
```

This switches the context to the `school` database.

---

## ✍️ CRUD Operations (Create, Read, Update, Delete)

---

### ✅ INSERT Documents

```js
db.students.insertOne({
  name: "Hokela Calvin",
  age: 40,
  GraduationDate: null,
  Course: "Software Engineering",
  unitsTaken: [
    "Software Engineering Principles",
    "Object Oriented Programming",
    "Web Development"
  ],
  internDate: new Date()
})
```

---

### 🔍 READ Documents

#### Find all:
```js
db.students.find()
```

#### Find by specific `_id`:
```js
db.students.find({ _id: ObjectId("6803644c9f938debabd861e1") })
```

#### Find with multiple conditions:
```js
db.students.find({
  $and: [
    { age: { $lt: 51 } },
    { gpa: { $gt: 2 } }
  ]
})
```

---

### ✏️ UPDATE Documents

#### Update one field:
```js
db.students.updateOne(
  { name: "Hokela Calvin" },
  { $set: { gpa: 3.6 } }
)
```

#### Update using `_id`:
```js
db.students.updateOne(
  { _id: ObjectId("6803644c9f938debabd861e1") },
  { $set: { gpa: 4.3 } }
)
```

#### Remove a field:
```js
db.students.updateMany(
  { name: { $in: ["Muchiri", "Paul"] } },
  { $unset: { Dating: "" } }
)
```

---

### 🗑️ DELETE Documents

#### Delete one:
```js
db.students.deleteOne({ name: "Hokela Calvin" })
```

#### Delete many:
```js
db.students.deleteMany({ age: { $gt: 50 } })
```

---

## 🧠 MongoDB Key Concepts

| Concept            | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **Database**        | A container for collections. E.g., `school`                                |
| **Collection**      | A group of related documents. E.g., `students`                             |
| **Document**        | A single record in JSON-like format (BSON)                                 |
| **_id**             | Unique identifier automatically generated for each document                |
| **Operators**       | Keywords like `$set`, `$unset`, `$gt`, `$lt`, `$in` used in queries        |
| **ObjectId**        | Special 12-byte unique identifier used for `_id`                           |
| **Date**            | Use `new Date()` to store date-time info                                   |
| **CRUD**            | Create, Read, Update, Delete operations                                    |

---

## 🧰 Common Pitfalls & Fixes

| Problem                                         | Fix                                                                 |
|------------------------------------------------|----------------------------------------------------------------------|
| `SyntaxError: Unexpected token`                | Check for missing commas, braces `{}`, or parentheses `()`          |
| `E11000 duplicate key error`                   | You're inserting a document with an `_id` that already exists       |
| `zsh: command not found: show`                 | You're typing Mongo shell commands outside the `mongosh` environment|
| `Invalid database name`                        | Ensure your connection string doesn't have malformed characters     |
| Case-sensitive database names (`school` vs `School`) | Always use consistent casing — preferably lowercase                |

---

## 📌 Best Practices

- Always use `$set` to update fields, not to overwrite the entire document.
- Use `updateMany()` if updating multiple documents.
- Validate your documents' structure with `db.students.find().pretty()` for better readability.
- Stick to lowercase database names to avoid confusion in cross-platform environments.

---

## 🎉 Final Thoughts

This tutorial covered the essentials of working with MongoDB through `mongosh`, giving you a solid foundation in querying, inserting, updating, and deleting documents. You're now ready to build real-world applications backed by a flexible NoSQL database!

---

## 🔗 Useful Links

- [MongoDB Shell Docs](https://www.mongodb.com/docs/mongodb-shell/)
- [MongoDB Query Operators](https://www.mongodb.com/docs/manual/reference/operator/)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)

---

Happy coding! 🚀
```

---
https://profound-creponne-2132ff.netlify.app