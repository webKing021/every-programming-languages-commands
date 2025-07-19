# MongoDB Commands Reference

## Connection & Authentication

```bash
# Connect to local MongoDB instance
mongo

# Connect to MongoDB instance with authentication
mongo --host hostname --port port -u username -p password --authenticationDatabase admin

# Connect to specific database
mongo database_name

# Connect with connection string
mongo "mongodb://username:password@hostname:port/database_name"

# Connect with connection string (SRV format)
mongo "mongodb+srv://username:password@cluster.mongodb.net/database_name"

# Connect with SSL
mongo --ssl --sslCAFile ca.pem --sslPEMKeyFile client.pem

# Connect with MongoDB Shell (mongosh - newer version)
mongosh "mongodb://hostname:port/database_name"
```

## Database Operations

```javascript
// Show all databases
show dbs
show databases

// Create or switch to database
use database_name

// Show current database
db

// Drop database
db.dropDatabase()

// Show database stats
db.stats()

// Run command on database
db.runCommand({ command: "value" })

// Get collection names
show collections
db.getCollectionNames()

// Create collection
db.createCollection("collection_name")

// Create capped collection (fixed size)
db.createCollection("collection_name", { capped: true, size: 10000000, max: 1000 })

// Drop collection
db.collection_name.drop()
```

## CRUD Operations

### Create (Insert)

```javascript
// Insert one document
db.collection_name.insertOne({ field1: "value1", field2: "value2" })

// Insert multiple documents
db.collection_name.insertMany([
  { field1: "value1", field2: "value2" },
  { field1: "value3", field2: "value4" }
])

// Insert with options
db.collection_name.insertOne(
  { field1: "value1" },
  { writeConcern: { w: "majority", wtimeout: 5000 } }
)
```

### Read (Query)

```javascript
// Find all documents
db.collection_name.find()

// Find with pretty formatting
db.collection_name.find().pretty()

// Find with query
db.collection_name.find({ field1: "value1" })

// Find one document
db.collection_name.findOne({ field1: "value1" })

// Find with projection (include fields)
db.collection_name.find({ field1: "value1" }, { field1: 1, field2: 1 })

// Find with projection (exclude fields)
db.collection_name.find({ field1: "value1" }, { field3: 0 })

// Find with limit
db.collection_name.find().limit(10)

// Find with skip
db.collection_name.find().skip(10)

// Find with sort (ascending)
db.collection_name.find().sort({ field1: 1 })

// Find with sort (descending)
db.collection_name.find().sort({ field1: -1 })

// Find with multiple sort fields
db.collection_name.find().sort({ field1: 1, field2: -1 })

// Count documents
db.collection_name.countDocuments({ field1: "value1" })

// Distinct values
db.collection_name.distinct("field1")

// Find with query operators
db.collection_name.find({ field1: { $eq: "value1" } })  // equals
db.collection_name.find({ field1: { $ne: "value1" } })  // not equals
db.collection_name.find({ field1: { $gt: 100 } })        // greater than
db.collection_name.find({ field1: { $gte: 100 } })       // greater than or equal
db.collection_name.find({ field1: { $lt: 100 } })        // less than
db.collection_name.find({ field1: { $lte: 100 } })       // less than or equal
db.collection_name.find({ field1: { $in: ["value1", "value2"] } })  // in array
db.collection_name.find({ field1: { $nin: ["value1", "value2"] } }) // not in array

// Find with logical operators
db.collection_name.find({ $and: [{ field1: "value1" }, { field2: "value2" }] })
db.collection_name.find({ $or: [{ field1: "value1" }, { field1: "value2" }] })
db.collection_name.find({ field1: { $not: { $eq: "value1" } } })
db.collection_name.find({ $nor: [{ field1: "value1" }, { field2: "value2" }] })

// Find with element operators
db.collection_name.find({ field1: { $exists: true } })
db.collection_name.find({ field1: { $type: "string" } })

// Find with array operators
db.collection_name.find({ tags: { $all: ["tag1", "tag2"] } })
db.collection_name.find({ field1: { $size: 3 } })
db.collection_name.find({ "array.0": "first_value" })
db.collection_name.find({ array: { $elemMatch: { field: "value", score: { $gt: 80 } } } })

// Find with regex
db.collection_name.find({ field1: /pattern/ })
db.collection_name.find({ field1: { $regex: "pattern", $options: "i" } })
```

### Update

