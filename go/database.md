# Database Operations in Go

## Setup and Connection

Go provides excellent database support through the `database/sql` package. Here's how to connect to a PostgreSQL database:

```go
import (
    "database/sql"
    "log"
    _ "github.com/lib/pq"  // PostgreSQL driver
)

// Connection string
dbURL := "postgres://username:password@localhost:5432/dbname?sslmode=disable"

// Open database connection
db, err := sql.Open("postgres", dbURL)
if err != nil {
    log.Fatal(err)
}
defer db.Close()

// Verify connection
if err = db.Ping(); err != nil {
    log.Fatal(err)
}
```

## Common Database Operations

### Creating a Table
```go
func createTable(db *sql.DB) error {
    query := `
        CREATE TABLE IF NOT EXISTS products (
            id SERIAL PRIMARY KEY,
            name VARCHAR(100) NOT NULL,
            price DECIMAL(10,2)
        );`
    
    _, err := db.Exec(query)
    return err
}
```

### Best Practices
1. Always close database connections with `defer db.Close()`
2. Use prepared statements for repeated queries
3. Handle errors appropriately
4. Use proper connection pooling settings
5. Validate connections with `db.Ping()`

### Important Notes
- The `database/sql` package is database-agnostic
- Driver registration uses blank identifier (`_`)
- Use parameterized queries to prevent SQL injection
