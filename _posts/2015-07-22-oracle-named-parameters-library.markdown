---
layout: post
title:  "Oracle named parameters query library"
date:   2015-07-21 09:00:00
categories: clojure oracle spring 
---

JDBC does not support named parameters in SQL queries. However, support for them has been implemented in [Spring framework][spring]. This library implements a simple way to use this feature from Clojure with Oracle database. Only queries are supported. 

{% highlight clojure %}
(ns oracle-namedparam-test.core
  (:require [clj-oracle-namedparameters.core :as db]))

(db/query "select table_name, num_rows from user_tables
           where num_rows > :min_rows
           order by num_rows desc"
          {:min_rows 100})
{% endhighlight %}

Plain JDBC version might be implemented later. 

[spring]:      http://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/jdbc/core/namedparam/NamedParameterJdbcTemplate.html
