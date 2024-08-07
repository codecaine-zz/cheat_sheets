### 1. Connecting to a Database

```python
import sqlite3

# Connect to a database (or create it if it doesn't exist)
conn = sqlite3.connect('example.db')

# Close the connection
conn.close()
```

### 2. Creating a Table

```python
import sqlite3

conn = sqlite3.connect('example.db')
c = conn.cursor()

# Create table
c.execute('''CREATE TABLE stocks
             (date text, trans text, symbol text, qty real, price real)''')

# Commit the changes
conn.commit()

# Close the connection
conn.close()
```

### 3. Inserting Data

```python
import sqlite3

conn = sqlite3.connect('example.db')
c = conn.cursor()

# Insert a row of data
c.execute("INSERT INTO stocks VALUES ('2006-01-05','BUY','RHAT',100,35.14)")

# Save (commit) the changes
conn.commit()

# Close the connection
conn.close()
```

### 4. Querying Data

```python
import sqlite3

conn = sqlite3.connect('example.db')
c = conn.cursor()

# Query the database
for row in c.execute('SELECT * FROM stocks ORDER BY price'):
    print(row)

# Close the connection
conn.close()
```

### 5. Using Parameters in Queries

```python
import sqlite3

conn = sqlite3.connect('example.db')
c = conn.cursor()

# Insert data with parameters
data = ('2006-03-28', 'BUY', 'IBM', 1000, 45.0)
c.execute('INSERT INTO stocks VALUES (?,?,?,?,?)', data)

# Query with parameters
symbol = ('RHAT',)
c.execute('SELECT * FROM stocks WHERE symbol=?', symbol)
print(c.fetchone())

# Close the connection
conn.close()
```

### 6. Using `executemany()`

```python
import sqlite3

conn = sqlite3.connect('example.db')
c = conn.cursor()

# Insert multiple records
purchases = [('2006-03-28', 'BUY', 'IBM', 1000, 45.0),
             ('2006-04-05', 'BUY', 'MSFT', 1000, 72.0),
             ('2006-04-06', 'SELL', 'IBM', 500, 53.0),
            ]
c.executemany('INSERT INTO stocks VALUES (?,?,?,?,?)', purchases)

# Commit the changes
conn.commit()

# Close the connection
conn.close()
```

### 7. Using Row Factory

```python
import sqlite3

conn = sqlite3.connect('example.db')
conn.row_factory = sqlite3.Row
c = conn.cursor()

# Query the database
c.execute('SELECT * FROM stocks')
rows = c.fetchall()
for row in rows:
    print(dict(row))

# Close the connection
conn.close()
```

### 8. Using Context Managers

```python
import sqlite3

with sqlite3.connect('example.db') as conn:
    c = conn.cursor()
    c.execute('SELECT * FROM stocks')
    print(c.fetchall())
```

### 9. Handling Errors

```python
import sqlite3

try:
    conn = sqlite3.connect('example.db')
    c = conn.cursor()
    c.execute('SELECT * FROM non_existing_table')
except sqlite3.Error as e:
    print(f"An error occurred: {e}")
finally:
    conn.close()
```

### 10. Custom Functions

```python
import sqlite3

def multiply(x, y):
    return x * y

conn = sqlite3.connect('example.db')
conn.create_function("multiply", 2, multiply)
c = conn.cursor()

c.execute("SELECT multiply(2, 3)")
print(c.fetchone()[0])  # Output: 6

conn.close()
```

### 11. Using `Blob` Data

```python
import sqlite3

conn = sqlite3.connect('example.db')
c = conn.cursor()

# Create a table with a BLOB column
c.execute('''CREATE TABLE IF NOT EXISTS images (id INTEGER PRIMARY KEY, img BLOB)''')

# Insert BLOB data
with open('example.png', 'rb') as f:
    c.execute("INSERT INTO images (img) VALUES (?)", (f.read(),))

# Query BLOB data
c.execute('SELECT img FROM images WHERE id=1')
img = c.fetchone()[0]

with open('output.png', 'wb') as f:
    f.write(img)

conn.commit()
conn.close()
```