```javascript
// Update one document
db.collection_name.updateOne(
  { field1: "value1" },
  { $set: { field2: "new_value" } }
)

// Update multiple documents
db.collection_name.updateMany(
  { field1: "value1" },
  { $set: { field2: "new_value" } }
)

// Replace entire document
db.collection_name.replaceOne(
  { field1: "value1" },
  { field1: "value1", field2: "new_value", field3: "value3" }
)

// Update with upsert (insert if not exists)
db.collection_name.updateOne(
  { field1: "value1" },
  { $set: { field2: "new_value" } },
  { upsert: true }
)

// Update operators
db.collection_name.updateOne({ field1: "value1" }, { $set: { field2: "value2" } })     // Set value
db.collection_name.updateOne({ field1: "value1" }, { $unset: { field2: "" } })         // Remove field
db.collection_name.updateOne({ field1: "value1" }, { $rename: { field2: "new_name" } }) // Rename field
db.collection_name.updateOne({ field1: "value1" }, { $inc: { counter: 1 } })            // Increment
db.collection_name.updateOne({ field1: "value1" }, { $mul: { price: 1.25 } })           // Multiply
db.collection_name.updateOne({ field1: "value1" }, { $min: { field2: 100 } })           // Min value
db.collection_name.updateOne({ field1: "value1" }, { $max: { field2: 100 } })           // Max value
db.collection_name.updateOne({ field1: "value1" }, { $currentDate: { lastModified: true } }) // Current date

// Array update operators
db.collection_name.updateOne({ field1: "value1" }, { $push: { array: "new_value" } })  // Add to array
db.collection_name.updateOne({ field1: "value1" }, { $pop: { array: 1 } })             // Remove last element
db.collection_name.updateOne({ field1: "value1" }, { $pop: { array: -1 } })            // Remove first element
db.collection_name.updateOne({ field1: "value1" }, { $pull: { array: "value" } })      // Remove all matching values
db.collection_name.updateOne({ field1: "value1" }, { $pullAll: { array: ["v1", "v2"] } }) // Remove multiple values
db.collection_name.updateOne({ field1: "value1" }, { $addToSet: { array: "value" } })  // Add if not exists

// Update with positional operator
db.collection_name.updateOne(
  { "array.field": "value" },
  { $set: { "array.$.field": "new_value" } }
)

// Update all array elements
db.collection_name.updateOne(
  { field1: "value1" },
  { $set: { "array.$[].field": "new_value" } }
)

// Update filtered array elements
db.collection_name.updateOne(
  { field1: "value1" },
  { $set: { "array.$[elem].field": "new_value" } },
  { arrayFilters: [{ "elem.field": "value" }] }
)
```

### Delete

```javascript
// Delete one document
db.collection_name.deleteOne({ field1: "value1" })

// Delete multiple documents
db.collection_name.deleteMany({ field1: "value1" })

// Delete all documents
db.collection_name.deleteMany({})
```

## Aggregation

```javascript
// Basic aggregation
db.collection_name.aggregate([
  { $match: { field1: "value1" } },
  { $group: { _id: "$field2", count: { $sum: 1 } } },
  { $sort: { count: -1 } }
])

// Aggregation stages
db.collection_name.aggregate([
  { $match: { field1: "value1" } },                // Filter documents
  { $project: { field1: 1, field2: 1, _id: 0 } },   // Select fields
  { $group: { _id: "$field2", count: { $sum: 1 } } }, // Group by field
  { $sort: { count: -1 } },                        // Sort results
  { $limit: 10 },                                  // Limit results
  { $skip: 5 }                                     // Skip results
])

// Lookup (join)
db.collection_name.aggregate([
  {
    $lookup: {
      from: "other_collection",
      localField: "field1",
      foreignField: "field2",
      as: "joined_data"
    }
  }
])

// Unwind arrays
db.collection_name.aggregate([
  { $unwind: "$array_field" }
])

// Add calculated fields
db.collection_name.aggregate([
  {
    $addFields: {
      full_name: { $concat: ["$first_name", " ", "$last_name"] }
    }
  }
])

// Count documents
db.collection_name.aggregate([
  { $count: "total" }
])

// Facet (multiple aggregation pipelines)
db.collection_name.aggregate([
  {
    $facet: {
      "categorizedByTags": [
        { $unwind: "$tags" },
        { $group: { _id: "$tags", count: { $sum: 1 } } }
      ],
      "categorizedByPrice": [
        { $match: { price: { $exists: true } } },
        { $bucket: { groupBy: "$price", boundaries: [0, 50, 100, 150], default: "Other" } }
      ]
    }
  }
])
```

## Indexes

```javascript
// List indexes
db.collection_name.getIndexes()

// Create index
db.collection_name.createIndex({ field1: 1 })  // Ascending
db.collection_name.createIndex({ field1: -1 }) // Descending

// Create compound index
db.collection_name.createIndex({ field1: 1, field2: -1 })

// Create unique index
db.collection_name.createIndex({ field1: 1 }, { unique: true })

// Create sparse index
db.collection_name.createIndex({ field1: 1 }, { sparse: true })

// Create TTL index
db.collection_name.createIndex({ createdAt: 1 }, { expireAfterSeconds: 3600 })

// Create text index
db.collection_name.createIndex({ field1: "text" })

// Create geospatial index
db.collection_name.createIndex({ location: "2dsphere" })

// Create hashed index
db.collection_name.createIndex({ field1: "hashed" })

// Create index with options
db.collection_name.createIndex(
  { field1: 1 },
  {
    unique: true,
    sparse: true,
    background: true,
    name: "custom_index_name"
  }
)

// Drop index
db.collection_name.dropIndex("index_name")
db.collection_name.dropIndex({ field1: 1 })

// Drop all indexes
db.collection_name.dropIndexes()

// Hide/unhide index
db.collection_name.hideIndex("index_name")
db.collection_name.unhideIndex("index_name")
```

