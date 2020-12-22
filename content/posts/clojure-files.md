---
title: Clojure Files
date: 2018-07-12T10:25:15+07:00
draft: false
tags:
  - clojure
  - file
---

```clj
(require '[clojure.java.io :as io])

; returns java.io.File object
(io/file "/tmp/foo")

; returns seq of java.io.File in a dir
(file-seq (io/file "/tmp"))

; java.io.File class
; https://docs.oracle.com/javase/7/docs/api/java/io/File.html
(.isDirectory %)
(.isFile %)
(.getName %)
(.getPath %)

; create dir
(.mkdir (io/file "dir"))

; delete dir has files
(doseq [f (reverse (file-seq (io/file dir)))]
  (io/delete-file f))
```
