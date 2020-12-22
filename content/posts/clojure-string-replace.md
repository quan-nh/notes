---
title: clojure.string/replace
date: 2018-06-22T14:25:15+07:00
draft: false
tags:
  - clojure
  - string
---

`clojure.string/replace` function is interesting! It can accept different types of input data.

The form of this function:
```clj
(clojure.string/replace s match replacement)
```

Where match/replacement can be:

+ string/string
```clj
(str/replace "The color is red" "red" "blue")
;=> "The color is blue"
```

+ char/char
```clj
(str/replace "The color is red" \c \k)
;=> "The kolor is red"
```

+ pattern/string
```clj
(str/replace "The color is red" #"red" "blue")
;=> "The color is blue"

;; $1, $2, etc. in the string are matched with regex pattern
(str/replace "Almost Pig Latin" #"\b(\w)(\w+)\b" "$2$1ay")
;=> "lmostAay igPay atinLay"
```

+ pattern/function
```clj
(str/replace "The color is red." #"[aeiou]"  #(str %1 %1))
;=> "Thee cooloor iis reed."

;; replaces all a's with 1 and all b's with 2 (map's also function)
(str/replace "a b a" #"a|b" {"a" "1" "b" "2"})
;=> "1 2 1"

;; to title case
(str/replace "hello world" #"\b." #(.toUpperCase %1))
;=> "Hello World"
```

## Spec'ing
```clj
(s/fdef clojure.string/replace
        :args (s/alt :string-string (s/cat :s string?
                                           :match string?
                                           :replacement string?)
                     :char-char (s/cat :s string?
                                       :match char?
                                       :replacement char?)
                     :pattern-string (s/cat :s string?
                                            :match pattern?
                                            :replacement string?)
                     :pattern-function (s/cat :s string?
                                              :match pattern?
                                              :replacement ifn?))
        :ret string?)
```
