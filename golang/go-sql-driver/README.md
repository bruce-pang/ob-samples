# Connect OceanBase with Golang (go-sql-driver/mysql)

English | [简体中文](README-CN.md)

This article describes how to connect to the OceanBase database through `go-sql-driver/mysql`.

For details about `go-sql-driver/mysql`, you can refer to [https://github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql).

## Quick Start

You can use `dataSourceName` to create a database connection, please refer to [go-sql-driver/mysql documentation](https://github.com/go-sql-driver/mysql#dsn-data-source-name) for details.

Take [example.go](example.go) code as an example.

```go
var (
   host     = "127.0.0.1"
   port     = 2881
   dbName   = "test"
   username = "root@test"
   password = ""
)
dataSourceName := fmt.Sprintf("%s:%s@tcp(%s:%d)/%s", username, password, host, port, dbName)

db, err := sql.Open("mysql", dataSourceName)
if err != nil {
    log.Fatal(err)
}
defer db.Close()
```

Modify the connection info in code, and use `run.sh` to run the example code.

```bash
sh run.sh
```

### Use PreparedStatement

Log in to OceanBase with a root user and run the following command:

```bash
alter system set _ob_enable_prepared_statement = true;
```
