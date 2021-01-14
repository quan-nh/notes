---
title: Clojure REPL
date: 2018-06-28T10:25:15+07:00
draft: false
tags:
  - clojure
  - repl
  - nrepl
---

### local repl
```clj
$ clj
Clojure 1.9.0
user=> (+ 1 1)
2
```

### socket repl
start socket repl
```sh
$ clj -J-Dclojure.server.repl="{:port 5555 :accept clojure.core.server/repl}"
Clojure 1.9.0
```

then, connect to this socket:
- w/ telnet
  ```clj
  $ telnet 127.0.0.1 5555
  Trying 127.0.0.1...
  Connected to localhost.
  Escape character is '^]'.
  user=> (println "hello")
  hello
  user=> :repl/quit
  Connection closed by foreign host.
  ```

### [nREPL](https://github.com/nrepl/nREPL)

deps.edn
```clj
{:deps
 {nrepl {:mvn/version "0.4.1"}}}
```

start nrepl server
```clj
$ clj
Clojure 1.9.0
user=> (use '[nrepl.server :only (start-server stop-server)])
nil
user=> (defonce server (start-server :port 7888))
#'user/server
```

client connect to nrepl server
```clj
$ clj
Clojure 1.9.0
user=> (require '[nrepl.core :as repl])
nil
(with-open [conn (repl/connect :port 7888)]
     (-> (repl/client conn 1000)
       (repl/message {:op :eval :code "(+ 1 1)"})
       repl/response-values))
[2]
```
