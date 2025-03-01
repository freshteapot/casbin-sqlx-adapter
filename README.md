# casbin-sqlx-adapter
sqlx adapter for Casbin https://github.com/casbin/casbin

Based on [sqlx](https://github.com/jmoiron/sqlx), and tested in [MySQL](https://github.com/go-sql-driver/mysql).

## Installation

    go get github.com/memwey/casbin-sqlx-adapter

## Usage example

```go
opts := &AdapterOptions{
    DriverName: "mysql",
    DataSourceName: "root:1234@tcp(127.0.0.1:3306)/yourdb",
    TableName: "casbin_rule",
    // or reuse an existing connection:
    // DB: myDBConn,
}

a := NewAdapterFromOptions(opts)
e := casbin.NewEnforcer("examples/rbac_model.conf", a)
```

## Notice

The implement is kind of different from the [official one](https://casbin.org/docs/en/adapters). In this implement you should create the database and table on your own.

In my opinion, in a general PRODUCTION environment, the business code can rarely create a database, create a table or drop a table.

## Thank

Special thanks to [casin](https://github.com/casbin). They provide a superb authorization library.

Special thanks to [sqlx](https://github.com/jmoiron/sqlx). It provides a brilliant set of extensions on go's standard `database/sql` library.

And this project is inspected by [Xorm Adapter](https://github.com/casbin/xorm-adapter), [Gorm Adapter](https://github.com/casbin/gorm-adapter), [Beego ORM Adapter](https://github.com/casbin/beego-orm-adapter) and [MySQL adapter
](https://github.com/casbin/mysql-adapter). Thanks all of them.

## Others

This is a very first opensource of me and if this project violates any of the opensource guidelines, please contact me. The project is far from perfect, issues and pull requesets are very welcome. 

## License

This project is under Apache 2.0 License. See the [LICENSE](LICENSE) file for the full license text.
