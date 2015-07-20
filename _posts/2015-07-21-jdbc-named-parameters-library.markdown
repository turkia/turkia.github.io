---
layout: post
title:  "JDBC named parameters query library"
date:   2015-07-21 01:00:00
categories: clojure jdbc spring 
---

JDBC does not support named parameters in SQL queries. However, support for them has been implemented in [Spring framework][spring]. This library implements a simple way to use this feature from Clojure. Only queries are supported. The library can be found [here][github].

{% highlight clojure %}
(ns jdbc-namedparam-test.core
  (:require [clj-jdbc-namedparameters.core :as db]))

(db/query "select table_name, num_rows from user_tables
           where num_rows > :min_rows
           order by num_rows desc"
          {:min_rows 100})
{% endhighlight %}

[spring]:      http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/jdbc/core/namedparam/NamedParameterJdbcTemplate.html
[github]:      https://github.com/turkia/clj-jdbc-namedparameters
