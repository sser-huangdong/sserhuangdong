---
layout: page
title: 黄东DE主页
tagline: Do Whatever You Want
---
{% include JB/setup %}
{% assign PicPath = '/temp_assets' %}
![首页]({{ PicPath }}/home.jpg)  

#`不好意思！`
    
    或许您是因为看到我的简历才来的，但是由于更换了博客，所以暂时没有新内容。
    不过很快就会有的，我会把之前记录的一些内容整理成合适的格式后放上来啦~~

{% highlight java %}
public class HelloWorld {
    public static void main(String args[]) {
      System.out.println("Hello World!");
    }
}
{% endhighlight %}

---

##`鄙人的文章:`  

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
