---
layout: post
title: '短信验证'
subtitle: '云片短息验证码'
date: 2018-02-03
categories: '短信验证'
tags: 'Java'
---
。。。。。。 话说这个东西倒是挺无语的，系统里面有个邮箱通知，为啥还要手机号呢？？(`据说邮箱不要钱`)、xk

选择的服务商还是挺靠谱的，有免费的次数，还挺多的，文档也全(`基本上都给你写好了`)、xk

接到这种需求，第一想到的便是redis了，方便，简单，一分钟过时很容易实现。但是系统用的是ehcache。。。不过也好，没用过，试试坑

<pre>
<code class="lang-java">
	Cache cache = chacheMng.getObject().getCache("CloudSliceMessage");
	Element element = new Element(session, code);
	element.setTimeToLive(60);
	cache.put(element);
</code>
</pre>

并没有考虑其他的`(短信到了就行)`一 一+

