---
title: "Clojure Code Snippets"
date: 2021-01-18T10:43:14+07:00
draft: false
tags:
  - clojure
  - snippet
---

Some Clojure code snippets.

```clj
;; map
; apply fn to all value of a map
(into {} (for [[k v] m]
           [k (f v)]))

; using Specter
(transform [MAP-VALS] inc {:a 1 :b 2 :c 3})
;=> {:a 2, :b 3, :c 4}


; update the values of multiple keys
(defn update-vals [m ks & args]
  (reduce #(apply update % %2 args) m ks))

(update-vals {:a 0 :b 1 :c 2} [:a :b] inc)
;;=> {:a 1, :b 2, c 2} 

(update-vals {:a 0 :b 1 :c 2} [:a :b] + 10)
;;=> {:a 10, :b 11, c 2}

;; using Specter
(transform (multi-path :a :b) inc {:a 0, :b 1, :c 2})
;=> {:a 1, :b 2, :c 2}

(transform [(submap [:a :b]) MAP-VALS] inc {:a 0, :b 1, :c 2})
;=> {:c 2, :a 1, :b 2}


;; vector
; remove the element at index n from vector v
(into (subvec v 0 n) (subvec v (inc n)))
```
