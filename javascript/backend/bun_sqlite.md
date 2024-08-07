### Bun.Sqlite.DB

```javascript
const { DB } = require("bun:sqlite");

const db = new DB("test.db");

db.run("CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY, name TEXT)");
db.run("INSERT INTO users (name) VALUES (?)", "John Doe");

const result = db.query("SELECT * FROM users").all();
console.log(result);
```

### Bun.Sqlite.Statement

```javascript
const { DB } = require("bun:sqlite");

const db = new DB("test.db");

const stmt = db.prepare("SELECT * FROM users WHERE name = ?");
stmt.bind("John Doe");
const result = stmt.all();
console.log(result);
```

### Bun.Sqlite.Transaction

```javascript
const { DB } = require("bun:sqlite");

const db = new DB("test.db");

const transaction = db.transaction(() => {
  db.run("INSERT INTO users (name) VALUES (?)", "Alice");
  db.run("INSERT INTO users (name) VALUES (?)", "Bob");
});

transaction();
const result = db.query("SELECT * FROM users").all();
console.log(result);
```

### Bun.Sqlite.Backup

```javascript
const { DB } = require("bun:sqlite");

const db = new DB("test.db");
const backupDb = new DB("backup.db");

const backup = db.backup(backupDb);
backup.step(-1);  // Backup all pages

const result = backupDb.query("SELECT * FROM users").all();
console.log(result);
```

### Bun.Sqlite.SQLite3

```javascript
const { SQLite3 } = require("bun:sqlite");

console.log("SQLite Version: " + SQLite3.version());
```
