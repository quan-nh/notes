---
title: parse duration
date: 2019-12-11T10:25:15+07:00
draft: false
tags:
  - java
  - time
---

[java.time.Duration/parse](https://docs.oracle.com/javase/8/docs/api/java/time/Duration.html#parse-java.lang.CharSequence-) function obtains a Duration from a text string in [ISO-8601](https://en.wikipedia.org/wiki/ISO_8601#Durations) duration format `P<date>T<time>`

Examples:

    "PT20.345S" -- parses as "20.345 seconds"
    "PT15M"     -- parses as "15 minutes" (where a minute is 60 seconds)
    "PT10H"     -- parses as "10 hours" (where an hour is 3600 seconds)
    "P2D"       -- parses as "2 days" (where a day is 24 hours or 86400 seconds)
    "P2DT3H4M"  -- parses as "2 days, 3 hours and 4 minutes"
    "P-6H3M"    -- parses as "-6 hours and +3 minutes"
    "-P6H3M"    -- parses as "-6 hours and -3 minutes"
    "-P-6H+3M"  -- parses as "+6 hours and -3 minutes"
 
```clj
(import java.time.Duration)

(.getSeconds (Duration/parse "pT20.345S"))
;=> 20
``` 
