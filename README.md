# clickhouse

Clickhouse support for GORM

# Quick Start

```go
package main

import (
  "fmt"


  "github.com/sweetpotato0/clickhouse"
  "gorm.io/gorm"
)

// User .
type User struct {
  ID   uint8  `gorm:"column:id"`
  Name string `gorm:"column:name"`
}

func main() {

  db, err := gorm.Open(clickhouse.Open("http://127.0.0.1:8123/default"), &gorm.Config{})
  if err != nil {
    panic(err.Error())
  }

  user := []User{}
  db.Table("user").Find(&user)
  fmt.Printf("%#v\n", user)
}

```
