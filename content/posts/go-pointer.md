---
title: Go Pointers
date: 2020-04-25T10:25:15+07:00
draft: false
tags:
  - go
  - pointer
---

A pointer holds the memory address of a value.

```go
// pointer types
var p *int

// The & operator generates a pointer to its operand.
i := 42
p = &i

// The * operator denotes the pointer's underlying value (deref).
fmt.Println(*p) // read i through the pointer p
*p = 21         // set i through the pointer p
```
