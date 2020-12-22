---
title: ex-info & ex-data
date: 2020-10-15T10:25:15+07:00
draft: false
tags:
  - clojure
  - exception
  - error
---

```clj
(defn div [x]
  (try
    (/ 3 x)
    (catch Exception e
      ;; ex-info return an ExceptionInfo exception with map data
      (throw (ex-info (.getMessage e) {:x x})))))

(try
  (div 0)
  (catch Exception e
    (prn (.getMessage e)) ; "Divide by zero"
    ;; ex-data get map data from ExceptionInfo exception
    (prn (ex-data e))     ; {:x 0}
    ))
```
