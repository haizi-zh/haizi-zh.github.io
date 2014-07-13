---
layout: post
title:  "Morphia/MongoDB的思考"
date:   2014-07-13 23:53:03
categories: 数据库
tags: [数据库 Java MongoDB Morphia]
---

<img class="myimg" src="http://zephyre.qiniudn.com/blog/MongoDB.png?imageView/0/w/320/q/85" style="max-width:100%;text-align:center;"/>

传统的数据库应用中，以关系型数据库（RDBMS）为主。关系型数据库的优势在于：……

近期以来，随着互联网应用的发展，关系型数据库的缺点逐渐暴露出来。很多非关系型数据库（NoSQL）表现出了极强的可扩展性，非常适合高并发、低事务要求的应用。[MongoDB][]就是其中非常有代表性的一种。

{% highlight java %}
@Entity
public class Locality extends TravelPiBaseItem {
    @Id
    public ObjectId id;

    @Indexed()
    public String zhName;

    public List<String> alias;

    public List<Integer> travelMonth;

    @Constraints.Required
    public int level;

    @Reference(lazy = true, ignoreMissing = true)
    public Country country;

    @Reference(lazy = true, ignoreMissing = true)
    public Locality parent;
}
{% endhighlight %}

[MongoDB]: http://www.mongodb.org/