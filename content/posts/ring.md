---
title: ring
date: 2018-06-25T10:25:15+07:00
draft: false
categories:
  - web
tags:
  - clojure
  - ring
  - web 
---

![ring](/images/ring.jpeg)

- handler fn: [req](https://github.com/ring-clojure/ring-spec/blob/master/src/ring/core/spec.clj#L114) -> [resp](https://github.com/ring-clojure/ring-spec/blob/master/src/ring/core/spec.clj#L145)

- middleware fn: handler -> handler
  + request middleware
  ```clj
    (defn wrap-user [handler user-info]
      (fn [request]
        (handler
          (assoc request :user user-info))))
  ```
  + response middleware
  ```clj
    (defn wrap-content-type [handler content-type]
      (fn [request]
        (let [response (handler request)]
          (assoc-in response [:headers "Content-Type"] content-type))))
  ```
  + req+resp middleware
  ```clj
    (defn wrap-cookies [handler options]
      (fn [request]
        (-> request
            (cookies-request options)
            handler
            (cookies-response options))))
  ```

- middleware order: bottom up
  ```clj
  (defn wrap-1 [handler]
    (fn [req]
      (handler
        (assoc req :a 1))))

  (defn wrap-2 [handler]
    (fn [req]
      (handler
        (assoc req :a 2))))

  (-> handler
      wrap-1
      wrap-2)

  (wrap-2 (wrap-1 handler))

  (wrap-2 #(handler (assoc % :a 1)))

  (fn [req]
    (#(handler (assoc % :a 1))
      (assoc req :a 2)))

  (fn [req]
    (handler (assoc (assoc req :a 2) :a 1)))
  ```
