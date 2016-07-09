---
layout: post
title:  "postgreSQL 笔记"
date:   2016-07-09
excerpt: "最近一直在使用postgreSQL处理数据,记录下常用的操作,方便以后查询"
categories:  postgreSQL 笔记  SQL
comments: true
---

# 字符串处理函数

 函数 ：character_length() 

说明 ：返回字符串的长度

 eg.  select character_length('中国人寿保险股份有限公司')  返回值为12
 
函数 ：substring(Arg[varchar] from begin[int] for end[int])

说明 ：截取字符串

eg.  substring('中国人寿保险股份有限公司' from 0 for character_length('中国人寿保险股份有限公司')-1)   返回值为'中国人寿保险股份有限公' 去掉了最后一个字符串

函数 ：字符串连接

说明 ：字符串连接

eg.  
{% highlight SQL %}
'我'||'喜欢'||'你'='我喜欢你'
{% endhighlight %}
#  序列的基本使用

创建序列 ：

{% highlight SQL %}
create sequence seq_tb_prod_id increment by 1 minvalue 1 no maxvalue start with 1; 
{% endhighlight %}

还可以可以简单点

{% highlight SQL %}
create sequence seq_tb_prod_id;
{% endhighlight %}

建议序列使用seq开头,后边通过下划线分割，连接表名和需要绑定的字段（一般设置为字段的默认值为序列的下一个值）

在创建表的时候为某个字段绑定序列值
{% highlight SQL %}
CREATE TABLE tb_prod
(
  id integer DEFAULT nextval('seq_tb_prod_id'::regclass),
  company character varying(100),
  prodname character varying(100),
  recordtime character varying(100),
  issale character varying(100),
  designtype character varying(100),
  approveway character varying(100),
  payway character varying(100),
  specialattr character varying(100),
  protectetime character varying(100),
  itemcode character varying(100),
  outsaletime character varying(100),
  produrl character varying(2000),
  prodtype character varying(100)
)
{% endhighlight %}

# 存储过程以及使用游标的例子

{% highlight SQL %}
CREATE or replace FUNCTION pro_n_product() RETURNS text  AS 
$$
DECLARE
  p record;
  result varchar;
  sum int;
  prod int;
  _recorddate varchar;

BEGIN
   for p in (select * from tb_prod where issale='在售') loop
  
	select  into _recorddate (select recorddate from (select t.companyname,b.name,b.recorddate from insyproduct b left join compay t on (b.companyno=t.companyno)where companyname=p.company and name=p.prodname) as c );
	
	update tb_prod set recordtime=_recorddate where issale='在售' and company=p.company and prodname=p.prodname;

   end loop;
    result='OK';

    return result;
END;
$$ LANGUAGE plpgsql;
{% endhighlight %}

如何调用

{% highlight SQL %}
select pro_n_product()
{% endhighlight %}

执行成功，会返回OK

删除存储过程

{% highlight SQL %}
DROP FUNCTION pro_n_product();
{% endhighlight %}
