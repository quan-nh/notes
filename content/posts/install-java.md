---
title: Install Java
date: 2020-06-09T10:25:15+07:00
draft: false
tags:
  - java
---

- download openjdk & unzip to `/Library/Java/JavaVirtualMachines/` dir

```sh
alias j8="export JAVA_HOME=`/usr/libexec/java_home -v 1.8`; java -version"
alias j13="export JAVA_HOME=`/usr/libexec/java_home -v 13`; java -version"
```