## Administration

```javascript
// Server status
db.serverStatus()

// Current operations
db.currentOp()

// Kill operation
db.killOp(op_id)

// Database profiling
db.getProfilingLevel()
db.setProfilingLevel(1)  // 0=off, 1=slow, 2=all
db.system.profile.find().pretty()

// Replica set status
rs.status()

// Replica set configuration
rs.conf()

// Step down primary
rs.stepDown()

// Sharding status
sh.status()

// Add shard
sh.addShard("hostname:port")

// Enable sharding for database
sh.enableSharding("database_name")

// Shard collection
sh.shardCollection("database.collection", { field1: 1 })
```

## User Management

```javascript
// Show users
db.getUsers()
show users

// Create user
db.createUser({
  user: "username",
  pwd: "password",
  roles: [{ role: "readWrite", db: "database_name" }]
})

// Create admin user
db.createUser({
  user: "admin",
  pwd: "password",
  roles: [{ role: "userAdminAnyDatabase", db: "admin" }]
})

// Grant role to user
db.grantRolesToUser(
  "username",
  [{ role: "readWrite", db: "another_database" }]
)

// Revoke role from user
db.revokeRolesFromUser(
  "username",
  [{ role: "readWrite", db: "another_database" }]
)

// Update user
db.updateUser(
  "username",
  {
    pwd: "new_password",
    roles: [{ role: "read", db: "database_name" }]
  }
)

// Change user password
db.changeUserPassword("username", "new_password")

// Drop user
db.dropUser("username")

// Drop all users
db.dropAllUsers()

// Authenticate user
db.auth("username", "password")
```

## Backup & Restore

```bash
# Backup database (mongodump)
mongodump --host hostname --port port -u username -p password --authenticationDatabase admin --db database_name --out /path/to/backup

# Backup collection
mongodump --collection collection_name --db database_name --out /path/to/backup

# Backup with query
mongodump --db database_name --collection collection_name --query '{"field":"value"}' --out /path/to/backup

# Backup with options
mongodump --db database_name --gzip --oplog --out /path/to/backup

# Restore database (mongorestore)
mongorestore --host hostname --port port -u username -p password --authenticationDatabase admin --db database_name /path/to/backup/database_name

# Restore collection
mongorestore --db database_name --collection collection_name /path/to/backup/database_name/collection_name.bson

# Restore with options
mongorestore --gzip --oplogReplay --drop /path/to/backup

# Export data to JSON or CSV (mongoexport)
mongoexport --db database_name --collection collection_name --out /path/to/export.json
mongoexport --db database_name --collection collection_name --type=csv --fields field1,field2 --out /path/to/export.csv

# Import data from JSON or CSV (mongoimport)
mongoimport --db database_name --collection collection_name --file /path/to/import.json
mongoimport --db database_name --collection collection_name --type=csv --headerline --file /path/to/import.csv
```

## Performance & Monitoring

```javascript
// Explain query plan
db.collection_name.find({ field1: "value1" }).explain()
db.collection_name.find({ field1: "value1" }).explain("executionStats")
db.collection_name.find({ field1: "value1" }).explain("allPlansExecution")

// Collection stats
db.collection_name.stats()

// Database stats
db.stats()

// Server status
db.serverStatus()

// Replica set status
rs.status()

// Sharding status
sh.status()

// Current operations
db.currentOp()

// Kill operation
db.killOp(op_id)

// Database profiling
db.setProfilingLevel(1)  // 0=off, 1=slow, 2=all
db.getProfilingLevel()
db.setProfilingLevel(1, { slowms: 100 })  // Set threshold to 100ms
db.system.profile.find().pretty()
db.system.profile.find({ millis: { $gt: 100 } }).pretty()
```

## Miscellaneous

```javascript
// MongoDB version
db.version()

// Run JavaScript file
load("/path/to/script.js")

// Print to console
print("Hello, MongoDB!")

// Help
help

// Collection help
db.collection_name.help()

// Convert ObjectId to timestamp
ObjectId("507f1f77bcf86cd799439011").getTimestamp()

// Generate new ObjectId
ObjectId()

// Convert string to ObjectId
ObjectId("507f1f77bcf86cd799439011")

// Get collection names
db.getCollectionNames()

// Get collection infos
db.getCollectionInfos()

// Run command
db.runCommand({ command: "value" })

// Evaluate JavaScript on server
db.eval("function() { return 'Hello, MongoDB!'; }")

// Set write concern
db.getMongo().setWriteConcern({ w: "majority", wtimeout: 5000 })

// Get write concern
db.getMongo().getWriteConcern()

// Set read preference
db.getMongo().setReadPref("secondaryPreferred")

// Get read preference
db.getMongo().getReadPref()
```