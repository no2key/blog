---
title: Hibernate中映射枚举类型
date: '2010-12-03 03:34:49'
description: 
tags: ['Enum''Hiberante''Mapping''映射''枚举'']
categories: ['Hibernate'']
---

Hibernate中提供了org.hibernate.type.EnumType类来进行枚举类型的映射，可以将枚举实例的name或者ordinal映射到数据库，具体在HBM文件中配置如下：

           &lt;property name="bank"&gt;
            &lt;column name="BANK_MARK"  length="20" not-null="true" /&gt;
            &lt;type name="org.hibernate.type.EnumType"&gt;
                &lt;param name="enumClass"&gt;com.lunny.Bank&lt;/param&gt;
                &lt;param name="type"&gt;12&lt;/param&gt;
            &lt;/type&gt;
        &lt;/property&gt;

其中type的值指的java.sql.Types.*的某个值12对应的是VARCHAR，表示将枚举的name存到数据库中。默认是存的ordinal，也可指明4，即Integer。

OK。问题来了，如果枚举用的是一个自定义的数值或字符来分开的，如何映射？我的做法是看看EnumType的源代码，自己写一个（本来是想继承的，但是发现很多方法都是private，基本无法重用）。主要的改变有如下几点：
1.加入成员变量
`
public static final String KEY = "key";
private Getter getter;
`

其中的Getter是枚举中获取key值的方法

2.重写nullSafeGet， nullSafeSet，setParameterValues，objectToSQLString，toXMLString，fromXMLString这几个方法。
2.1 在setParameterValues方法中增加新的配置项解析，用于解析Key，并将key的Getter方法保存起来。


&lt;property name="bank"&gt;
  &lt;column name="BANK_MARK"  length="20" not-null="true" /&gt;
  &lt;type name="org.hibernate.type.EnumType"&gt;
    &lt;param name="enumClass"&gt;com.lunny.Bank&lt;/param&gt;
    &lt;param name="type"&gt;12&lt;/param&gt;
    &lt;param name="key"&gt;key&lt;/param&gt;
  &lt;/type&gt;
&lt;/property&gt;

2.2 在上述其它方法中加入判断Getter是否为空，如果不为空，则调用该方法来获得要存入数据库的值从而替代name或者ordianl。
