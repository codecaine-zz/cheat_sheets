### 1. `Database#run(sql, [param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");

  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (let i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  db.each("SELECT rowid AS id, info FROM lorem", (err, row) => {
    console.log(row.id + ": " + row.info);
  });
});

db.close();
```

### 2. `Database#get(sql, [param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");
  db.run("INSERT INTO lorem VALUES ('Ipsum')");

  db.get("SELECT rowid AS id, info FROM lorem", (err, row) => {
    if (err) {
      console.error(err.message);
    }
    console.log(row.id + ": " + row.info);
  });
});

db.close();
```

### 3. `Database#all(sql, [param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");
  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (let i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  db.all("SELECT rowid AS id, info FROM lorem", [], (err, rows) => {
    if (err) {
      throw err;
    }
    rows.forEach((row) => {
      console.log(row.id + ": " + row.info);
    });
  });
});

db.close();
```

### 4. `Database#each(sql, [param, ...], [callback], [complete])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");
  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (let i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  db.each("SELECT rowid AS id, info FROM lorem", (err, row) => {
    console.log(row.id + ": " + row.info);
  }, (err, count) => {
    if (err) {
      throw err;
    }
    console.log("Total rows: " + count);
  });
});

db.close();
```

### 5. `Database#exec(sql, [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.exec("CREATE TABLE lorem (info TEXT); INSERT INTO lorem VALUES ('Ipsum');", (err) => {
  if (err) {
    return console.error(err.message);
  }
  console.log("Table created and row inserted");
});

db.close();
```

### 6. `Database#prepare(sql, [param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");

  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (let i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  db.each("SELECT rowid AS id, info FROM lorem", (err, row) => {
    console.log(row.id + ": " + row.info);
  });
});

db.close();
```

### 7. `Statement#run([param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");

  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  stmt.run("Ipsum", (err) => {
    if (err) {
      console.error(err.message);
    }
    console.log("Row inserted");
  });
  stmt.finalize();
});

db.close();
```

### 8. `Statement#get([param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");
  db.run("INSERT INTO lorem VALUES ('Ipsum')");

  let stmt = db.prepare("SELECT rowid AS id, info FROM lorem WHERE info = ?");
  stmt.get("Ipsum", (err, row) => {
    if (err) {
      console.error(err.message);
    }
    console.log(row.id + ": " + row.info);
  });
  stmt.finalize();
});

db.close();
```

### 9. `Statement#all([param, ...], [callback])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");
  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (let i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  let stmt2 = db.prepare("SELECT rowid AS id, info FROM lorem");
  stmt2.all([], (err, rows) => {
    if (err) {
      throw err;
    }
    rows.forEach((row) => {
      console.log(row.id + ": " + row.info);
    });
  });
  stmt2.finalize();
});

db.close();
```

### 10. `Statement#each([param, ...], [callback], [complete])`
```javascript
const sqlite3 = require('sqlite3').verbose();
let db = new sqlite3.Database(':memory:');

db.serialize(() => {
  db.run("CREATE TABLE lorem (info TEXT)");
  let stmt = db.prepare("INSERT INTO lorem VALUES (?)");
  for (let i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i);
  }
  stmt.finalize();

  let stmt2 = db.prepare("SELECT rowid AS id, info FROM lorem");
  stmt2.each([], (err, row) => {
    console.log(row.id + ": " + row.info);
  }, (err, count) => {
    if (err) {
      throw err;
    }
    console.log("Total rows: " + count);
  });
  stmt2.finalize();
});

db.close();
```
